# Implementation Plan

- [ ] 1. Set up project structure and core interfaces
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Create directory structure following onion architecture layers (Common, Domain, Enactment, Infrastructure, Integration, Presentation)
  - Define TypeScript interfaces for core data structures: GameState, PlayerState, UnitInstance, BuildingInstance
  - Implement JSON schemas for all entity types (Identity, Catalog, Session, Map, Economy, Combat, Zone, Replay contexts)
  - Set up build system with TypeScript 5.8, Angular 20, and BabylonJS 8.15.1
  - _Requirements: All requirements depend on this foundation_

- [ ] 2. Implement geodesic map system and basic geometry
- [ ] 2.1 Create geodesic polyhedron generation
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Implement mathematical utilities for geodesic sphere creation with configurable resolution
  - Write algorithms for hexagonal tile placement with pentagon distribution at regular intervals
  - Create 3D coordinate system for navigating geodesic surfaces with smooth zoom transitions
  - Implement map types: Full Sphere (complete globe), Ring Maps (band around globe), Globe Fragment (up to 2/3 sphere)
  - Write unit tests for geometric calculations and coordinate transformations
  - _Requirements: 12.1, 12.2, 12.3_

- [ ] 2.2 Implement spawn zone system and fairness
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code five-zone system: Red zones (spawn areas at pentagons), Orange zones (inner expansion), Yellow zones (outer expansion), Light Blue zones (buffer areas), Dark Blue zones (intra-spawn wild areas)
  - Implement spawn point placement system using Red zones at pentagon tiles for geometric fairness and equal player distances
  - Create resource distribution algorithms enforcing minimum/maximum resource guarantees in Red, Orange, Yellow, and Light Blue zones for fair early game
  - Implement restriction system ensuring subway stations, hazards, and asymmetrical features only spawn in Dark Blue intra-spawn zones
  - Code Fair Mode (enforces spawn zone rules) and Creative Mode (allows rule breaking) for map editor
  - Write unit tests for zone classification, fairness validation, and resource distribution balance
  - _Requirements: 12.1, 12.2, 12.3, 12.4, 12.5_

- [ ] 2.3 Implement strategic feature placement
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Create subway station placement system with randomized pairings (hidden until discovered) restricted to Dark Blue intra-spawn zones only
  - Implement Central Underground Core placement for Core Control victory condition in contested areas
  - Code hazard and asymmetrical terrain feature placement restricted to Dark Blue zones
  - Write unit tests for strategic feature placement validation and zone restriction compliance
  - _Requirements: 13.2, 16.1_

- [ ] 3. Implement five-resource economy system
- [ ] 3.1 Create resource management core
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Implement ResourceBundle data structure with Metal, Fuel, Food, Polymers, Electricity distinguishing between consumable (Metal, Polymers) and capacity-based (Food, Fuel, Electricity) resources
  - Code resource extraction system: Metal/Fuel from deposits, Food/Polymers/Electricity from production buildings
  - Create dual resource tracking: consumable resources (current amount) and capacity resources (current production rate vs. current consumption rate)
  - Implement capacity validation system preventing unit/building construction when insufficient capacity available
  - Create resource transaction processing with atomic operations and validation for both consumable and capacity-based resources
  - Implement resource storage for consumable resources and capacity management for continuous supply resources
  - Write unit tests for resource calculations, capacity validation, extraction rates, and edge cases
  - _Requirements: 2.1, 2.2, 2.3_

- [ ] 3.2 Implement capacity-based resource system and faction specialization
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Food capacity system where units require continuous food supply (e.g., 2 food capacity out of total X food production) rather than one-off payments
  - Implement Electricity capacity system where buildings require continuous electricity supply (e.g., 3 electricity capacity out of total Y electricity production)
  - Code Fuel capacity system similar to electricity where certain units/buildings require continuous fuel supply
  - Implement capacity validation preventing construction of new units/buildings when insufficient capacity available
  - Create faction-specific resource emphasis bonuses: Survivors=Metal, Fists=Fuel, Technomancers=Electricity, Dwellers=Food, Warmachine=Polymers
  - Implement resource decay mechanics and efficiency calculations for capacity-based resources
  - Write unit tests for capacity validation, resource effects, faction bonuses, and capacity management mechanics
  - _Requirements: 2.4, 2.5, 2.6_

- [ ] 4. Create faction system with Platonic solid identity
- [ ] 4.1 Implement faction definitions and core mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Create FactionDefinition data structures mapping to Platonic solids: Tetrahedron(4)=Survivors, Cube(6)=Fists, Octahedron(8)=Technomancers, Dodecahedron(12)=Dwellers, Icosahedron(20)=Warmachine
  - Implement difficulty ratings: 1/5 to 5/5 based on face count, with tempo classifications (rush to late-game)
  - Code starting resource configurations and faction-specific resource emphasis bonuses
  - Implement maximum upgrades per unit based on face count (Tetrahedron=1, Cube=2, Octahedron=3, Dodecahedron=4, Icosahedron=5)
  - Write unit tests for faction initialization, tempo balance, and property validation
  - _Requirements: 1.1, 1.2, 7.1, 7.2, 7.3_

- [ ] 4.2 Implement Scrapyard Survivors faction mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code scavenging system for resource extraction from unit/building wrecks with bounded returns
  - Implement Undercurrent Mode mobile spawn capability when all buildings destroyed (time-limited grace period)
  - Create self-destruction mechanics with full resource refunds for own buildings
  - Implement surface-stacked infrastructure and mobile depot/caravan systems
  - Code combat units building Tier 1 structures slowly as backup builders
  - Write unit tests for scavenging loops, mobile spawn mechanics, and resource refunds
  - _Requirements: 1.3, 5.1_

- [ ] 4.3 Implement Celestial Fists faction mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code wall-based expansion system requiring walls to expand build radius
  - Implement fuel pipeline construction along walls with underground distribution
  - Create squad-based unit control system with individual member loss tracking and morale bonuses
  - Code Call to Arms ability converting workers into militia units
  - Implement formation commands (Form Wall, Sprint, Charge) and commander aura systems
  - Write unit tests for wall expansion, squad mechanics, and morale calculations
  - _Requirements: 1.4, 5.2_

- [ ] 4.4 Implement Technomancers faction mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code pilot-drone relationship system via Remote Control Centers with graceful degradation when RCCs destroyed
  - Implement drone reserve stockpiling system with instant replacement from reserves
  - Create energy grid management with wireless power distribution via pylons and battery storage
  - Code Phase Gate teleportation system for unit mobility
  - Implement drone autopilot for non-combat tasks with combat autopilot limitations
  - Write unit tests for RCC dependency, drone reserves, and energy grid mechanics
  - _Requirements: 1.5, 5.3_

- [ ] 4.5 Implement Auporan Dwellers faction mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code zone generator system creating bio-dome areas with healing/production bonuses and enemy debuffs
  - Implement tunnel network connectivity between all buildings for automatic unit transport
  - Create terraforming capabilities for permanent/temporary terrain modification
  - Code underground unit burrowing mechanics with concealment and tunnel creation
  - Implement espionage/sabotage mechanics with detection and consequence systems
  - Write unit tests for zone effects, tunnel networks, and burrowing mechanics
  - _Requirements: 1.6, 5.4_

- [ ] 4.6 Implement Industrial Warmachine faction mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code rail network construction and validation system with track laying requirements
  - Implement mobile building relocation along rails with mobile/fortified state toggles
  - Create building adjacency buff stacking system with saturation caps to prevent exponential scaling
  - Implement heavy logistics system with Resource Carts doubling as static defense when parked
  - Code siege weapon systems and strategic intel tools for planning counters
  - Write unit tests for rail mechanics, mobile buildings, and buff stacking calculations
  - _Requirements: 1.7, 5.5_

- [ ] 5. Implement worker system and expansion mechanics
- [ ] 5.1 Create core worker management system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Implement WorkerManager interface with generic worker operations: task assignment, capability validation, and upgrade processing
  - Code WorkerInstance and WorkerTask data structures for managing faction-specific workers
  - Create worker task queue system with priority handling and progress tracking
  - Implement worker capability validation system ensuring workers can only perform tasks they're designed for
  - Write unit tests for worker task assignment, capability validation, and queue management
  - _Requirements: 16.1, 16.2, 16.3, 16.4, 16.5_

- [ ] 5.2 Implement Scrapyard Survivors worker system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Zama zama Crew workers: build all buildings (fastest at Tier 1, slower at higher tiers), mine Metal/Fuel, scavenge wrecks
  - Implement Zabatek Pilot upgrade system: loses build ability, gains mobile depot/hauling capability, automates resource hauling
  - Create combat unit construction capability allowing combat units to build Tier 1 buildings slowly as backup builders
  - Implement opportunistic expansion mechanics with forward depots and temporary outposts
  - Write unit tests for worker flexibility, caravan mechanics, combat unit building, and expansion validation
  - _Requirements: 16.1, 16.6_

- [ ] 5.3 Implement Celestial Fists dual-worker system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Citizen-Builder workers: best at walls/pipelines, weak at high-tech, can garrison for rifle fire
  - Implement Tianex Engineer workers: best at high-tech, weak at walls/pipelines, can garrison for RPG/anti-armor fire
  - Create wall-based expansion system requiring walls to expand build radius with fortress-centric expansion mechanics
  - Implement pipeline distribution system under walls for fuel and electricity with safe logistics
  - Write unit tests for dual-worker specialization, wall expansion requirements, and pipeline mechanics
  - _Requirements: 16.2, 16.6_

- [ ] 5.4 Implement Technomancers automated worker system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Utility Drones: pilot-controlled, can assign build sites for auto-build, mine Metal/Fuel efficiently
  - Implement Maintenance Drones: must attend construction sites, can accelerate auto-builds, battery-powered with charging requirements
  - Create battery management system with charging pads, wireless recharging upgrades, and power grid feedback mode
  - Implement energy grid expansion mechanics tied to Energy Pylons extending wireless grid coverage
  - Write unit tests for automated building, battery mechanics, RCC dependency, and grid expansion
  - _Requirements: 16.3, 16.6_

- [ ] 5.5 Implement Auporan Dwellers tunnel-based worker system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Bio-Cultivator workers: builds Tier 1 anywhere, slow at tunnels, tends Hydroponics, produces Food in domes
  - Implement Burrower Drone workers: builds all buildings only if connected to tunnel network, fast tunnel creation, mines Metal/Fuel
  - Create tunnel network connectivity system where all buildings act as tunnel entrances with automatic unit transport
  - Implement tunnel network expansion mechanics with underground connectivity requirements
  - Write unit tests for tunnel connectivity validation, worker specialization, and network transport mechanics
  - _Requirements: 16.4, 16.6_

- [ ] 5.6 Implement Industrial Warmachine rail-based worker system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Track Layer workers: builds all buildings (must attend), repairs rails and mobile buildings, mines Metal/Fuel
  - Implement Pravon Cart units: hauler only, cannot build, upgradeable with static defense modules, acts as defense when parked on rails
  - Create rail network system with Rail Hubs, Rail Segments, and mobile building relocation along rails
  - Implement rail network advancement expansion mechanics with linear territorial control
  - Write unit tests for rail construction requirements, mobile buildings, dual-use resource carts, and rail expansion
  - _Requirements: 16.5, 16.6_

- [ ] 6. Implement detection and counter-detection system
- [ ] 6.1 Create detection infrastructure
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Implement DetectionManager interface with sensor deployment, scanning, and detection resolution
  - Code DetectionSensor and BurrowedUnit data structures for managing stealth and detection mechanics
  - Create Underground Sensors that reveal burrowed units in radius and Seismic Detectors for tunneling activity detection
  - Implement detection radius calculations, energy costs, and sensor upgrade systems
  - Write unit tests for sensor deployment, detection calculations, and radius validation
  - _Requirements: 17.1, 17.2_

- [ ] 6.2 Implement burrowing and stealth mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code burrowing transition system allowing units to switch between surface and underground states with 3-5 second transition time
  - Implement burrowed unit mechanics: concealed (invisible unless detected), cannot attack, can tunnel slowly
  - Create tunnel creation system where burrowed units can create permanent tunnel connections between buildings
  - Implement underground movement validation and pathfinding for burrowed units
  - Write unit tests for burrowing transitions, stealth mechanics, and tunnel creation
  - _Requirements: 17.2, 17.3_

- [ ] 6.3 Implement counter-detection and deception
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code detection immunity system providing some advanced burrowed units with limited detection immunity capabilities
  - Implement false tunnel signature generation allowing Dwellers to confuse seismic detection systems
  - Create counter-intelligence mechanics with decoy signatures and seismic deception
  - Implement detection resolution system balancing detection attempts against countermeasures
  - Write unit tests for detection immunity, false signatures, and counter-intelligence mechanics
  - _Requirements: 17.4, 17.5_

- [ ] 7. Implement visual system with Platonic solid rendering
- [ ] 7.1 Create vector mode rendering system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Implement Platonic solid arrangement rendering: Infantry=single solid, Vehicle=2-3 solids linearly arranged, Squad=cluster/orbit around core, Building=stacked solids with base ring
  - Code attachment grammar system for upgrades using fixed attachment points on Platonic solids
  - Create level-of-detail system: Far=silhouettes, Mid=arrangements+attachments, Close=detailed vectors and animations
  - Implement GPU instancing and procedural mesh generation for efficient Platonic solid rendering
  - Code faction-specific solid mapping: Tetrahedron=Survivors, Cube=Fists, Octahedron=Technomancers, Dodecahedron=Dwellers, Icosahedron=Warmachine
  - Write unit tests for rendering calculations, LOD transitions, and visual state management
  - _Requirements: 1.8, 1.9, 8.1, 8.5_

- [ ] 7.2 Implement visual feedback and skin systems
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code experience and upgrade visual indicators using orbiting smaller solids (rank count) and attachment points
  - Implement health visualization through face-chipping animation or opacity changes for damaged units
  - Create cosmetic skin overlay system with palette + edge thickness + particle sets without altering hitboxes or gameplay
  - Implement shield visualization with halo rings and energy animations with animated edge glows
  - Code colorblind-friendly palettes and high-contrast options for accessibility
  - Write unit tests for visual state transitions, skin application, and accessibility features
  - _Requirements: 8.2, 8.3, 8.4_

- [ ] 8. Create underground expansion and tier system
- [ ] 8.1 Implement underground floor construction and tier gating
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code underground floor creation system beneath surface buildings with UndergroundFloor data structure
  - Implement depth-based technology tier unlocking: Tier 1-2 (shallow) for basic tech, Tier 3-4 (mid) for advanced labs, Tier 5+ (deep) for ultimate tech and super-units
  - Create additional production queue slots, research capabilities, and garrison space per underground floor
  - Implement time and logistics costs for underground construction via digger units or specialized modules
  - Code faction-specific underground mechanics: Survivors use vertical stacking instead of underground bunkers
  - Write unit tests for underground construction, tier validation, and capacity calculations
  - _Requirements: 3.1, 3.2, 3.3, 3.7_

- [ ] 8.2 Implement underground management and tunnel systems
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code cutaway side-profile view system for underground floor management and visualization
  - Implement tunnel connection system specifically for Auporan Dwellers allowing underground unit movement between buildings
  - Create tunnel network connectivity where all Dweller buildings act as tunnel entrances with automatic transport
  - Implement burrowing mechanics for Dweller units with concealment, slow tunneling, and tunnel creation capabilities
  - Code underground sensors and seismic detectors for counter-play against burrowed units
  - Write unit tests for underground visualization, tunnel networks, and burrowing detection systems
  - _Requirements: 3.4, 3.5, 3.6_

- [ ] 9. Implement unit experience and training system
- [ ] 9.1 Create experience and ranking system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code experience point award system: kills=50 XP, assists=25 XP, 10s alive=5 XP with combat participation tracking
  - Implement rank progression system with thresholds: Rank0→1=100, →2=300, →3=700, →4=1500 XP
  - Create rank-based stat improvements and visual indicators using orbiting smaller Platonic solids
  - Implement experience preservation during unit retraining with partial XP retention options
  - Code visual badges and progress bars for XP and rank display with hover tooltips
  - Write unit tests for experience calculations, rank progression, and stat bonus applications
  - _Requirements: 4.1, 4.2, 4.3, 4.6_

- [ ] 9.2 Implement retraining and upgrade systems
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code unit retraining system with rank-based time reduction: trainingTime = baseTime × (1 - rank × 0.15)
  - Implement faction-specific upgrade limits based on Platonic solid faces (Tetrahedron=1, Cube=2, Octahedron=3, Dodecahedron=4, Icosahedron=5)
  - Create upgrade validation system preventing over-upgrading and ensuring faction balance
  - Implement training queue system with visible progress, cancellation options, and partial refunds
  - Code upgrade application system with visual attachment points on Platonic solid arrangements
  - Write unit tests for retraining mechanics, upgrade limits, and queue management
  - _Requirements: 4.4, 4.5_

- [ ] 10. Create subway station system
- [ ] 10.1 Implement subway station placement and capture mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code strategic subway station placement only in Dark Blue intra-spawn zones with randomized connection pairings hidden until discovered
  - Implement capture progress system requiring 60 seconds of uncontested unit presence with diegetic water tank visual indicators
  - Create capture progress decay at 10% per 10 seconds when uncontested and reset when enemy contests
  - Implement faction-specific bonuses: Survivors (+5 Polymers per minute), Fists (pipeline network extension), Technomancers (power grid node), Dwellers (tunnel network entrance), Warmachine (rail network integration)
  - Code static defense activation upon successful capture and station HP system (500 HP)
  - Write unit tests for station placement algorithms, zone restriction validation, capture timing mechanics, and faction bonus calculations
  - _Requirements: 16.1, 16.2, 16.3, 16.4_

- [ ] 10.2 Implement subway transportation and breach mechanics
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code instant teleportation system between connected stations for controlling player
  - Implement connection discovery system: lines only revealed when units actually travel through them
  - Create station destruction mechanics with 60-second breach windows allowing any faction to use connection before collapse
  - Implement spectator visibility: show all connections to viewers while keeping them hidden from players until discovered
  - Write unit tests for teleportation mechanics, discovery system, and breach window timing
  - _Requirements: 16.5, 16.6_

- [ ] 11. Implement victory condition system
- [ ] 11.1 Create configurable victory conditions
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code victory condition configuration system for match setup allowing hosts to enable/disable each victory type
  - Implement Destruction Victory detection for eliminated HQs and spawns with Survivors' Undercurrent Mode exception
  - Create Core Control Victory with 5-minute hold requirement at Central Underground Core
  - Write unit tests for victory condition validation and timing
  - _Requirements: 6.1, 6.2, 6.3_

- [ ] 11.2 Implement Economic Victory system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Economic Victory detection with 3× income advantage requirement over all opponents
  - Implement 10-minute countdown with public resource disclosure showing all players' resource generation rates
  - Create victory condition combination validation ensuring at least one victory type is always enabled
  - Write unit tests for economic calculations and victory timing
  - _Requirements: 6.4, 6.5, 6.6_

- [ ] 12. Create advanced camera and navigation system
- [ ] 12.1 Implement core camera functionality
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code seamless zoom system from tactical (flat-feeling) to strategic (full globe visible) views with smooth transitions
  - Implement minimap globe rotation system with corresponding main camera perspective rotation
  - Create smooth camera movement interpolation and coordinate transformation for geodesic surfaces
  - Implement camera position and state management with CameraPosition and CameraState interfaces
  - Write unit tests for camera calculations, zoom transitions, and coordinate transformations
  - _Requirements: 11.1, 11.2_

- [ ] 12.2 Implement advanced camera modes and automation
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Cinematic Mode with automatic zoom in/out to frame action appropriately and jump to important events with timing delays
  - Implement Esports Mode with automated broadcast-quality camera work, player POV cut-ins, and instant replay queuing
  - Create alert system with visual indicators, hotkey navigation, and automatic camera movement to relevant locations
  - Code picture-in-picture overlay system for handling multiple simultaneous events when rapid camera jumps aren't feasible
  - Implement auto-focus mode that can be toggled on/off for following action automatically
  - Write unit tests for camera mode transitions, alert handling, and automated camera behavior
  - _Requirements: 11.3, 11.4, 11.5_

- [ ] 12.3 Implement orientation aids and manual control
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code orientation aid systems: compass directions, coordinate systems, and pentagon grid overlays for player navigation
  - Implement camera bookmark system for saving and returning to specific positions and "return to base" hotkeys
  - Create full manual camera control with free rotation, zoom, pan, and saved camera positions
  - Implement toggleable auto-focus mode and orientation aids that can be enabled/disabled
  - Write unit tests for orientation calculations, bookmark management, and manual control responsiveness
  - _Requirements: 11.6, 11.7_

- [ ] 13. Implement client-server architecture
- [ ] 13.1 Create game server foundation
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code authoritative game state management on dedicated servers with GameStateManager interface
  - Implement player command processing and validation with proper security checks
  - Create game tick advancement and state synchronization across all connected clients
  - Write unit tests for server state management and command processing
  - _Requirements: 9.1, 9.2_

- [ ] 13.2 Implement network communication and resilience
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code client-server communication protocols with state synchronization and delta compression
  - Implement lag compensation and rollback mechanisms for fair gameplay under network conditions
  - Create reconnection capabilities with state recovery and custom server connection support
  - Write unit tests for network protocols and disconnection handling
  - _Requirements: 9.3, 9.4, 9.5_

- [ ] 14. Create matchmaking and lobby system
- [ ] 14.1 Implement matchmaking core
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code player queue management with skill-based matching and MatchmakingManager interface
  - Implement tempo-based faction pairing for placement matches (rush vs rush, turtle vs turtle)
  - Create server allocation and custom server connection support with fallback to official servers
  - Write unit tests for matchmaking algorithms and server allocation
  - _Requirements: 10.1, 10.2, 10.3_

- [ ] 14.2 Implement multiplayer game management
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code support for 1v1, 2v2, and larger multiplayer formats with proper game state synchronization
  - Implement AI takeover and pause/resume functionality for competitive matches
  - Create deterministic gameplay with synchronized state across all clients
  - Write unit tests for multiplayer coordination and AI integration
  - _Requirements: 10.4, 10.5_

- [ ] 15. Implement replay system with event streaming
- [ ] 15.1 Create event recording and playback system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code lightweight event stream recording system capturing all game events as GameEvent entities rather than video data
  - Implement replay file creation and loading from event streams with ReplayData structure
  - Create replay validation and integrity checking to ensure replays produce identical outcomes
  - Implement EventStreamManager for client-side replay file management and local storage
  - Write unit tests for event recording accuracy, replay file integrity, and playback consistency
  - _Requirements: 14.1, 14.5_

- [ ] 15.2 Implement advanced replay features and annotation system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code multiple camera modes for replay viewing: Cinematic (smooth transitions), Esports (auto-focus battles with instant replays), Manual (full camera control)
  - Implement 3D-anchored annotation system with drawing tools for map markup with persistent overlays anchored to 3D coordinates
  - Create annotation merging system allowing annotations to be saved as additional events and merged with original replay
  - Code replay branching system allowing players to take control at any point and play from that state while preserving relevant annotations
  - Implement spectator tools with picture-in-picture, player POV cut-ins, and automated broadcast-quality camera work
  - Write unit tests for replay camera modes, annotation persistence, and branching functionality
  - _Requirements: 14.2, 14.3, 14.4_

- [ ] 16. Create map editor and user-generated content system
- [ ] 16.1 Implement map editor core functionality
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code geodesic map creation tools with customizable resolution and size controls for full-sphere, ring, and fragment map types
  - Implement resource node placement system for Metal/Fuel deposits and terrain feature editing tools
  - Create underground layer design tools for multi-tier underground construction
  - Implement faction spawn point placement at pentagon locations for geometric fairness
  - Code map validation system to ensure compatibility with all faction mechanics and balance requirements
  - Write unit tests for map editor operations, validation algorithms, and export/import functionality
  - _Requirements: 13.1, 13.2_

- [ ] 16.2 Implement scenario creation and community sharing
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code custom victory condition setup allowing creators to enable/disable Destruction, Core Control, and Economic victory types
  - Implement pre-placed unit system and scripted event creation for custom scenarios
  - Create custom starting resources and faction configuration options for scenarios
  - Implement community map sharing system with rating, search functionality, and compatibility validation
  - Code map publishing pipeline ensuring maps work with all faction mechanics before approval
  - Write unit tests for scenario validation, sharing functionality, and community rating system
  - _Requirements: 13.3, 13.4, 13.5_

- [ ] 17. Implement tutorial and onboarding system
- [ ] 17.1 Create general tutorial system
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code general RTS mechanics tutorial covering basic controls, camera navigation, and unit selection
  - Implement five-resource economy tutorial with interactive examples showing Metal/Fuel extraction and Food/Polymers/Electricity production
  - Create tutorial progress tracking and validation system with TutorialManager interface
  - Implement practice scenarios and AI skirmish modes unlocked after tutorial completion
  - Write unit tests for tutorial completion detection and progression tracking
  - _Requirements: 18.1, 18.5_

- [ ] 17.2 Implement faction-specific tutorials
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Code Scrapyard Survivors tutorial (2-5 minutes) focusing on scavenge loop, mobile hive mechanics, and Undercurrent Mode
  - Implement Celestial Fists tutorial demonstrating wall expansion, squad reinforcement, and Call to Arms ability
  - Create Technomancers tutorial covering pilot-drone uplink system, drone reserve swapping, and energy grid management
  - Code Auporan Dwellers tutorial showing zone placement, tunnel network benefits, and terraforming capabilities
  - Implement Industrial Warmachine tutorial demonstrating rail network construction, mobile building mechanics, and logistics chains
  - Create guided sequences with step-by-step instructions and validation checkpoints for each faction's signature mechanics
  - Write unit tests for faction tutorial completion, mechanic demonstration, and progression validation
  - _Requirements: 18.2, 18.3, 18.4_

- [ ] 18. Integration and final system wiring
- [ ] 18.1 Integrate all faction systems with game engine
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Wire faction mechanics into main game loop and GameStateManager with proper tick processing
  - Integrate resource system with faction bonuses, emphasis calculations, and starvation/shortage effects
  - Connect underground expansion system with faction-specific mechanics (Dwellers tunnels, Survivors stacking, etc.)
  - Implement faction balance validation ensuring tempo curve works correctly (4-face rush to 20-face late-game)
  - Write integration tests for faction interaction edge cases, resource sharing, and mechanic conflicts
  - _Requirements: All faction-related requirements (1.*, 5.*, 7.*)_

- [ ] 18.2 Integrate camera system with replay and spectator tools
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Connect advanced camera modes (Cinematic, Esports, Manual) with replay viewing and live spectating
  - Integrate 3D-anchored annotation system with camera positioning and coordinate transformations
  - Wire spectator tools with live match viewing, including picture-in-picture and POV cut-ins
  - Implement camera bookmark system integration with replay branching and annotation preservation
  - Write integration tests for camera mode transitions, annotation persistence, and spectator functionality
  - _Requirements: 11.*, 14.*_

- [ ] 18.3 Integrate victory conditions with all game systems
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Connect victory detection with faction mechanics, subway station control, and underground core access
  - Integrate Economic Victory with resource system calculations and faction bonus multipliers
  - Wire Core Control Victory with 5-minute hold requirement and underground tier access validation
  - Implement configurable victory condition system allowing hosts to enable/disable each type
  - Write integration tests for victory condition interactions, timing validation, and edge cases
  - _Requirements: 6.*, 15.*_

- [ ] 18.4 Final system integration and comprehensive testing
  - Create an implementation plan for this task to expand upon the implmentation details before starting to work on the task.
  - Integrate matchmaking system with game server allocation and tempo-based faction pairing for placement matches
  - Connect tutorial system with main game progression, unlocking practice scenarios and AI skirmish modes
  - Wire map editor with multiplayer match creation, ensuring custom maps work with all faction mechanics
  - Implement complete client-server architecture with authoritative game state and custom server support
  - Write comprehensive end-to-end tests covering complete game flows: tutorial → matchmaking → match → replay
  - _Requirements: All requirements_