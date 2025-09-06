# Implementation Plan

- [ ] 1. Set up project structure and core interfaces
  - Create directory structure following onion architecture layers (Common, Domain, Enactment, Infrastructure, Integration, Presentation)
  - Define TypeScript interfaces for core data structures: GameState, PlayerState, UnitInstance, BuildingInstance
  - Implement JSON schemas for all entity types (Identity, Catalog, Session, Map, Economy, Combat, Zone, Replay contexts)
  - Set up build system with TypeScript 5.8, Angular 20, and BabylonJS 8.15.1
  - _Requirements: All requirements depend on this foundation_

- [ ] 2. Implement geodesic map system and basic geometry
- [ ] 2.1 Create geodesic polyhedron generation
  - Implement mathematical utilities for geodesic sphere creation with configurable resolution
  - Write algorithms for hexagonal tile placement with pentagon distribution at regular intervals
  - Create 3D coordinate system for navigating geodesic surfaces with smooth zoom transitions
  - Implement map types: Full Sphere (complete globe), Ring Maps (band around globe), Globe Fragment (up to 2/3 sphere)
  - Write unit tests for geometric calculations and coordinate transformations
  - _Requirements: 12.1, 12.2, 12.3_

- [ ] 2.2 Implement spawn point and resource distribution
  - Code spawn point placement system using pentagon tiles as faction starting locations
  - Implement resource node distribution algorithms ensuring Metal/Fuel deposits are properly placed
  - Create subway station placement system with randomized pairings (hidden until discovered)
  - Implement Central Underground Core placement for Core Control victory condition
  - Write unit tests for map generation consistency and balance validation
  - _Requirements: 12.4, 12.5, 15.1_

- [ ] 3. Implement five-resource economy system
- [ ] 3.1 Create resource management core
  - Implement ResourceBundle data structure with Metal, Fuel, Food, Polymers, Electricity
  - Code resource extraction system: Metal/Fuel from deposits, Food/Polymers/Electricity from production buildings
  - Create resource transaction processing with atomic operations and validation
  - Implement resource storage and capacity management with Food Silos for all factions
  - Write unit tests for resource calculations, extraction rates, and edge cases
  - _Requirements: 2.1, 2.2, 2.3_

- [ ] 3.2 Implement resource effects and faction specialization
  - Code Food starvation effects causing gradual HP loss for living units when Food runs out
  - Implement Electricity shortage effects powering down buildings until capacity restored
  - Create faction-specific resource emphasis bonuses: Survivors=Metal, Fists=Fuel, Technomancers=Electricity, Dwellers=Food, Warmachine=Polymers
  - Implement resource decay mechanics and efficiency calculations
  - Write unit tests for resource effects, faction bonuses, and starvation mechanics
  - _Requirements: 2.4, 2.5, 2.6_

- [ ] 4. Create faction system with Platonic solid identity
- [ ] 4.1 Implement faction definitions and core mechanics
  - Create FactionDefinition data structures mapping to Platonic solids: Tetrahedron(4)=Survivors, Cube(6)=Fists, Octahedron(8)=Technomancers, Dodecahedron(12)=Dwellers, Icosahedron(20)=Warmachine
  - Implement difficulty ratings: 1/5 to 5/5 based on face count, with tempo classifications (rush to late-game)
  - Code starting resource configurations and faction-specific resource emphasis bonuses
  - Implement maximum upgrades per unit based on face count (Tetrahedron=1, Cube=2, Octahedron=3, Dodecahedron=4, Icosahedron=5)
  - Write unit tests for faction initialization, tempo balance, and property validation
  - _Requirements: 1.1, 1.2, 7.1, 7.2, 7.3_

- [ ] 4.2 Implement Scrapyard Survivors faction mechanics
  - Code scavenging system for resource extraction from unit/building wrecks with bounded returns
  - Implement Undercurrent Mode mobile spawn capability when all buildings destroyed (time-limited grace period)
  - Create self-destruction mechanics with full resource refunds for own buildings
  - Implement surface-stacked infrastructure and mobile depot/caravan systems
  - Code combat units building Tier 1 structures slowly as backup builders
  - Write unit tests for scavenging loops, mobile spawn mechanics, and resource refunds
  - _Requirements: 1.3, 5.1_

- [ ] 4.3 Implement Celestial Fists faction mechanics
  - Code wall-based expansion system requiring walls to expand build radius
  - Implement fuel pipeline construction along walls with underground distribution
  - Create squad-based unit control system with individual member loss tracking and morale bonuses
  - Code Call to Arms ability converting workers into militia units
  - Implement formation commands (Form Wall, Sprint, Charge) and commander aura systems
  - Write unit tests for wall expansion, squad mechanics, and morale calculations
  - _Requirements: 1.4, 5.2_

- [ ] 4.4 Implement Technomancers faction mechanics
  - Code pilot-drone relationship system via Remote Control Centers with graceful degradation when RCCs destroyed
  - Implement drone reserve stockpiling system with instant replacement from reserves
  - Create energy grid management with wireless power distribution via pylons and battery storage
  - Code Phase Gate teleportation system for unit mobility
  - Implement drone autopilot for non-combat tasks with combat autopilot limitations
  - Write unit tests for RCC dependency, drone reserves, and energy grid mechanics
  - _Requirements: 1.5, 5.3_

- [ ] 4.5 Implement Auporan Dwellers faction mechanics
  - Code zone generator system creating bio-dome areas with healing/production bonuses and enemy debuffs
  - Implement tunnel network connectivity between all buildings for automatic unit transport
  - Create terraforming capabilities for permanent/temporary terrain modification
  - Code underground unit burrowing mechanics with concealment and tunnel creation
  - Implement espionage/sabotage mechanics with detection and consequence systems
  - Write unit tests for zone effects, tunnel networks, and burrowing mechanics
  - _Requirements: 1.6, 5.4_

- [ ] 4.6 Implement Industrial Warmachine faction mechanics
  - Code rail network construction and validation system with track laying requirements
  - Implement mobile building relocation along rails with mobile/fortified state toggles
  - Create building adjacency buff stacking system with saturation caps to prevent exponential scaling
  - Implement heavy logistics system with Resource Carts doubling as static defense when parked
  - Code siege weapon systems and strategic intel tools for planning counters
  - Write unit tests for rail mechanics, mobile buildings, and buff stacking calculations
  - _Requirements: 1.7, 5.5_

- [ ] 5. Implement visual system with Platonic solid rendering
- [ ] 5.1 Create vector mode rendering system
  - Implement Platonic solid arrangement rendering: Infantry=single solid, Vehicle=2-3 solids linearly arranged, Squad=cluster/orbit around core, Building=stacked solids with base ring
  - Code attachment grammar system for upgrades using fixed attachment points on Platonic solids
  - Create level-of-detail system: Far=silhouettes, Mid=arrangements+attachments, Close=detailed vectors and animations
  - Implement GPU instancing and procedural mesh generation for efficient Platonic solid rendering
  - Code faction-specific solid mapping: Tetrahedron=Survivors, Cube=Fists, Octahedron=Technomancers, Dodecahedron=Dwellers, Icosahedron=Warmachine
  - Write unit tests for rendering calculations, LOD transitions, and visual state management
  - _Requirements: 1.8, 1.9, 8.1, 8.5_

- [ ] 5.2 Implement visual feedback and skin systems
  - Code experience and upgrade visual indicators using orbiting smaller solids (rank count) and attachment points
  - Implement health visualization through face-chipping animation or opacity changes for damaged units
  - Create cosmetic skin overlay system with palette + edge thickness + particle sets without altering hitboxes or gameplay
  - Implement shield visualization with halo rings and energy animations with animated edge glows
  - Code colorblind-friendly palettes and high-contrast options for accessibility
  - Write unit tests for visual state transitions, skin application, and accessibility features
  - _Requirements: 8.2, 8.3, 8.4_

- [ ] 6. Create underground expansion and tier system
- [ ] 6.1 Implement underground floor construction and tier gating
  - Code underground floor creation system beneath surface buildings with UndergroundFloor data structure
  - Implement depth-based technology tier unlocking: Tier 1-2 (shallow) for basic tech, Tier 3-4 (mid) for advanced labs, Tier 5+ (deep) for ultimate tech and super-units
  - Create additional production queue slots, research capabilities, and garrison space per underground floor
  - Implement time and logistics costs for underground construction via digger units or specialized modules
  - Code faction-specific underground mechanics: Survivors use vertical stacking instead of underground bunkers
  - Write unit tests for underground construction, tier validation, and capacity calculations
  - _Requirements: 3.1, 3.2, 3.3, 3.7_

- [ ] 6.2 Implement underground management and tunnel systems
  - Code cutaway side-profile view system for underground floor management and visualization
  - Implement tunnel connection system specifically for Auporan Dwellers allowing underground unit movement between buildings
  - Create tunnel network connectivity where all Dweller buildings act as tunnel entrances with automatic transport
  - Implement burrowing mechanics for Dweller units with concealment, slow tunneling, and tunnel creation capabilities
  - Code underground sensors and seismic detectors for counter-play against burrowed units
  - Write unit tests for underground visualization, tunnel networks, and burrowing detection systems
  - _Requirements: 3.4, 3.5, 3.6_

- [ ] 7. Implement unit experience and training system
- [ ] 7.1 Create experience and ranking system
  - Code experience point award system: kills=50 XP, assists=25 XP, 10s alive=5 XP with combat participation tracking
  - Implement rank progression system with thresholds: Rank0→1=100, →2=300, →3=700, →4=1500 XP
  - Create rank-based stat improvements and visual indicators using orbiting smaller Platonic solids
  - Implement experience preservation during unit retraining with partial XP retention options
  - Code visual badges and progress bars for XP and rank display with hover tooltips
  - Write unit tests for experience calculations, rank progression, and stat bonus applications
  - _Requirements: 4.1, 4.2, 4.3, 4.6_

- [ ] 7.2 Implement retraining and upgrade systems
  - Code unit retraining system with rank-based time reduction: trainingTime = baseTime * (1 - rank * 0.15)
  - Implement faction-specific upgrade limits based on Platonic solid faces (Tetrahedron=1, Cube=2, Octahedron=3, Dodecahedron=4, Icosahedron=5)
  - Create upgrade validation system preventing over-upgrading and ensuring faction balance
  - Implement training queue system with visible progress, cancellation options, and partial refunds
  - Code upgrade application system with visual attachment points on Platonic solid arrangements
  - Write unit tests for retraining mechanics, upgrade limits, and queue management
  - _Requirements: 4.4, 4.5_

- [ ] 8. Create subway station system
- [ ] 8.1 Implement subway station placement and capture mechanics
  - Code strategic subway station placement at key map locations with randomized connection pairings hidden until discovered
  - Implement capture progress system using diegetic water tank/silo visual indicators that fill with player colors
  - Create any-unit capture system with progress decay when uncontested and reset when enemy contests
  - Implement faction-specific bonuses: Survivors=polymer income, Fists=pipeline extension, Technomancers=power grid nodes, Dwellers=tunnel network integration, Warmachine=rail integration
  - Code static defense activation upon successful capture to prevent yo-yo captures
  - Write unit tests for station placement algorithms, capture progress mechanics, and faction bonus calculations
  - _Requirements: 15.1, 15.2, 15.3_

- [ ] 8.2 Implement subway transportation and breach mechanics
  - Code instant teleportation system between connected stations for controlling player
  - Implement connection discovery system: lines only revealed when units actually travel through them
  - Create station destruction mechanics with temporary breach windows allowing any faction to use connection before collapse
  - Implement spectator visibility: show all connections to viewers while keeping them hidden from players until discovered
  - Code station HP system allowing destruction back to neutral state
  - Write unit tests for teleportation mechanics, discovery system, and breach window timing
  - _Requirements: 15.4, 15.5_

- [ ] 9. Implement victory condition system
- [ ] 9.1 Create configurable victory conditions
  - Code victory condition configuration system for match setup
  - Implement Destruction Victory detection for eliminated HQs and spawns
  - Create Core Control Victory with 5-minute hold requirement
  - Write unit tests for victory condition validation and timing
  - _Requirements: 6.1, 6.2, 6.3_

- [ ] 9.2 Implement Economic Victory system
  - Code Economic Victory detection with 3× income advantage
  - Implement 10-minute countdown with public resource disclosure
  - Create victory condition combination validation
  - Write unit tests for economic calculations and victory timing
  - _Requirements: 6.4, 6.5, 6.6_

- [ ] 10. Create advanced camera and navigation system
- [ ] 10.1 Implement core camera functionality
  - Code seamless zoom system from tactical (flat-feeling) to strategic (full globe visible) views with smooth transitions
  - Implement minimap globe rotation system with corresponding main camera perspective rotation
  - Create smooth camera movement interpolation and coordinate transformation for geodesic surfaces
  - Implement camera position and state management with CameraPosition and CameraState interfaces
  - Write unit tests for camera calculations, zoom transitions, and coordinate transformations
  - _Requirements: 11.1, 11.2_

- [ ] 10.2 Implement advanced camera modes and automation
  - Code Cinematic Mode with automatic zoom in/out to frame action appropriately and jump to important events with timing delays
  - Implement Esports Mode with automated broadcast-quality camera work, player POV cut-ins, and instant replay queuing
  - Create alert system with visual indicators, hotkey navigation, and automatic camera movement to relevant locations
  - Code picture-in-picture overlay system for handling multiple simultaneous events when rapid camera jumps aren't feasible
  - Implement auto-focus mode that can be toggled on/off for following action automatically
  - Write unit tests for camera mode transitions, alert handling, and automated camera behavior
  - _Requirements: 11.3, 11.4, 11.5_

- [ ] 10.3 Implement orientation aids and manual control
  - Code orientation aid systems: compass directions, coordinate systems, and pentagon grid overlays for player navigation
  - Implement camera bookmark system for saving and returning to specific positions and "return to base" hotkeys
  - Create full manual camera control with free rotation, zoom, pan, and saved camera positions
  - Implement toggleable auto-focus mode and orientation aids that can be enabled/disabled
  - Write unit tests for orientation calculations, bookmark management, and manual control responsiveness
  - _Requirements: 11.6, 11.7_

- [ ] 11. Implement client-server architecture
- [ ] 11.1 Create game server foundation
  - Code authoritative game state management on dedicated servers
  - Implement player command processing and validation
  - Create game tick advancement and state synchronization
  - Write unit tests for server state management and command processing
  - _Requirements: 9.1, 9.2_

- [ ] 11.2 Implement network communication and resilience
  - Code client-server communication protocols with state synchronization
  - Implement lag compensation and rollback mechanisms
  - Create reconnection capabilities with state recovery
  - Write unit tests for network protocols and disconnection handling
  - _Requirements: 9.3, 9.4, 9.5_

- [ ] 12. Create matchmaking and lobby system
- [ ] 12.1 Implement matchmaking core
  - Code player queue management with skill-based matching
  - Implement tempo-based faction pairing for placement matches
  - Create server allocation and custom server connection support
  - Write unit tests for matchmaking algorithms and server allocation
  - _Requirements: 10.1, 10.2, 10.3_

- [ ] 12.2 Implement multiplayer game management
  - Code support for 1v1, 2v2, and larger multiplayer formats
  - Implement AI takeover and pause/resume functionality
  - Create deterministic gameplay with synchronized state
  - Write unit tests for multiplayer coordination and AI integration
  - _Requirements: 10.4, 10.5_

- [ ] 13. Implement replay system with event streaming
- [ ] 13.1 Create event recording and playback system
  - Code lightweight event stream recording system capturing all game events as GameEvent entities rather than video data
  - Implement replay file creation and loading from event streams with ReplayData structure
  - Create replay validation and integrity checking to ensure replays produce identical outcomes
  - Implement EventStreamManager for client-side replay file management and local storage
  - Write unit tests for event recording accuracy, replay file integrity, and playback consistency
  - _Requirements: 14.1, 14.5_

- [ ] 13.2 Implement advanced replay features and annotation system
  - Code multiple camera modes for replay viewing: Cinematic (smooth transitions), Esports (auto-focus battles with instant replays), Manual (full camera control)
  - Implement 3D-anchored annotation system with drawing tools for map markup with persistent overlays anchored to 3D coordinates
  - Create annotation merging system allowing annotations to be saved as additional events and merged with original replay
  - Code replay branching system allowing players to take control at any point and play from that state while preserving relevant annotations
  - Implement spectator tools with picture-in-picture, player POV cut-ins, and automated broadcast-quality camera work
  - Write unit tests for replay camera modes, annotation persistence, and branching functionality
  - _Requirements: 14.2, 14.3, 14.4_

- [ ] 14. Create map editor and user-generated content system
- [ ] 14.1 Implement map editor core functionality
  - Code geodesic map creation tools with customizable resolution and size controls for full-sphere, ring, and fragment map types
  - Implement resource node placement system for Metal/Fuel deposits and terrain feature editing tools
  - Create underground layer design tools for multi-tier underground construction
  - Implement faction spawn point placement at pentagon locations for geometric fairness
  - Code map validation system to ensure compatibility with all faction mechanics and balance requirements
  - Write unit tests for map editor operations, validation algorithms, and export/import functionality
  - _Requirements: 13.1, 13.2_

- [ ] 14.2 Implement scenario creation and community sharing
  - Code custom victory condition setup allowing creators to enable/disable Destruction, Core Control, and Economic victory types
  - Implement pre-placed unit system and scripted event creation for custom scenarios
  - Create custom starting resources and faction configuration options for scenarios
  - Implement community map sharing system with rating, search functionality, and compatibility validation
  - Code map publishing pipeline ensuring maps work with all faction mechanics before approval
  - Write unit tests for scenario validation, sharing functionality, and community rating system
  - _Requirements: 13.3, 13.4, 13.5_

- [ ] 15. Implement tutorial and onboarding system
- [ ] 15.1 Create general tutorial system
  - Code general RTS mechanics tutorial covering basic controls, camera navigation, and unit selection
  - Implement five-resource economy tutorial with interactive examples showing Metal/Fuel extraction and Food/Polymers/Electricity production
  - Create tutorial progress tracking and validation system with TutorialManager interface
  - Implement practice scenarios and AI skirmish modes unlocked after tutorial completion
  - Write unit tests for tutorial completion detection and progression tracking
  - _Requirements: 16.1, 16.5_

- [ ] 15.2 Implement faction-specific tutorials
  - Code Scrapyard Survivors tutorial (2-5 minutes) focusing on scavenge loop, mobile hive mechanics, and Undercurrent Mode
  - Implement Celestial Fists tutorial demonstrating wall expansion, squad reinforcement, and Call to Arms ability
  - Create Technomancers tutorial covering pilot-drone uplink system, drone reserve swapping, and energy grid management
  - Code Auporan Dwellers tutorial showing zone placement, tunnel network benefits, and terraforming capabilities
  - Implement Industrial Warmachine tutorial demonstrating rail network construction, mobile building mechanics, and logistics chains
  - Create guided sequences with step-by-step instructions and validation checkpoints for each faction's signature mechanics
  - Write unit tests for faction tutorial completion, mechanic demonstration, and progression validation
  - _Requirements: 16.2, 16.3, 16.4_

- [ ] 16. Implement faction-specific worker and building systems
- [ ] 16.1 Create Scrapyard Survivors worker system
  - Implement Scavenger Crew workers that build all buildings (fastest at Tier 1, slower at higher tiers)
  - Code Caravan Pilot upgrade system (loses build ability, gains mobile depot/hauling capability)
  - Implement combat units building Tier 1 structures slowly as backup builders
  - Create starting setup: 6 Scavenger Crews, 2 Scavenger Raiders, Scrap Citadel, Scrap Mine, Scrap Garden, Jury-Rigged Generator with Power Lines
  - Write unit tests for worker flexibility, caravan mechanics, and combat unit building
  - _Requirements: 1.3, 5.1_

- [ ] 16.2 Create Celestial Fists dual-worker system
  - Implement Citizen-Builder workers (best at walls/pipelines, weak at high-tech, garrison with rifle fire)
  - Code Engineer Squad workers (best at high-tech, weak at walls/pipelines, garrison with RPG/anti-armor fire)
  - Create wall-based expansion system requiring walls to expand build radius
  - Implement pipeline distribution system under walls for fuel and electricity
  - Create starting setup: 8 Citizen-Builders, Command Citadel, Ore Quarry, Food Garden, Fuel Generator, Wall segments with Fortress Gate
  - Write unit tests for dual-worker specialization, wall expansion, and pipeline mechanics
  - _Requirements: 1.4, 5.2_

- [ ] 16.3 Create Technomancers automated worker system
  - Implement Utility Drones (pilot-controlled, assign build sites then leave for auto-build, battery-powered with charging requirements)
  - Code Maintenance Drones (must attend build sites, can accelerate auto-builds, can recharge shields)
  - Create battery management system with charging pads, wireless recharging upgrades, and feedback mode for grid power dumping
  - Implement RCC dependency with graceful degradation when Remote Control Centers are destroyed
  - Create starting setup: 4 Utility Drones, 1 Maintenance Drone, 4 Pilots, 1 Drone Swarm, Crystal Citadel with RCC slots, Energy Pylon, Energy Battery
  - Write unit tests for automated building, battery mechanics, and RCC dependency
  - _Requirements: 1.5, 5.3_

- [ ] 16.4 Create Auporan Dwellers tunnel-based worker system
  - Implement Bio-Cultivator workers (builds Tier 1 anywhere, slow at tunnels, tends Hydroponics)
  - Code Burrower Drone workers (builds all buildings but only if connected to tunnel network, fast tunnel creation)
  - Create tunnel network system where all buildings act as tunnel entrances with automatic unit transport
  - Implement starting setup: 2 Bio-Cultivators, 2 Burrower Drones, Living Citadel, Ore Harvester, 2 Hydroponics Labs with passive electricity generation
  - Write unit tests for tunnel connectivity, worker specialization, and network transport
  - _Requirements: 1.6, 5.4_

- [ ] 16.5 Create Industrial Warmachine rail-based worker system
  - Implement Track Layer workers (builds all buildings, must attend, repairs rails and mobile buildings)
  - Code Resource Cart units (hauler only, cannot build, upgradeable with static defense modules, acts as defense when parked on rails)
  - Create rail network system with Rail Hubs, Rail Segments, and mobile building relocation along rails
  - Implement Rail Hub Refinery upgrade for unique Tier 1 macro advantage with fuel redistribution
  - Create starting setup: 5 Track Layers, 3 Steel Troopers, Iron Citadel, Ore Drill, Food Factory, Fuel Generator, Rail Hub with connecting segments
  - Write unit tests for rail construction, mobile buildings, and dual-use resource carts
  - _Requirements: 1.7, 5.5_

- [ ] 17. Integration and final system wiring
- [ ] 17.1 Integrate all faction systems with game engine
  - Wire faction mechanics into main game loop and GameStateManager with proper tick processing
  - Integrate resource system with faction bonuses, emphasis calculations, and starvation/shortage effects
  - Connect underground expansion system with faction-specific mechanics (Dwellers tunnels, Survivors stacking, etc.)
  - Implement faction balance validation ensuring tempo curve works correctly (4-face rush to 20-face late-game)
  - Write integration tests for faction interaction edge cases, resource sharing, and mechanic conflicts
  - _Requirements: All faction-related requirements (1.*, 5.*, 7.*)_

- [ ] 17.2 Integrate camera system with replay and spectator tools
  - Connect advanced camera modes (Cinematic, Esports, Manual) with replay viewing and live spectating
  - Integrate 3D-anchored annotation system with camera positioning and coordinate transformations
  - Wire spectator tools with live match viewing, including picture-in-picture and POV cut-ins
  - Implement camera bookmark system integration with replay branching and annotation preservation
  - Write integration tests for camera mode transitions, annotation persistence, and spectator functionality
  - _Requirements: 11.*, 14.*_

- [ ] 17.3 Integrate victory conditions with all game systems
  - Connect victory detection with faction mechanics, subway station control, and underground core access
  - Integrate Economic Victory with resource system calculations and faction bonus multipliers
  - Wire Core Control Victory with 5-minute hold requirement and underground tier access validation
  - Implement configurable victory condition system allowing hosts to enable/disable each type
  - Write integration tests for victory condition interactions, timing validation, and edge cases
  - _Requirements: 6.*, 15.*_

- [ ] 17.4 Final system integration and comprehensive testing
  - Integrate matchmaking system with game server allocation and tempo-based faction pairing for placement matches
  - Connect tutorial system with main game progression, unlocking practice scenarios and AI skirmish modes
  - Wire map editor with multiplayer match creation, ensuring custom maps work with all faction mechanics
  - Implement complete client-server architecture with authoritative game state and custom server support
  - Write comprehensive end-to-end tests covering complete game flows: tutorial → matchmaking → match → replay
  - _Requirements: All requirements_