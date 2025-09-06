# Design Document

## Overview

Pentaclism is a real-time strategy game that revolutionizes the RTS genre through innovative geodesic sphere maps, asymmetric faction design based on Platonic solids, and a sophisticated five-resource economy. The game features a client-server architecture with advanced camera systems, comprehensive replay functionality, and unique mechanics like underground expansion and subway station control.

This design document outlines the **technical architecture**, system components, and implementation approach for delivering the requirements specified in the requirements document. The architecture follows onion architecture principles with clear layer separation to ensure maintainability, testability, and scalability.

## Game Design Reference

This technical design document focuses on **how the systems work** from a code architecture perspective. For detailed information about **what the game content should be** - including specific faction mechanics, unit stats, building costs, balance values, map layouts, and gameplay mechanics - please refer to the separate **Game Design Document** (`game-design.md`).

The Game Design Document covers:
- Detailed faction mechanics and unique abilities
- Complete unit and building specifications with stats
- Resource costs, build times, and balance values
- Map generation rules and resource distribution
- Victory condition parameters and timing
- Combat mechanics and damage calculations
- Underground expansion progression and tech trees
- Subway station mechanics and faction bonuses

Both documents work together: this technical design provides the framework for implementation, while the game design document provides the specific content and balance parameters that populate that framework.

## Architecture

### Onion Architecture Layers

The system is organized into six distinct layers, with dependencies flowing inward from outer to inner layers:

#### Layer 1: Common (Innermost)
- **Purpose**: Shared utilities, constants, and basic data structures
- **Contents**: Mathematical utilities, geometric calculations, Platonic solid definitions, resource type enums, basic value objects
- **Dependencies**: None (pure functions and data)

#### Layer 2: Domain
- **Purpose**: Core business logic and domain entities
- **Contents**: Faction definitions, unit/building types, game rules, victory conditions, resource management logic
- **Dependencies**: Common layer only

#### Layer 3: Enactment
- **Purpose**: Game state management and rule enforcement
- **Contents**: Game engine, real-time tick processing, combat resolution, resource calculations, underground expansion logic
- **Dependencies**: Domain and Common layers

#### Layer 4: Infrastructure
- **Purpose**: External system integrations and data persistence
- **Contents**: Database access, file I/O, network protocols, event streaming, replay storage
- **Dependencies**: Enactment, Domain, and Common layers

#### Layer 5: Integration
- **Purpose**: API boundaries and service coordination
- **Contents**: REST APIs, WebSocket handlers, matchmaking services, lobby management
- **Dependencies**: Infrastructure and inner layers

#### Layer 6: Presentation (Outermost)
- **Purpose**: User interfaces and client applications
- **Contents**: Game client UI, map editor, replay viewer, spectator tools
- **Dependencies**: All inner layers

### Client-Server Architecture

The game employs a dedicated server architecture with authoritative game state and flexible hosting options:

- **Game Server**: Maintains authoritative game state, processes player commands, enforces rules, streams events to clients for local replay recording
- **Game Client**: Handles rendering, input, prediction, UI, and local replay file management
- **Matchmaking Service**: Manages player queues, skill-based matching, and server allocation
- **Custom Server Support**: Allows players to connect to custom server addresses while defaulting to official servers
- **Network Resilience**: Provides lag compensation, rollback mechanisms, and reconnection capabilities for stable multiplayer experience

## Components and Interfaces

### Core Game Engine (Enactment Layer)

#### GameState Manager
```typescript
interface GameStateManager {
  initializeMatch(config: MatchConfiguration): GameState
  processPlayerCommand(playerId: string, command: PlayerCommand): GameStateUpdate
  advanceGameTick(): GameStateUpdate
  validateVictoryConditions(): VictoryResult | null
  getPlayerView(playerId: string): PlayerGameView
  processVictoryCondition(type: VictoryType, playerId: string): VictoryProgress
  handlePlayerDisconnection(playerId: string): DisconnectionResult
}
```

#### Victory Condition Manager
```typescript
interface VictoryConditionManager {
  initializeConditions(enabledConditions: VictoryType[]): void
  checkDestructionVictory(gameState: GameState): VictoryResult | null
  checkCoreControlVictory(gameState: GameState): VictoryResult | null
  checkEconomicVictory(gameState: GameState): VictoryResult | null
  startEconomicCountdown(playerId: string): void
  validateCoreControlDuration(playerId: string, duration: number): boolean
}
```

#### Resource System
```typescript
interface ResourceManager {
  calculateResourceGeneration(playerId: string): ResourceDelta
  processResourceTransaction(transaction: ResourceTransaction): boolean
  validateResourceCost(playerId: string, cost: ResourceCost): boolean
  validateCapacityRequirement(playerId: string, capacityRequirement: CapacityRequirement): boolean
  processCapacityAllocation(playerId: string, allocation: CapacityAllocation): boolean
  releaseCapacityAllocation(playerId: string, allocationId: string): void
  getCurrentCapacityUsage(playerId: string): CapacityUsage
  applyResourceDecay(playerId: string): ResourceDelta
}
```

#### Faction System
```typescript
interface FactionManager {
  getFactionDefinition(factionId: FactionId): FactionDefinition
  validateFactionMechanic(playerId: string, mechanic: FactionMechanic): boolean
  processSignatureMechanic(playerId: string, mechanic: FactionMechanic): GameStateUpdate
  calculateFactionBonuses(playerId: string): FactionBonuses
  
  // Faction-Specific Mechanics
  processScavenging(playerId: string, wreckId: string): ResourceBundle
  enableUndercurrentMode(playerId: string): MobileSpawnState
  processCallToArms(playerId: string, workerId: string): MilitiaUnit
  manageDroneReserves(playerId: string, droneType: UnitTypeId): DroneReserve
  createBioDomeZone(playerId: string, coordinate: HexCoordinate): BioDomeZone
  processRailMovement(playerId: string, entityId: string, path: RailPath): MovementResult
}
```

#### Visual System Manager
```typescript
interface VisualSystemManager {
  setVectorMode(enabled: boolean): void
  renderPlatonicSolidUnit(unitId: string, factionId: FactionId): RenderData
  updateUnitVisualState(unitId: string, state: UnitVisualState): void
  applyCosmeticSkin(entityId: string, skinId: string): void
  calculateLevelOfDetail(distance: number): LODLevel
  renderHealthIndicator(unitId: string, healthPercent: number): HealthVisual
}
```

### Map and Navigation System (Domain/Enactment)

#### Geodesic Map Generator
```typescript
interface MapGenerator {
  generateGeodesicMap(config: MapConfiguration): GeodesicMap
  placePentagons(map: GeodesicMap, playerCount: number): SpawnConfiguration
  generateResourceNodes(map: GeodesicMap, config: ResourceConfiguration): ResourceNode[]
  createSubwayNetwork(map: GeodesicMap): SubwayNetwork
  generateMapType(type: 'full-sphere' | 'ring' | 'fragment', resolution: number): GeodesicMap
  validateMapBalance(map: GeodesicMap): BalanceReport
}
```

#### Advanced Camera System
```typescript
interface CameraController {
  // Core Navigation
  setViewMode(mode: CameraMode): void
  zoomToLevel(level: number, smooth: boolean): void
  panToCoordinate(coordinate: HexCoordinate, smooth: boolean): void
  rotateGlobe(rotation: Rotation3D): void
  
  // Advanced Features
  enableCinematicMode(enabled: boolean): void
  enableEsportsMode(enabled: boolean): void
  followUnit(unitId: string): void
  enableAutoFocus(enabled: boolean): void
  
  // Alert and Navigation
  jumpToAlert(alertId: string): void
  addCameraBookmark(name: string, position: CameraPosition): void
  returnToBase(playerId: string): void
  
  // Orientation Aids
  showCompass(enabled: boolean): void
  showCoordinateSystem(enabled: boolean): void
  showPentagonGrid(enabled: boolean): void
  
  // Picture-in-Picture
  enablePictureInPicture(enabled: boolean): void
  setPiPSource(source: CameraSource): void
}
```

#### Map Editor System
```typescript
interface MapEditor {
  createNewMap(type: MapType, resolution: number): EditableMap
  placeTerrain(coordinate: HexCoordinate, terrainType: TerrainType): void
  placeResourceNode(coordinate: HexCoordinate, resourceType: ResourceType): void
  createUndergroundLayer(depth: number): UndergroundLayer
  setSpawnPoint(coordinate: HexCoordinate, factionId: FactionId): void
  validateMapDesign(map: EditableMap): ValidationResult[]
  exportMap(map: EditableMap): MapFile
  importMap(mapFile: MapFile): EditableMap
}

### Underground Expansion System

#### Underground Manager
```typescript
interface UndergroundManager {
  digFloor(buildingId: string, depth: number): UndergroundFloor
  connectTunnels(startId: string, endId: string): TunnelConnection
  calculateTierAccess(playerId: string, depth: number): TechTier
  processUndergroundMovement(unitId: string, path: UndergroundPath): MovementResult
}
```

### Unit Experience and Training System

#### Experience Manager
```typescript
interface ExperienceManager {
  awardExperience(unitId: string, source: ExperienceSource, amount: number): void
  calculateRank(experience: number): number
  processRetraining(unitId: string, targetType: UnitTypeId): RetrainingResult
  validateUpgradeLimit(unitId: string, upgrade: UpgradeId): boolean
  calculateTrainingTimeReduction(unitRank: number, baseTime: number): number
  preserveExperienceOnRetraining(unitId: string, retentionRate: number): void
}
```

### Worker System and Expansion

#### Worker Manager
```typescript
interface WorkerManager {
  // Generic Worker Operations
  assignWorkerTask(workerId: string, task: WorkerTask): TaskAssignment
  validateWorkerCapability(workerId: string, task: WorkerTask): boolean
  processWorkerUpgrade(workerId: string, upgradeType: WorkerUpgradeType): UpgradeResult
  
  // Faction-Specific Worker Mechanics
  processScavengerCrewUpgrade(workerId: string): ZabatekPilot
  manageDualWorkerSystem(playerId: string, workerType: 'citizen' | 'engineer'): WorkerAssignment
  handleAutomatedConstruction(droneId: string, buildSite: BuildSite): AutoBuildResult
  manageTunnelConnectivity(workerId: string, buildingId: string): TunnelValidation
  processRailDependentConstruction(workerId: string, buildSite: BuildSite): RailValidation
  
  // Expansion Mechanics
  validateExpansionRequirements(playerId: string, expansionType: ExpansionType): ExpansionValidation
  processWallBasedExpansion(playerId: string, wallSegments: WallSegment[]): ExpansionResult
  manageEnergyGridExpansion(playerId: string, pylonNetwork: PylonNetwork): GridExpansion
  handleTunnelNetworkExpansion(playerId: string, tunnelConnections: TunnelConnection[]): NetworkExpansion
  processRailNetworkAdvancement(playerId: string, railSegments: RailSegment[]): RailExpansion
}
```

### Detection and Counter-Detection System

#### Detection Manager
```typescript
interface DetectionManager {
  // Detection Systems
  deployUndergroundSensor(playerId: string, coordinate: HexCoordinate): DetectionSensor
  deploySeismicDetector(playerId: string, coordinate: HexCoordinate): SeismicDetector
  processDetectionScan(sensorId: string): DetectionResult[]
  
  // Burrowing and Stealth
  processBurrowTransition(unitId: string, targetState: 'surface' | 'underground'): BurrowResult
  validateBurrowedMovement(unitId: string, path: UndergroundPath): MovementValidation
  createTunnelConnection(unitId: string, startCoord: HexCoordinate, endCoord: HexCoordinate): TunnelCreation
  
  // Counter-Detection
  applyDetectionImmunity(unitId: string, immunityType: ImmunityType): ImmunityResult
  generateFalseTunnelSignature(playerId: string, coordinate: HexCoordinate): CounterIntelligence
  processSeismicDeception(playerId: string, decoySignatures: DecoySignature[]): DeceptionResult
  
  // Detection Resolution
  resolveDetectionAttempt(detectorId: string, targetId: string): DetectionOutcome
  calculateDetectionRadius(sensorType: SensorType, upgrades: SensorUpgrade[]): number
  validateDetectionCountermeasures(targetId: string, detectionAttempt: DetectionAttempt): CountermeasureResult
}
```

### Subway Station System

#### Subway Controller
```typescript
interface SubwayController {
  initializeStations(map: GeodesicMap): SubwayStation[]
  processCaptureAttempt(stationId: string, playerId: string): CaptureProgress
  calculateFactionBonus(stationId: string, factionId: FactionId): StationBonus
  processStationDestruction(stationId: string): BreachWindow
  revealConnection(stationId: string, playerId: string): ConnectionInfo
  processInstantTeleportation(unitId: string, fromStationId: string, toStationId: string): TeleportResult
  updateCaptureProgress(stationId: string, playerId: string, deltaTime: number): CaptureProgress
  validateStationAccess(stationId: string, playerId: string): boolean
}
```

### Matchmaking and Lobby System

#### Matchmaking Manager
```typescript
interface MatchmakingManager {
  queuePlayer(playerId: string, preferences: MatchPreferences): QueueResult
  findMatch(playerId: string): MatchResult | null
  considerTempoMatching(player1: Player, player2: Player): boolean
  validateSkillBalance(players: Player[]): boolean
  allocateGameServer(matchId: string): ServerAllocation
  handleCustomServerConnection(playerId: string, serverAddress: string): ConnectionResult
}
```

### Replay and Event System

#### Event Stream Manager (Client-Side)
```typescript
interface EventStreamManager {
  recordEvent(event: GameEvent): void
  saveReplayToFile(matchId: string, filePath: string): void
  loadReplayFromFile(filePath: string): ReplayData
  createReplayFromEvents(events: GameEvent[]): ReplayData
  mergeAnnotations(replay: ReplayData, annotations: AnnotationEvent[]): AnnotatedReplay
  branchFromTick(replayId: string, tick: number): BranchableGameState
  validateReplayIntegrity(replay: ReplayData): boolean
}
```

#### Spectator and Annotation Tools
```typescript
interface SpectatorController {
  // Camera Control
  setCameraMode(mode: SpectatorCameraMode): void
  enableCinematicMode(enabled: boolean): void
  enableEsportsMode(enabled: boolean): void
  
  // Annotation System
  addMapAnnotation(annotation: MapAnnotation): void
  drawOnMap(coordinates: HexCoordinate[], style: DrawingStyle): void
  anchorAnnotationTo3D(annotation: Annotation, coordinate: HexCoordinate): void
  
  // Replay Features
  queueInstantReplay(event: GameEvent, priority: ReplayPriority): void
  enablePictureInPicture(enabled: boolean): void
  exportAnnotatedReplay(replayId: string): AnnotatedReplayFile
  
  // Broadcasting
  enablePlayerPOVCutIns(enabled: boolean): void
  setAutomaticCameraWork(enabled: boolean): void
}
```

#### Tutorial System
```typescript
interface TutorialManager {
  startGeneralTutorial(): TutorialSession
  startFactionTutorial(factionId: FactionId): TutorialSession
  createGuidedSequence(steps: TutorialStep[]): TutorialSequence
  validateTutorialCompletion(sessionId: string): boolean
  unlockPracticeScenarios(playerId: string): void
}
```

## Data Models

### Core Entities

#### Faction Definition
```typescript
interface FactionDefinition {
  id: FactionId
  name: string
  platonicSolid: PlatonicSolid
  faceCount: number
  difficultyRating: 1 | 2 | 3 | 4 | 5
  tempo: 'rush' | 'defensive' | 'flexible' | 'macro' | 'late-game'
  resourceSpecialization: ResourceType
  signatureMechanics: FactionMechanic[]
  maxUpgradesPerUnit: number
  startingResources: ResourceBundle
  uniqueBuildings: BuildingTypeId[]
  uniqueUnits: UnitTypeId[]
}
```

#### Game State
```typescript
interface GameState {
  matchId: string
  currentTick: number
  players: PlayerState[]
  map: GeodesicMap
  units: UnitInstance[]
  buildings: BuildingInstance[]
  subwayStations: SubwayStation[]
  activeEffects: StatusEffect[]
  victoryConditions: VictoryCondition[]
  gamePhase: 'setup' | 'active' | 'ended'
  enabledVictoryTypes: VictoryType[]
  economicVictoryCountdown: EconomicCountdown | null
  coreControlProgress: CoreControlProgress | null
}
```

#### Match Configuration
```typescript
interface MatchConfiguration {
  mapType: 'full-sphere' | 'ring' | 'fragment'
  mapResolution: number
  playerCount: number
  enabledVictoryConditions: VictoryType[]
  customRules: CustomRule[]
  allowSpectators: boolean
  allowReconnection: boolean
}
```

#### Geodesic Map
```typescript
interface GeodesicMap {
  id: string
  type: 'full-sphere' | 'ring' | 'fragment'
  resolution: number
  hexTiles: HexTile[]
  pentagons: PentagonTile[]
  resourceNodes: ResourceNode[]
  undergroundLayers: UndergroundLayer[]
  spawnPoints: SpawnPoint[]
  subwayStations: SubwayStation[]
  subwayConnections: SubwayConnection[]
  centralUndergroundCore: CoreLocation | null
}
```

#### Camera Position and State
```typescript
interface CameraPosition {
  coordinate: HexCoordinate
  zoom: number
  rotation: Rotation3D
  mode: CameraMode
}

interface CameraState {
  currentPosition: CameraPosition
  targetPosition: CameraPosition
  isTransitioning: boolean
  autoFocusEnabled: boolean
  cinematicModeEnabled: boolean
  esportsModeEnabled: boolean
  bookmarks: Map<string, CameraPosition>
  orientationAidsEnabled: OrientationAids
}
```

### Resource System

#### Resource Bundle
```typescript
interface ResourceBundle {
  // Consumable resources (stored amounts)
  metal: number
  polymers: number
  
  // Capacity-based resources (production rates)
  food: number
  fuel: number
  electricity: number
}

interface CapacityUsage {
  // Current capacity consumption vs production
  foodUsed: number
  foodProduced: number
  fuelUsed: number
  fuelProduced: number
  electricityUsed: number
  electricityProduced: number
}

interface CapacityRequirement {
  food?: number
  fuel?: number
  electricity?: number
}

interface CapacityAllocation {
  id: string
  playerId: string
  entityId: string // unit or building ID
  requirements: CapacityRequirement
  timestamp: number
}
```

#### Resource Transaction
```typescript
interface ResourceTransaction {
  playerId: string
  type: 'income' | 'expense' | 'transfer' | 'capacity-allocation' | 'capacity-release'
  resources?: ResourceBundle // for consumable resources
  capacityRequirement?: CapacityRequirement // for capacity-based resources
  allocationId?: string // for capacity management
  source: string
  timestamp: number
}
```

### Underground System

#### Underground Floor
```typescript
interface UndergroundFloor {
  buildingId: string
  depth: number
  tier: TechTier
  modules: FloorModule[]
  connections: TunnelConnection[]
  capacity: number
  currentOccupancy: number
}
```

### Subway System

#### Subway Station
```typescript
interface SubwayStation {
  id: string
  position: HexCoordinate
  ownerId: string | null
  captureProgress: number
  connectedStationId: string
  factionBonuses: Map<FactionId, StationBonus>
  defenses: DefenseStructure[]
  breachWindow: BreachWindow | null
}
```

### Worker System

#### Worker Instance
```typescript
interface WorkerInstance {
  id: string
  playerId: string
  factionId: FactionId
  workerType: WorkerType
  currentTask: WorkerTask | null
  capabilities: WorkerCapability[]
  upgrades: WorkerUpgrade[]
  batteryLevel?: number // For Technomancer drones
  tunnelConnectivity?: boolean // For Auporan Dwellers
  railAccess?: boolean // For Industrial Warmachine
}

interface WorkerTask {
  id: string
  type: 'mine' | 'build' | 'repair' | 'haul' | 'garrison'
  targetId: string
  priority: number
  estimatedCompletion: number
}
```

### Detection System

#### Detection Sensor
```typescript
interface DetectionSensor {
  id: string
  playerId: string
  position: HexCoordinate
  sensorType: 'underground' | 'seismic'
  detectionRadius: number
  energyCost: number
  upgrades: SensorUpgrade[]
  isActive: boolean
}

interface BurrowedUnit {
  unitId: string
  burrowState: 'surface' | 'transitioning' | 'underground'
  transitionProgress: number
  tunnelPath: HexCoordinate[]
  detectionImmunity: ImmunityType[]
  movementSpeed: number
}
```

### Expansion System

#### Expansion State
```typescript
interface ExpansionState {
  playerId: string
  factionId: FactionId
  expansionType: ExpansionType
  controlledTerritory: HexCoordinate[]
  expansionRequirements: ExpansionRequirement[]
  activeExpansions: ActiveExpansion[]
}

interface ActiveExpansion {
  id: string
  targetCoordinate: HexCoordinate
  expansionMethod: 'walls' | 'energy-grid' | 'tunnels' | 'rails' | 'opportunistic'
  progress: number
  requiredResources: ResourceBundle
  estimatedCompletion: number
}
```

### Event System

#### Game Event
```typescript
interface GameEvent {
  id: string
  matchId: string
  tick: number
  type: GameEventType
  actorId: string
  targetId?: string
  data: Record<string, any>
  timestamp: number
}
```

## Error Handling

### Validation Strategy
- **Input Validation**: All player commands validated at API boundary
- **State Validation**: Game state consistency checks after each update
- **Resource Validation**: Resource transactions validated before processing
- **Faction Validation**: Faction-specific mechanics validated against faction rules

### Error Recovery
- **Graceful Degradation**: Non-critical systems continue operating during partial failures
- **State Rollback**: Ability to revert to previous valid game state
- **Client Prediction**: Client-side prediction with server reconciliation
- **Network Resilience**: Automatic reconnection and state synchronization

### Logging and Monitoring
- **Event Logging**: All game events logged for debugging and replay
- **Performance Monitoring**: Real-time monitoring of server performance
- **Error Tracking**: Centralized error collection and analysis
- **Player Behavior Analytics**: Anonymized gameplay data collection

## Testing Strategy

### Unit Testing
- **Domain Logic**: Comprehensive testing of business rules and calculations
- **Faction Mechanics**: Isolated testing of each faction's unique systems
- **Resource Management**: Testing of resource generation, consumption, and validation
- **Map Generation**: Testing of geodesic map creation and validation

### Integration Testing
- **Client-Server Communication**: Testing of network protocols and state synchronization
- **Database Operations**: Testing of data persistence and retrieval
- **Replay System**: Testing of event recording and playback
- **Matchmaking**: Testing of player matching, skill-based pairing, and server allocation
- **Custom Server Integration**: Testing connection to custom servers and fallback to official servers
- **Tutorial System**: Testing faction-specific tutorials and progression tracking

### System Testing
- **Full Game Scenarios**: End-to-end testing of complete matches
- **Performance Testing**: Load testing with multiple concurrent matches
- **Stress Testing**: Testing system behavior under extreme conditions
- **Compatibility Testing**: Testing across different client configurations

### Specialized Testing
- **Faction Balance**: Automated testing of faction matchup outcomes and tempo curve validation
- **Map Fairness**: Testing of spawn point balance, resource distribution, and subway station placement
- **Camera System**: Testing of navigation, orientation aids, and advanced camera modes on geodesic maps
- **Replay Accuracy**: Verification that replays produce identical outcomes and annotation persistence
- **Victory Condition Testing**: Testing all combinations of enabled/disabled victory conditions
- **Map Editor Validation**: Testing custom map creation, sharing, and compatibility

## Performance Considerations

### Server Optimization
- **Tick Rate**: Optimized game tick processing for smooth gameplay
- **State Compression**: Efficient encoding of game state updates
- **Spatial Partitioning**: Optimized collision detection and unit queries
- **Memory Management**: Careful management of game object lifecycle

### Client Optimization
- **Rendering Pipeline**: Efficient rendering of geodesic maps and Platonic solid units
- **Level of Detail**: Dynamic LOD system for units and terrain
- **Prediction**: Client-side prediction to reduce perceived latency
- **Asset Streaming**: Progressive loading of game assets

### Network Optimization
- **Delta Compression**: Only transmit changed game state
- **Priority Queuing**: Prioritize critical game events
- **Bandwidth Adaptation**: Adjust update frequency based on connection quality
- **Regional Servers**: Geographically distributed servers for reduced latency

### Scalability
- **Horizontal Scaling**: Ability to run multiple game servers
- **Load Balancing**: Distribute players across available servers
- **Database Sharding**: Partition player data across multiple databases
- **CDN Integration**: Distribute static assets via content delivery network

## Key Design Decisions and Rationales

### Tempo-Based Faction Design
**Decision**: Faction complexity scales directly with Platonic solid face count (4-20 faces)
**Rationale**: This creates an intuitive difficulty progression where new players can start with simple rush factions (Tetrahedron) and gradually learn more complex mechanics. The geometric correlation provides a memorable and thematically consistent system.

### Event-Stream Replay System
**Decision**: Record lightweight event streams rather than video data
**Rationale**: Event streams are dramatically smaller in file size, allow perfect replay accuracy, enable branching from any point, and support advanced features like annotation merging and spectator tools.

### Geodesic Sphere Maps
**Decision**: Use geodesic polyhedron surfaces instead of traditional flat maps
**Rationale**: Eliminates corner camping, creates true 360-degree strategic gameplay, provides geometric fairness through pentagon spawn points, and offers unique tactical challenges not found in traditional RTS games.

### Onion Architecture Implementation
**Decision**: Strict layer separation with inward-only dependencies
**Rationale**: Ensures maintainability and testability of complex faction mechanics, allows independent testing of game rules, and provides clear boundaries for future expansion and modding support.

### Client-Server with Custom Server Support
**Decision**: Authoritative dedicated servers with optional custom server addresses
**Rationale**: Provides stable competitive gameplay while allowing community hosting, reduces cheating through server authority, and enables tournament organizers to run their own infrastructure.

### Underground Expansion as Core Mechanic
**Decision**: Multi-tier underground system tied to technology progression
**Rationale**: Creates meaningful strategic depth beyond surface control, provides defensive options for turtle strategies, and offers unique faction differentiation (especially for Auporan Dwellers' tunnel networks).

## Implementation Priorities

### Phase 1: Core Systems
1. Geodesic map generation and navigation
2. Basic faction mechanics and Platonic solid rendering
3. Five-resource economy system
4. Client-server architecture with authoritative game state

### Phase 2: Advanced Features
1. Underground expansion and tier system
2. Subway station capture mechanics
3. Advanced camera system with multiple modes
4. Unit experience and retraining system

### Phase 3: Polish and Content
1. Comprehensive replay system with annotations
2. Map editor and user-generated content
3. Tutorial system and faction-specific onboarding
4. Spectator tools and esports features

This design provides a comprehensive foundation for implementing Pentaclism while maintaining clean architecture principles and ensuring the system can scale to support a large player base with complex, asymmetric gameplay mechanics.