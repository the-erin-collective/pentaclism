# Requirements Document

## Introduction

Pentaclism is a real-time strategy game set on a hostile planet where five distinct factions compete for dominance through surface and underground expansion. Each faction is built around one of the five Platonic solids, creating unique gameplay tempos, visual identities, and strategic approaches. The game emphasizes faction asymmetry, underground expansion mechanics, and a five-resource economy system that drives meaningful strategic choices.

The core innovation lies in the Platonic Tempo Curve - where the number of faces on each faction's geometric symbol directly correlates to their complexity and intended win timing, from the chaotic 4-face Tetrahedron rush faction to the methodical 20-face Icosahedron late-game powerhouse.

## Requirements

### Requirement 1: Faction System with Platonic Solid Identity

**User Story:** As a player, I want to choose from five distinct factions each with unique mechanics and visual identity based on Platonic solids, so that I can experience varied gameplay styles and strategic approaches.

#### Acceptance Criteria

1. WHEN the game starts THEN the system SHALL provide exactly five playable factions: Scrapyard Survivors (Tetrahedron, 4 faces, rush tempo), Celestial Fists (Cube, 6 faces, defensive tempo), Technomancers (Octahedron, 8 faces, flexible tempo), Auporan Dwellers (Dodecahedron, 12 faces, macro tempo), and Industrial Warmachine (Icosahedron, 20 faces, late-game tempo)
2. WHEN a faction is selected THEN the system SHALL display its Platonic solid, face count, difficulty rating (1-5 based on face count), and tempo classification
3. WHEN playing Scrapyard Survivors THEN the system SHALL provide scavenging mechanics, mobile spawn capability, full resource refunds on self-destruction, and surface-stacked infrastructure
4. WHEN playing Celestial Fists THEN the system SHALL require wall-based expansion with fuel pipelines buildable along walls, provide squad-based unit control with morale systems, and enable "Call to Arms" worker militia conversion
5. WHEN playing Technomancers THEN the system SHALL require pilot-drone relationships via Remote Control Centers and allow stockpiling of drones to be piloted, provide energy grid management with wireless power distribution and energy batteries
6. WHEN playing Auporan Dwellers THEN the system SHALL provide a "zone generator" structure enabling zone creation which buffs allied units or debuffs enemy units, a tunnel network connectivity between buildings, terraforming capabilities, and underground unit burrowing
7. WHEN playing Industrial Warmachine THEN the system SHALL require rail network construction, enable mobile building relocation on rails
8. WHEN viewing units and buildings THEN the system SHALL render them using arrangements and transformations to their faction's Platonic solid as the base geometric form
9. IF vector visual mode is enabled THEN the system SHALL display all units as arrangements of their faction's Platonic solid with attachment grammar for upgrades and states

### Requirement 2: Five-Resource Economy System

**User Story:** As a player, I want to manage five distinct resources with different acquisition methods, so that I can make strategic economic decisions and leverage my faction's resource specialization.

#### Acceptance Criteria

1. WHEN starting a match THEN the system SHALL initialize five resource types: Metal (natural), Fuel (natural), Food (produced), Polymers (produced), and Electricity (produced)
2. WHEN extracting resources THEN the system SHALL allow Metal and Fuel extraction from visible/hidden deposits respectively
3. WHEN producing resources THEN the system SHALL require Food, Polymers, and Electricity to be manufactured using buildings and workers
4. WHEN Food runs out THEN the system SHALL cause living units to slowly lose HP
5. WHEN Electricity runs out THEN the system SHALL power down buildings until capacity is restored
6. WHEN playing different factions THEN the system SHALL provide faction-specific resource emphasis bonuses (Survivors=Metal, Fists=Fuel, Technomancers=Electricity, Dwellers=Food, Warmachine=Polymers)

### Requirement 3: Underground Expansion and Tier System

**User Story:** As a player, I want to expand underground through multiple tiers to unlock advanced technologies and defensive positions, so that I can access powerful late-game options while managing surface vulnerability.

#### Acceptance Criteria

1. WHEN building structures THEN the system SHALL allow construction of underground floors beneath surface buildings
2. WHEN digging deeper THEN the system SHALL unlock technology tiers: Tier 1-2 (shallow) for basic tech, Tier 3-4 (mid) for advanced labs, Tier 5+ (deep) for ultimate tech and super-units
3. WHEN adding underground floors THEN the system SHALL provide additional production queues, research slots, and garrison space per floor
4. WHEN viewing buildings THEN the system SHALL allow toggling to cutaway side-profile view to see and manage underground floors
5. IF playing Auporan Dwellers THEN the system SHALL allow tunnel networks for underground unit movement
6. WHEN constructing underground THEN the system SHALL require time and logistics costs via digger units or specialized modules
7. WHEN the faction is the "Scrapyard Survivors" this same mechanic is used for vertically stacked floors instead of underground bunkers.

### Requirement 4: Unit Experience and Training System

**User Story:** As a player, I want my units to gain experience and be retrained into new roles, so that I can preserve my investment in veteran forces and adapt my army composition dynamically.

#### Acceptance Criteria

1. WHEN units are created THEN they start as untrained and SHALL be trainable into more specialized units
2. WHEN units participate in combat THEN the system SHALL award experience points based on kills, damage dealt, and survival time
3. WHEN units gain sufficient XP THEN the system SHALL promote them to higher ranks with improved combat statistics
4. WHEN retraining units THEN the system SHALL reduce training time based on unit rank (higher rank = faster retraining)
5. WHEN upgrading units THEN the system SHALL limit maximum upgrades per unit based on faction's Platonic solid face count (Tetrahedron=1, Cube=2, Octahedron=3, Dodecahedron=4, Icosahedron=5)
6. WHEN units are retrained THEN the system SHALL preserve their accumulated experience points

### Requirement 5: Faction-Specific Signature Mechanics

**User Story:** As a player, I want each faction to have unique gameplay mechanics that reflect their identity and strategic focus, so that mastering different factions provides distinct gameplay experiences.

#### Acceptance Criteria

1. WHEN playing Scrapyard Survivors THEN the system SHALL allow scavenging resources from wrecks, enable "Undercurrent Mode" mobile spawn when all buildings are destroyed, and provide full resource refunds when destroying own buildings
2. WHEN playing Celestial Fists THEN the system SHALL require wall construction to expand build radius, enable squad-based unit control with morale bonuses, and provide "Call to Arms" ability to convert workers into militia
3. WHEN playing Technomancers THEN the system SHALL require pilots to control drones via Remote Control Centers, allow drone reserves for instant replacement, and enable Phase Gate teleportation
4. WHEN playing Auporan Dwellers THEN the system SHALL create bio-dome zones with healing/production bonuses, allow terraforming to alter terrain, and enable underground tunnel networks for unit movement
5. WHEN playing Industrial Warmachine THEN the system SHALL require rail networks for optimal unit/building movement, allow mobile buildings that can relocate along rails, and provide buff stacking from adjacent buildings

### Requirement 6: Victory Conditions and Game Flow

**User Story:** As a player, I want configurable victory conditions that can be enabled or disabled to create different game modes and strategies, so that I can play matches that emphasize different aspects of gameplay.

#### Acceptance Criteria

1. WHEN setting up matches THEN the system SHALL allow hosts to enable/disable each victory condition type: Destruction, Core Control, and Economic Dominance
2. WHEN at least one victory condition is enabled AND all enemy HQs and mobile spawns are destroyed THEN the system SHALL declare a Destruction Victory if enabled
3. WHEN Core Control is enabled AND a player captures and holds the Central Underground Core for 5 uninterrupted minutes THEN the system SHALL declare a Core Victory
4. WHEN Economic Victory is enabled AND a player achieves 3× the resource income of all opponents for 10 minutes THEN the system SHALL begin an Economic Victory countdown with public resource disclosure
5. WHEN victory conditions are met THEN the system SHALL immediately end the match and display victory/defeat screens
6. WHEN only Destruction Victory is enabled THEN the system SHALL create the most aggressive game mode focused purely on military conflict

### Requirement 7: Tempo-Based Faction Balance

**User Story:** As a player, I want faction complexity and win timing to scale predictably with their Platonic solid face count, so that I can choose factions that match my preferred game pace and skill level.

#### Acceptance Criteria

1. WHEN selecting factions THEN the system SHALL display difficulty ratings: Tetrahedron (1/5), Cube (2/5), Octahedron (3/5), Dodecahedron (4/5), Icosahedron (5/5)
2. WHEN playing low-face-count factions THEN the system SHALL provide faster unit production, simpler mechanics, and earlier power spikes
3. WHEN playing high-face-count factions THEN the system SHALL provide more complex mechanics, deeper tech trees, and stronger late-game scaling
4. WHEN matchmaking THEN the system SHALL attempt to pair similar tempo factions for the first 10 placement games
5. WHEN balancing factions THEN the system SHALL ensure each faction has clear weaknesses: Survivors (poor late-game), Fists (vulnerable to mobility), Technomancers (RCC dependency), Dwellers (weak outside zones), Warmachine (slow early game)

### Requirement 8: Visual System with Vector Mode

**User Story:** As a player, I want a clear, readable visual system that uses Platonic solids as the canonical representation with optional cosmetic skins, so that I can easily identify units and factions while enjoying visual variety.

#### Acceptance Criteria

1. WHEN in vector visual mode THEN the system SHALL render all units and buildings as arrangements of their faction's Platonic solid
2. WHEN units gain experience or upgrades THEN the system SHALL display visual indicators using orbiting smaller solids or attachment points
3. WHEN units take damage THEN the system SHALL show health through face-chipping animation or opacity changes
4. WHEN applying cosmetic skins THEN the system SHALL overlay visual themes without altering hitboxes, ranges, or gameplay mechanics
5. WHEN viewing at different distances THEN the system SHALL provide appropriate level-of-detail: far (silhouettes), mid (arrangements + attachments), close (detailed vectors and animations)

### Requirement 9: Client-Server Architecture and Networking

**User Story:** As a player, I want to connect to game servers for multiplayer matches with the option to use custom servers, so that I can enjoy stable online gameplay with flexible hosting options.

#### Acceptance Criteria

1. WHEN starting the game THEN the system SHALL provide a game client that connects to a dedicated game server
2. WHEN connecting THEN the system SHALL default to the publisher's official server but allow players to enter custom server addresses
3. WHEN in multiplayer matches THEN the system SHALL maintain authoritative game state on the server with client prediction for responsiveness
4. WHEN network issues occur THEN the system SHALL provide lag compensation and rollback mechanisms to maintain fair gameplay
5. WHEN players disconnect THEN the system SHALL provide reconnection capabilities and maintain game state during brief disconnections

### Requirement 10: Multiplayer and Matchmaking System

**User Story:** As a player, I want to find balanced matches against opponents of similar skill and faction tempo preferences, so that I can enjoy competitive games regardless of my chosen faction.

#### Acceptance Criteria

1. WHEN queuing for matches THEN the system SHALL support 1v1, 2v2, and larger multiplayer formats
2. WHEN in placement matches THEN the system SHALL attempt to pair players using similar tempo factions (rush vs rush, turtle vs turtle)
3. WHEN matchmaking THEN the system SHALL consider player rating, faction preference, and connection quality
4. WHEN matches are found THEN the system SHALL ensure deterministic gameplay with synchronized game state across all clients
5. WHEN players disconnect THEN the system SHALL provide AI takeover options and pause/resume functionality for competitive matches

### Requirement 11: Advanced Camera and Navigation System

**User Story:** As a player and spectator, I want an intuitive camera system that seamlessly handles geodesic sphere navigation with smart automation and manual control options, so that I can effectively play and watch matches without getting lost or missing important action.

#### Acceptance Criteria

1. WHEN navigating the map THEN the system SHALL provide seamless zoom from tactical (flat-feeling) to strategic (full globe visible) views with smooth transitions
2. WHEN using the minimap THEN the system SHALL allow rotation of the globe view which correspondingly rotates the main camera perspective
3. WHEN important events occur THEN the system SHALL provide an alert system with visual indicators, hotkey navigation, and automatic camera movement to relevant locations
4. WHEN in Cinematic Mode THEN the system SHALL automatically zoom in/out to frame action appropriately, jump to important events with timing delays, and use picture-in-picture when multiple simultaneous events prevent rapid camera jumps
5. WHEN in Esports Mode THEN the system SHALL provide automated broadcast-quality camera work with player POV cut-ins, instant replay queuing, and picture-in-picture overlay when spectators take manual control or replays are shown during live action
6. WHEN taking manual control THEN the system SHALL provide full camera freedom including free rotation, zoom, pan, saved camera positions, and optional auto-focus mode that can be toggled on/off
7. WHEN players feel disoriented THEN the system SHALL provide orientation aids including compass directions, coordinate systems, pentagon grid overlays, and "return to base" hotkeys

### Requirement 12: Geodesic Sphere Map System

**User Story:** As a player, I want to play on innovative geodesic sphere maps that eliminate corners and create true 360-degree strategic gameplay, so that I can experience unique tactical challenges not found in traditional flat RTS maps.

#### Acceptance Criteria

1. WHEN maps are generated THEN the system SHALL create geodesic polyhedron surfaces composed primarily of hexagonal tiles with pentagons interspersed at regular intervals
2. WHEN placing spawn points THEN the system SHALL use pentagon tiles as faction starting locations to ensure geometric fairness and strategic landmarks
3. WHEN selecting map types THEN the system SHALL support Full Sphere maps (complete globe for macro games), Ring Maps (band around the globe for medium games), and Globe Fragment maps (up to two-thirds of sphere with irregular shapes for fast 1v1 games)
4. WHEN playing on sphere maps THEN the system SHALL eliminate corner camping and edge advantages while creating true encirclement and 360-degree threat scenarios
5. WHEN navigating the map THEN the system SHALL provide smooth zoom transitions from tactical (flat-feeling) to strategic (globe-visible) views with orientation tools including compass directions, coordinate systems, and pentagon grid overlays

**User Story:** As a player, I want to play on innovative geodesic sphere maps that eliminate corners and create true 360-degree strategic gameplay, so that I can experience unique tactical challenges not found in traditional flat RTS maps.

#### Acceptance Criteria

1. WHEN maps are generated THEN the system SHALL create geodesic polyhedron surfaces composed primarily of hexagonal tiles with pentagons interspersed at regular intervals
2. WHEN placing spawn points THEN the system SHALL use pentagon tiles as faction starting locations to ensure geometric fairness and strategic landmarks
3. WHEN selecting map types THEN the system SHALL support Full Sphere maps (complete globe for macro games), Ring Maps (band around the globe for medium games), and Globe Fragment maps (up to two-thirds of sphere with irregular shapes for fast 1v1 games)
4. WHEN playing on sphere maps THEN the system SHALL eliminate corner camping and edge advantages while creating true encirclement and 360-degree threat scenarios
5. WHEN navigating the map THEN the system SHALL provide smooth zoom transitions from tactical (flat-feeling) to strategic (globe-visible) views with orientation tools including compass directions, coordinate systems, and pentagon grid overlays

### Requirement 13: Map Editor and User-Generated Content

**User Story:** As a player and content creator, I want to create custom maps and scenarios using an integrated map editor, so that I can design unique gameplay experiences and share them with the community.

#### Acceptance Criteria

1. WHEN accessing the map editor THEN the system SHALL provide tools to create geodesic polyhedron maps with customizable resolution and size
2. WHEN designing maps THEN the system SHALL allow placement of resource nodes, terrain features, underground layers, and faction spawn points at pentagon locations
3. WHEN creating scenarios THEN the system SHALL support custom victory conditions, starting resources, pre-placed units, and scripted events
4. WHEN publishing maps THEN the system SHALL provide a sharing system for community-created content with rating and search functionality
5. WHEN loading custom maps THEN the system SHALL validate map balance and ensure compatibility with all faction mechanics

### Requirement 14: Replay System with Event Streaming

**User Story:** As a player, spectator, and content creator, I want a comprehensive replay system that records game events and supports advanced viewing features, so that I can analyze matches, create content, and learn from gameplay.

#### Acceptance Criteria

1. WHEN matches are played THEN the system SHALL record all game events as a lightweight event stream rather than video data
2. WHEN viewing replays THEN the system SHALL support multiple camera modes: Cinematic (smooth transitions), Esports (auto-focus on battles with instant replays), and Manual (full camera control)
3. WHEN in spectator mode THEN the system SHALL provide drawing tools to annotate the map with persistent overlays anchored to 3D coordinates
4. WHEN creating annotated replays THEN the system SHALL save annotations as additional events that can be merged with the original replay
5. WHEN branching from replays THEN the system SHALL allow players to take control at any point and play from that state while preserving relevant annotations

### Requirement 15: Subway Station System for Map Control

**User Story:** As a player, I want to capture and control ancient subway stations that provide mobility and faction-specific bonuses, so that I can gain strategic advantages and create dynamic frontlines across the map.

#### Acceptance Criteria

1. WHEN maps are generated THEN the system SHALL place subway stations at strategic locations with randomized pairings that are hidden until discovered
2. WHEN capturing stations THEN the system SHALL require units to stand in the capture zone while a visible progress indicator (water tank) fills with the player's color
3. WHEN stations are captured THEN the system SHALL provide instant teleportation between connected stations and faction-specific bonuses (Survivors=polymer income, Fists=pipeline extension, Technomancers=power grid, Dwellers=tunnel network, Warmachine=rail integration)
4. WHEN stations are destroyed THEN the system SHALL create a temporary breach window where any faction can use the connection before it collapses
5. WHEN viewing as spectator THEN the system SHALL show all subway connections while players only discover them by scouting or sending units through

### Requirement 16: Tutorial and Onboarding System

**User Story:** As a new player, I want faction-specific tutorials that teach core mechanics and signature abilities, so that I can quickly understand how to play my chosen faction effectively.

#### Acceptance Criteria

1. WHEN starting the game THEN the system SHALL provide a general tutorial covering basic RTS mechanics and the five-resource economy
2. WHEN selecting a faction THEN the system SHALL offer a faction-specific tutorial (2-5 minutes) demonstrating signature mechanics
3. WHEN learning Scrapyard Survivors THEN the system SHALL teach the scavenge loop and mobile hive mechanics
4. WHEN learning other factions THEN the system SHALL provide guided sequences for their unique mechanics (wall expansion, drone control, zone placement, rail networks)
5. WHEN completing tutorials THEN the system SHALL unlock practice scenarios and AI skirmish modes for further learning