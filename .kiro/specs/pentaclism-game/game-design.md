# Game Design Document

## Overview

This document defines the specific gameplay content, mechanics, and balance parameters for Pentaclism. While the technical design document covers how systems are implemented, this document covers what those systems contain and how they behave from a player's perspective.

## Faction Design

### Scrapyard Survivors (Tetrahedron - 4 Faces)
**Identity**: Chaotic scavengers, ultra-fast rush, high visual flair
**Difficulty**: 1/5 (Very Easy)
**Tempo**: Rush/Early Game
**Resource Specialization**: Metal extraction and scavenging

#### Signature Mechanics
- **Scavenging Economy**: Units can harvest 10-20 resources from wrecks (scales with upgrades)
- **Undercurrent Mode**: When all buildings destroyed, enter mobile spawn for 3 minutes
- **Full Resource Refund**: Get 100% resources back when destroying own buildings
- **Surface Stacking**: Build infrastructure above ground instead of underground bunkers
- **Combat Unit Construction**: Combat units can build Tier 1 buildings slowly

#### Tech Tier 1 Buildings (Surface/Shallow)
- **Scrap Citadel** (HQ): 200 Metal, 60s build time, 1500 HP
- **Scrap Foundry**: 100 Metal, 25s, converts wrecks to resources
- **Patchwork Barracks**: 100 Metal + 20 Fuel, 25s, trains infantry
- **Jury-Rigged Workshop**: 120 Metal + 30 Fuel, 30s, produces vehicles
- **Signal Tower**: 80 Metal + 20 Fuel, 20s, +15% speed/attack aura

#### Tech Tier 2 Buildings (Shallow Underground)
- **Mobile Depot**: 150 Metal + 40 Fuel, 35s, can pack up and move
- **Scrap Refinery**: 180 Metal + 60 Fuel, 45s, improves scavenging efficiency
- **Explosive Workshop**: 200 Metal + 80 Fuel, 50s, produces mines and bombs

#### Tech Tier 3+ Buildings (Mid/Deep Underground)
- **Colossus Assembly**: 400 Metal + 150 Fuel + 100 Polymers, 90s, builds super-units
- **Chaos Generator**: 300 Metal + 200 Fuel + 80 Polymers, 75s, faction superweapon

#### Tech Tier 1 Units (Early Game)
- **Scavenger Raiders**: 40 Metal + 10 Food, 12s, 80 HP, can loot corpses
- **Scrap Bikes**: 60 Metal + 20 Fuel + 10 Food, 18s, 120 HP, fastest unit in game

#### Tech Tier 2 Units (Mid Game)
- **Patchwork Tank**: 120 Metal + 40 Fuel + 20 Food, 30s, 300 HP, randomized weapons
- **Scrap Flyers**: 180 Metal + 60 Fuel + 30 Food, 45s, 200 HP, unstable air units

#### Tech Tier 3+ Units (Late Game)
- **Colossus Rig**: 400 Metal + 100 Fuel + 50 Food, 120s, 1200 HP, can eat wrecks to heal
- **Scrap Titan**: 600 Metal + 200 Fuel + 100 Food, 180s, 1800 HP, stitched together from wrecks
- **Suicide Bombers**: 80 Metal + 40 Fuel + 20 Food, 25s, 150 HP, infantry with volatile packs
- **Rigged Artillery**: 300 Metal + 120 Fuel + 60 Food, 90s, 400 HP, long-range but unstable

#### Strategic Paths
- **Swarm Path**: Spam cheap Raiders, Bikes, and Patchwork Tanks for harassment and snowballing
- **Rig Path**: Invest in Colossus Rigs and Scrap Titans for risky late-game power
- **Mad Science Path**: Unlock weird upgrades like flamethrowers, acid sprayers, EMP bombs, Suicide Bombers

### Celestial Fists (Cube - 6 Faces)
**Identity**: Disciplined fortress-builders, early-mid timing pushes
**Difficulty**: 2/5 (Easy-Medium)
**Tempo**: Defensive/Early-Mid Game
**Resource Specialization**: Fuel extraction

#### Signature Mechanics
- **Wall-Based Expansion**: Can only build within wall network, walls expand build radius
- **Squad System**: Infantry trained in squads of 4-6, act as single unit, retain XP if 1+ survives
- **Morale & Command Auras**: Units gain bonuses near Command Citadel or commanders
- **Call to Arms**: Convert workers to militia for 60s (3min cooldown), slows economy

#### Tech Tier 1 Buildings (Surface/Shallow)
- **Command Citadel** (HQ): 250 Metal + 50 Fuel, 75s, 2000 HP, global morale boost
- **Barracks of Discipline**: 120 Metal + 30 Fuel, 30s, trains squads, can reinforce
- **Fortified Wall Segment**: 20 Metal, 5s, 200 HP, expands build radius
- **Defense Tower**: 100 Metal + 30 Fuel, 25s, 400 HP, ranged defense

#### Tech Tier 2 Buildings (Shallow Underground)
- **Hall of Heroes**: 200 Metal + 80 Fuel, 60s, unlocks elite units and buffs
- **Fortress Gate**: 150 Metal + 40 Fuel, 40s, fortified entrance with garrison
- **Pipeline Hub**: 180 Metal + 60 Fuel, 45s, distributes fuel through wall network

#### Tech Tier 3+ Buildings (Mid/Deep Underground)
- **Order Sanctum**: 400 Metal + 200 Fuel + 150 Polymers, 100s, ultimate command center
- **Fortress Arsenal**: 350 Metal + 180 Fuel + 120 Polymers, 85s, advanced weapon systems

#### Tech Tier 1 Units (Early Game)
- **Disciplined Infantry Squad**: 80 Metal + 20 Food, 20s, 4-6 soldiers, morale bonuses
- **Shieldbearers**: 60 Metal + 20 Fuel + 20 Food, 22s, deployable energy shields

#### Tech Tier 2 Units (Mid Game)
- **Siege Ballistae**: 100 Metal + 40 Fuel + 20 Food, 30s, long-range artillery
- **Elite Guard Squad**: 150 Metal + 40 Fuel + 30 Food, 35s, veteran infantry with special abilities
- **Sprint Infantry**: 120 Metal + 30 Fuel + 25 Food, 28s, can dash through fire

#### Tech Tier 3+ Units (Late Game)
- **Avatar of Order**: 500 Metal + 150 Fuel + 100 Food, 180s, massive exo-suit with aura
- **Champion Squads**: 200 Metal + 80 Fuel + 60 Food, 60s, fewer soldiers but each is elite
- **Guardian Towers**: 180 Metal + 60 Fuel + 40 Food, 45s, infantry that can garrison into walls

#### Strategic Paths
- **Shield Doctrine**: Shieldbearer Squads and Guardian Towers for holding ground and fortress pushes
- **Assault Doctrine**: Sprint Infantry and mobile Siege Ballistae for timing pushes and breaching
- **Heroic Doctrine**: Champion Squads and Avatar of Order for elite army with strong morale synergy

### Technomancers (Octahedron - 8 Faces)
**Identity**: Energy grids, drones, pilots, automation
**Difficulty**: 3/5 (Medium)
**Tempo**: Tech-timing/Flexible
**Resource Specialization**: Electricity generation and management

#### Signature Mechanics
- **Pilot-Drone System**: Pilots control drones via Remote Control Centers (RCCs)
- **Drone Reserves**: Can stockpile drones for instant replacement when destroyed
- **Energy Grid**: Wireless power distribution via pylons, batteries store electricity
- **Phase Gates**: Instant movement between surface and underground layers

#### Tech Tier 1 Buildings (Surface/Shallow)
- **Crystal Citadel** (HQ): 300 Metal + 100 Fuel, 90s, 1800 HP, includes 4 RCC slots
- **Energy Nexus**: 150 Metal + 60 Fuel, 45s, powers nearby structures, creates shield grids
- **Drone Foundry**: 120 Metal + 30 Fuel, 30s, produces and stockpiles drones
- **Remote Control Center**: 100 Metal + 40 Fuel, 25s, expands pilot capacity

#### Tech Tier 2 Buildings (Shallow Underground)
- **Phase Gate**: 200 Metal + 100 Fuel, 60s, instant surface-underground movement
- **Energy Battery**: 180 Metal + 80 Fuel, 50s, stores electricity, can overcharge
- **Research Pyramid**: 250 Metal + 120 Fuel, 70s, advanced technology research

#### Tech Tier 3+ Buildings (Mid/Deep Underground)
- **Quantum Lab**: 500 Metal + 300 Fuel + 200 Polymers, 120s, experimental technology
- **Obelisk Forge**: 450 Metal + 250 Fuel + 180 Polymers, 100s, constructs super-units

#### Tech Tier 1 Units (Early Game)
- **Drone Swarms**: 50 Metal + 10 Fuel + 10 Food, 15s, controlled in groups by 1 pilot
- **Energy Trooper Drones**: 80 Metal + 30 Fuel + 20 Food, 22s, shielded infantry equivalent

#### Tech Tier 2 Units (Mid Game)
- **Hover Skimmers**: 100 Metal + 40 Fuel + 20 Food, 28s, fast terrain-ignoring vehicles
- **Shield Drones**: 120 Metal + 50 Fuel + 25 Food, 30s, mobile shield generators
- **Bulwark Drone**: 150 Metal + 80 Fuel + 40 Food, 45s, slow, tanky, shield generator (1:1 pilot ratio)

#### Tech Tier 3+ Units (Late Game)
- **Obelisk Walker**: 600 Metal + 200 Fuel + 150 Food, 200s, towering beam weapon construct
- **Kamikaze Drone**: 60 Metal + 30 Fuel + 15 Food, 20s, explodes on impact, pilot ejects safely
- **Swarm Cloud**: 80 Metal + 40 Fuel + 20 Food, 25s, mass of micro-drones with chip damage

#### Strategic Paths
- **Heavy Drone Path**: Bulwark Drones and Obelisk Walkers (1:1 pilot ratio) for small elite army, strong in direct fights
- **Swarm Drone Path**: Kamikaze Drones and Swarm Clouds (1 pilot controls many) for overwhelming numbers and pressure
- **Utility/Support Path**: Shield rechargers, EMP disruptors, teleport relays for control-oriented gameplay

### Auporan Dwellers (Dodecahedron - 12 Faces)
**Identity**: Eco-tech macro faction, terraforming & attrition
**Difficulty**: 4/5 (Hard)
**Tempo**: Long-term macro/Expansion
**Resource Specialization**: Food production and biomass conversion

#### Signature Mechanics
- **Bio-Dome Zones**: Create healing/production auras, buff allies, debuff enemies
- **Tunnel Networks**: All buildings connect underground, units can move through tunnels
- **Terraforming**: Terraform Spires alter terrain, create beneficial/hazardous zones
- **Underground Burrowing**: Certain units can burrow and move underground invisibly

#### Tech Tier 1 Buildings (Surface/Shallow)
- **Living Citadel** (HQ): 350 Metal + 80 Fuel, 100s, 2200 HP, tunnel network hub
- **Bio-Domes**: 100 Metal + 20 Fuel, 25s, generate food/resources, heal nearby units
- **Hydroponics Lab**: 120 Metal + 40 Fuel, 35s, boosts resource efficiency

#### Tech Tier 2 Buildings (Shallow Underground)
- **Terraform Spire**: 180 Metal + 60 Fuel, 50s, alters terrain, creates zones
- **Research Conservatory**: 250 Metal + 100 Fuel, 80s, advanced research facility
- **Tunnel Network Hub**: 200 Metal + 80 Fuel, 60s, expands underground connections

#### Tech Tier 3+ Buildings (Mid/Deep Underground)
- **Gaia Core**: 600 Metal + 400 Fuel + 300 Polymers, 150s, planetary terraforming control
- **Evolution Chamber**: 500 Metal + 350 Fuel + 250 Polymers, 120s, advanced bio-engineering

#### Tech Tier 1 Units (Early Game)
- **Eco-Guards**: 70 Metal + 20 Food, 18s, self-healing infantry, stronger in zones
- **Spore Drones**: 60 Metal + 30 Fuel + 20 Food, 20s, flying harassment, applies debuffs

#### Tech Tier 2 Units (Mid Game)
- **Bio-Crawlers**: 120 Metal + 40 Fuel + 30 Food, 28s, regenerative vehicles
- **Burrower Drones**: 100 Metal + 50 Fuel + 25 Food, 35s, can tunnel underground
- **Ambusher Beetle**: 140 Metal + 60 Fuel + 35 Food, 40s, melee brawler, can burrow and ambush

#### Tech Tier 3+ Units (Late Game)
- **Gaia Engine**: 800 Metal + 300 Fuel + 200 Food, 240s, massive terraforming machine
- **Tunnel Wyrm**: 400 Metal + 200 Fuel + 100 Food, 120s, slow tanky siege creature, can burrow and emerge behind lines
- **Bio-Transport Leviathan**: 300 Metal + 150 Fuel + 100 Food + 50 Polymers, 90s, carries 4 squads through tunnel network
- **Bio-Assimilator**: 150 Metal + 100 Fuel + 25 Polymers, 45s, feeds on corpses to create hazard zones

#### Strategic Paths
- **Terraform Path**: Spore Drones and Terraform Spires for environmental control and area denial
- **Bio-Swarm Path**: Bio-Tanks and Gaia Engine for attrition with regenerating units
- **Espionage Path**: Burrower Drones, Ambusher Beetles, and Tunnel Wyrms for guerrilla warfare and infiltration

### Industrial Warmachine (Icosahedron - 20 Faces)
**Identity**: Steel tide on rails, ultimate siege & logistics
**Difficulty**: 5/5 (Very Hard)
**Tempo**: Late-game/Attrition
**Resource Specialization**: Polymer production and heavy industry

#### Signature Mechanics
- **Rail System**: Mobile buildings and heavy units ride on player-placed tracks
- **Train Logistics**: Resource carts and unit shuttles move at rail speed (2.5× walking)
- **Mobile Fortresses**: Key buildings can relocate along rails between mobile/fortified states
- **Buff Stacking**: Adjacent buildings provide area buffs (production speed, armor, reload)

#### Tech Tier 1 Buildings (Surface/Shallow)
- **Iron Citadel** (HQ): 400 Metal + 120 Fuel, 120s, 2500 HP, central rail hub
- **War Foundry**: 140 Metal + 40 Fuel, 35s, produces heavy vehicles, can relocate on rails
- **Rail Hub**: 120 Metal + 30 Fuel, 30s, central node, produces Resource Carts

#### Tech Tier 2 Buildings (Shallow Underground)
- **Siege Assembly Yard**: 200 Metal + 80 Fuel, 70s, builds artillery and walkers
- **Bunker Complex**: 180 Metal + 60 Fuel, 55s, fortified garrison, mobile on rails
- **Polymer Plant**: 250 Metal + 100 Fuel, 75s, converts resources to polymers

#### Tech Tier 3+ Buildings (Mid/Deep Underground)
- **Titan Foundry**: 800 Metal + 500 Fuel + 400 Polymers, 180s, constructs super-units
- **Industrial Core**: 700 Metal + 450 Fuel + 350 Polymers, 150s, ultimate production facility

#### Tech Tier 1 Units (Early Game)
- **Steel Troopers**: 100 Metal + 20 Fuel + 20 Food, 25s, elite heavy infantry
- **Resource Carts**: 80 Metal + 20 Fuel, 25s, haulers that can upgrade to defense

#### Tech Tier 2 Units (Mid Game)
- **Crawler Tanks**: 150 Metal + 60 Fuel + 30 Food, 40s, tracked high-firepower vehicles
- **Siege Walkers**: 200 Metal + 80 Fuel + 40 Food, 60s, long-range artillery mechs
- **Armored Train**: 300 Metal + 120 Fuel + 60 Food, 75s, armored transport carrying squads

#### Tech Tier 3+ Units (Late Game)
- **Titan Forge**: 1000 Metal + 400 Fuel + 300 Food, 300s, colossal war machine
- **Iron Leviathan**: 700 Metal + 400 Fuel + 200 Food + 200 Polymers, 210s, gigantic rail-bound mech with fortress mode
- **Siege Dreadnought**: 500 Metal + 300 Fuel + 100 Food + 150 Polymers, 150s, massive artillery tank with siege mode
- **Spider Carrier**: 250 Metal + 150 Fuel + 50 Food + 50 Polymers, 75s, train cart with legs, can detach from rails
- **Iron Warden**: 300 Metal + 200 Fuel + 100 Food + 100 Polymers, 90s, legendary commander with artillery strike ability

#### Strategic Paths
- **Armor Path**: Crawler Tanks and Siege Walkers for slow, unstoppable push
- **Rail Path**: Armored Trains and mobile bunkers for advancing the rail line as fortress on wheels
- **Titan Path**: Titan Forge and Iron Leviathan for late-game inevitability with polymer-heavy super-units

## Resource System

### Resource Types and Generation
- **Metal**: 10-15 per worker per minute, visible deposits, universal building material
- **Fuel**: 8-12 per worker per minute, hidden deposits revealed by surveys, powers vehicles/generators
- **Food**: 5-8 per worker per minute, produced by farms/hydroponics, consumed by living units
- **Polymers**: 3-5 per facility per minute, manufactured from Metal+Fuel, high-tech requirements
- **Electricity**: 20-30 per generator per minute, powers buildings and energy weapons

### Starting Resources
- **All Factions**: 500 Metal, 200 Food, 100 Electricity (from HQ)
- **Faction Bonuses**: +200 to specialized resource (Survivors=Metal, Fists=Fuel, etc.)

### Resource Consumption
- **Food Starvation**: Units lose 1 HP per 5 seconds when food reaches 0
- **Power Outage**: Buildings shut down when electricity reaches 0, restart when restored
- **Supply Limits**: Each faction starts with 50 supply, expanded by specific buildings

## Underground Expansion System

### Depth Structure
- **Shallow Levels (1-2)**: 0-50m depth, basic production and storage, unlocks Tech Tier 1-2
- **Mid Levels (3-4)**: 50-150m depth, advanced labs and faction-unique tech, unlocks Tech Tier 3-4
- **Deep Levels (5+)**: 150m+ depth, ultimate tech, super-units, Central Core access, unlocks Tech Tier 5+

### Construction Costs
- **Level 1 Floor**: 50 Metal + 20 Fuel, 30s build time
- **Level 2 Floor**: 75 Metal + 30 Fuel, 45s build time
- **Level 3 Floor**: 100 Metal + 50 Fuel + 25 Polymers, 60s build time
- **Level 4+ Floors**: Exponentially increasing costs and build times

### Benefits per Floor
- **Production Buildings**: +1 production queue per floor
- **Research Buildings**: +1 research slot per floor
- **Defense Buildings**: +2 garrison slots, +25% HP per floor

## Victory Conditions

### Destruction Victory
- **Condition**: Eliminate all enemy HQs and mobile spawns
- **Survivors Exception**: Undercurrent Mode provides 3-minute grace period

### Core Victory
- **Condition**: Capture and hold Central Underground Core for 5 uninterrupted minutes
- **Core Location**: Always at deepest accessible point (Level 5+ depth)
- **Capture Mechanism**: Similar to subway stations, requires continuous unit presence

### Economic Victory
- **Condition**: Achieve 3× the resource income of all opponents for 10 consecutive minutes
- **Public Disclosure**: All players can see resource generation rates (like stock market)
- **Income Calculation**: Total resources generated per minute across all types

## Subway Station System

### Station Mechanics
- **Capture Time**: 60 seconds of uncontested unit presence
- **Progress Indicator**: Water tank fills with player's color
- **Decay Rate**: 10% progress lost per 10 seconds when uncontested
- **Destruction**: 500 HP, creates 60-second breach window when destroyed

### Faction Bonuses (per controlled station)
- **Survivors**: +5 Polymers per minute (helps with tech scaling)
- **Fists**: Can extend pipeline network through station
- **Technomancers**: Station acts as power grid node
- **Dwellers**: Station becomes tunnel network entrance
- **Warmachine**: Station integrates with rail network

### Discovery Mechanics
- **Scouting**: Stations appear on minimap when first scouted
- **Connection Reveal**: Other end only revealed when unit travels through
- **Spectator View**: Observers see all connections, players discover them

## Map Generation

### Geodesic Sphere Structure
- **Hex Tiles**: Primary surface, 6-sided for movement and building
- **Pentagon Tiles**: 12 per map, used as spawn points and strategic landmarks
- **Resolution**: Configurable density, higher resolution = more tiles

### Map Types
- **Full Sphere**: Complete globe, 4-8 players, 45-90 minute games
- **Ring Maps**: Equatorial band, 2-4 players, 20-45 minute games  
- **Globe Fragments**: Up to 2/3 sphere, irregular shapes, 1v1 optimized, 10-30 minute games

### Resource Distribution
- **Metal Deposits**: 3-5 per spawn area, visible, 2000-3000 units each
- **Fuel Deposits**: 2-3 per spawn area, hidden until surveyed, 1500-2500 units each
- **Expansion Resources**: Scattered across map, encourage territorial control
- **Central Resources**: High-value deposits near Central Core

## Camera and Navigation System

### Camera Modes
- **Manual**: Full player control, hotkeys, saved positions
- **Auto-Focus**: Automatic event following, toggleable, default ON for new players
- **Cinematic**: Smooth transitions, dynamic framing for replays
- **Esports**: Broadcast-ready with POV cuts, instant replays, picture-in-picture

### Navigation Features
- **Seamless Zoom**: Tactical (flat-feeling) to strategic (full globe visible)
- **Rotatable Minimap**: Drag to rotate main camera view
- **Alert System**: Visual indicators + hotkey cycling for important events
- **Orientation Aids**: Compass, coordinates, pentagon grid overlay, return-to-base hotkey

### Auto-Focus Behaviors
- **Event Alerts**: Unit under attack, building complete, worker idle, research finished
- **Camera Actions**: Auto-zoom for large selections, auto-pan to follow units
- **Smart Timing**: Delays between jumps, picture-in-picture for simultaneous events

## Worker System and Expansion Mechanics

### Faction Worker Designs

#### Scrapyard Survivors - Scavenger Crew
- **Single Worker Type**: Scavenger Crew (40 Metal, 10s build time)
- **Gathering**: Mines Metal/Fuel, scavenges wrecks, hauls resources
- **Construction**: Builds all buildings (fastest at Tech Tier 1, slower at higher tiers)
- **Upgrade Option**: Can become Caravan Pilot (50 Metal + 20 Fuel, 15s) - mobile depot/hauler, loses build ability
- **Unique Feature**: Combat units can build Tech Tier 1 buildings very slowly
- **Identity**: Improvised, chaotic - everyone builds, but badly

#### Celestial Fists - Dual Worker System
- **Citizen-Builder** (50 Metal, 12s): Mines Metal/Fuel, maintains pipelines, builds all buildings (best at walls/pipelines, weak at high-tech), can garrison for rifle fire
- **Engineer Squad** (80 Metal + 20 Fuel, 20s): Can mine but inefficient, builds all buildings (best at high-tech, weak at walls/pipelines), can garrison for RPG/anti-armor fire
- **Identity**: Structured, disciplined - everyone builds, but specialization matters

#### Technomancers - Automated System
- **Utility Drone** (40 Metal, 10s): Pilot-controlled, mines Metal/Fuel, can assign building sites then leave (auto-builds slowly), battery-powered with charging requirements
- **Maintenance Drone** (60 Metal, 20s): Pure support, must attend construction sites, can accelerate auto-builds, can recharge shields
- **Battery Mechanics**: Utility Drones operate off onboard batteries, must return to charging pads, can upgrade to wireless recharging and power grid feedback
- **Identity**: Automated, cerebral - semi-automated builds, battery economy, fragile if RCCs/power disrupted

#### Auporan Dwellers - Dual Specialization
- **Bio-Cultivator** (50 Metal, 12s): Produces Food in domes, tends Hydroponics, builds Tech Tier 1 buildings anywhere (slow at tunnels)
- **Burrower Drone** (60 Metal, 20s): Mines Metal/Fuel, digs tunnels, builds all buildings but only if connected to tunnel network, builds tunnels faster
- **Identity**: Subterranean, harmonious - early flexibility, late-game tunnel synergy

#### Industrial Warmachine - Rail-Dependent System
- **Track Layer** (60 Metal, 20s): Mines Metal/Fuel, builds rail segments, builds all buildings (must attend), repairs rails and mobile buildings
- **Resource Cart** (80 Metal + 20 Fuel, 25s): Hauler only, cannot build, can upgrade with static defense modules (turrets, AA guns), acts as static defense when parked on rails
- **Identity**: Industrial, inevitable - Track Layers build the empire, Carts defend and sustain it

### Expansion Strategies by Faction

#### Scrapyard Survivors - Opportunistic Outposts
- **Method**: Use Caravan Pilots for forward depots, combat units can build anywhere, cheap and fast but fragile
- **Map Control**: Harassment equals map control, constant raiding, explosive traps in contested areas
- **Identity**: Flow like raiders, temporary depots, scavenging wherever they fight

#### Celestial Fists - Fortress-Centric Expansion
- **Method**: Must wall outward to expand build radius, every expansion is a mini-fortress with walls/gates/pipelines/towers
- **Map Control**: Chokepoint control, Ballistae + Shieldbearers hold ground while walls extend, pipelines safe from harassment
- **Identity**: Creeping fortress - slow, deliberate, unbreakable once established

#### Technomancers - Grid-Based Outposts
- **Method**: Expansion tied to Energy Pylons extending wireless grid, can drop RCCs + Drone Foundries at forward pylons
- **Map Control**: Drone stockpiling for quick force projection, Hover Skimmers for mobility, forward batteries for temporary pushes
- **Identity**: Web of pylons - flexible, fast to set up, vulnerable to disruption

#### Auporan Dwellers - Tunnel Networks & Zone Anchors
- **Method**: Every building is tunnel entrance, expansions connected underground, slow to dig but automatic logistics once connected
- **Map Control**: Zone denial with Terraform Spires at chokepoints, Mini-Railgun Turrets + Eco-Guards hold zones
- **Identity**: Roots spreading underground - slow, hidden, create zones of dominance

#### Industrial Warmachine - Rail-Centric Rolling Frontline
- **Method**: Expansion tied to rail networks, Rail Hubs + Refineries allow decentralized processing, slow start but extremely efficient
- **Map Control**: Rolling fortress with mobile Foundries/Bunkers/Mortars, Resource Carts as dual-use hauler/defense, siege line advances with rails
- **Identity**: Steel tide - slow, linear, permanent territorial control once rails established

### Starting Setups by Faction

#### Scrapyard Survivors
- **Units**: 6 Scavenger Crews, 2 Scavenger Raiders
- **Buildings**: Scrap Citadel, Scrap Mine, Scrap Garden, Jury-Rigged Generator, Power Lines
- **Strategy**: Fastest rush start, fragile if harassment fails

#### Celestial Fists
- **Units**: 8 Citizen-Builders, no combat units
- **Buildings**: Command Citadel, Ore Quarry, Food Garden, Fuel Generator, Wall + Fortress Gate, Wall extension to Quarry
- **Strategy**: Slowest expansion but safest economy

#### Technomancers
- **Units**: 4 Utility Drones (piloted), 1 Maintenance Drone, 4 Pilots (in Citadel), 1 Drone Swarm
- **Buildings**: Crystal Citadel (4 RCC slots), Ore Extractor, Food Synthesizer, Fuel Generator, Energy Pylon, Energy Battery
- **Strategy**: Micro-heavy start, flexible but fragile grid

#### Auporan Dwellers
- **Units**: 4 workers (2 Bio-Cultivators, 2 Burrower Drones)
- **Buildings**: Living Citadel, Ore Harvester, 2 Hydroponics Labs, Power Generator, all connected via tunnels
- **Strategy**: Weakest start but renewable electricity and smooth mid-game logistics

#### Industrial Warmachine
- **Units**: 5 Track Layers, 3 Steel Troopers
- **Buildings**: Iron Citadel, Ore Drill, Food Factory, Fuel Generator, Rail Hub, Rail Segments, extra rail line for expansion
- **Strategy**: Strongest individual units but slowest economy, strongest late-game potential

## Balance Philosophy

### Faction Tempo Scaling
- **Face Count = Complexity**: More faces = more complex mechanics and longer optimal game time
- **Early Game Power**: Inversely related to face count (Survivors strongest early, Warmachine weakest)
- **Late Game Power**: Directly related to face count (Warmachine strongest late, Survivors weakest)
- **Skill Ceiling**: Scales with face count (Survivors easy to learn, Warmachine very difficult)

### Counter Relationships
- **Universal Counters**: EMP disables shields, fire bypasses armor, artillery outranges static defense
- **Faction Counters**: Each faction has clear weaknesses that others can exploit
- **Situational Advantages**: Map type, victory conditions, and player skill affect matchups

### Progression Systems
- **Unit Experience**: Combat XP improves stats, reduces retraining time
- **Upgrade Limits**: Max upgrades per unit = faction face count ÷ 4 (rounded up)
- **Elite Unit Caps**: Prevent snowballing, maintain strategic choices

## Air Combat System

### Air Combat Philosophy
Air units are powerful but situational - they excel at mobility, harassment, and surgical strikes, but cannot dominate through brute force. The system creates clear counterplay where expensive, slow-to-build anti-air creates "no-fly zones" that force combined-arms gameplay.

### Core Air Mechanics
- **Air Superiority**: Air units ignore terrain and have high mobility
- **AA Zones**: Static anti-air creates expensive but dominant defensive zones
- **Mobile AA**: Each faction has one specialist mobile anti-air unit with unique mechanics
- **Air Production**: Each faction has dedicated air production buildings with faction-specific mechanics

### Air Production Buildings by Faction

#### Scrapyard Survivors - Scrap Airstrip
- **Cost**: 200 Metal + 80 Fuel, 60s build time
- **Mechanics**: Crude runway, aircraft must land to repair/rearm, vulnerable when grounded
- **Special**: Can salvage crashed aircraft for 50% resource refund
- **Capacity**: 3 aircraft maximum, queue builds while airborne

#### Celestial Fists - Fortress Hangar
- **Cost**: 250 Metal + 100 Fuel, 75s build time
- **Mechanics**: Underground hangar with armored doors, aircraft protected when not deployed
- **Special**: Can garrison infantry squads for anti-air defense
- **Capacity**: 2 aircraft maximum, heavily armored structure

#### Technomancers - Drone Launch Bay
- **Cost**: 180 Metal + 120 Fuel, 50s build time
- **Mechanics**: Automated launch/recovery system, drones auto-repair when docked
- **Special**: Can overcharge for 50% faster production using stored electricity
- **Capacity**: 4 drones maximum, wireless control integration

#### Auporan Dwellers - Bio-Spire Nest
- **Cost**: 220 Metal + 90 Fuel, 65s build time
- **Mechanics**: Living structure that grows air units, self-healing building
- **Special**: Flying units regenerate health when near Bio-Spires
- **Capacity**: 3 creatures maximum, connects to tunnel network

#### Industrial Warmachine - Rail Catapult
- **Cost**: 300 Metal + 150 Fuel, 90s build time
- **Mechanics**: Rail-mounted launch system, can relocate along rail network
- **Special**: Launches aircraft at 2× normal speed, requires rail connection
- **Capacity**: 2 aircraft maximum, mobile when on rails

### Air Units by Faction

#### Scrapyard Survivors Air Units

**Scrap Flyers (Light Air)**
- **Cost**: 120 Metal + 60 Fuel + 30 Food, 45s
- **Stats**: 180 HP, medium speed, short range
- **Role**: Cheap harassment, scouting
- **Special**: Unstable - 10% chance to malfunction and crash each minute
- **Weapons**: Jury-rigged machine guns, decent vs infantry

**Bomber Kite (Medium Air)**
- **Cost**: 200 Metal + 100 Fuel + 50 Food, 75s
- **Stats**: 250 HP, slow speed, no air-to-air weapons
- **Role**: Hit-and-run bombing
- **Special**: Drops explosive payload, must return to rearm
- **Weapons**: Bomb drop, high damage vs buildings/vehicles

**Scrap Interceptor (Fighter)**
- **Cost**: 180 Metal + 80 Fuel + 40 Food, 60s
- **Stats**: 200 HP, high speed, air-to-air focused
- **Role**: Air superiority, escort
- **Special**: Ramming attack - can sacrifice self for massive damage
- **Weapons**: Scrap cannons, strong vs air units

#### Celestial Fists Air Units

**Disciplined Gunship (Medium Air)**
- **Cost**: 250 Metal + 120 Fuel + 60 Food, 90s
- **Stats**: 400 HP, medium speed, heavily armored
- **Role**: Close air support, formation flying
- **Special**: Gains accuracy bonus when near other Fists air units
- **Weapons**: Precision cannons, effective vs vehicles

**Sky Fortress (Heavy Air)**
- **Cost**: 400 Metal + 200 Fuel + 100 Food, 150s
- **Stats**: 800 HP, slow speed, massive firepower
- **Role**: Flying fortress, area control
- **Special**: Can deploy temporary shield dome for ground units
- **Weapons**: Multiple turrets, devastating vs ground targets

**Patrol Drone (Light Air)**
- **Cost**: 150 Metal + 80 Fuel + 30 Food, 50s
- **Stats**: 220 HP, medium speed, long patrol range
- **Role**: Reconnaissance, early warning
- **Special**: Provides vision in large radius, alerts to enemy movement
- **Weapons**: Light cannons, primarily defensive

#### Technomancers Air Units

**Energy Fighter (Light Air)**
- **Cost**: 160 Metal + 100 Fuel + 40 Food, 55s
- **Stats**: 200 HP, high speed, energy shields
- **Role**: Air superiority, shield support
- **Special**: Can transfer shield energy to nearby units
- **Weapons**: Energy beams, bonus damage vs shields

**Stealth Bomber (Heavy Air - T3)**
- **Cost**: 500 Metal + 300 Fuel + 150 Food + 100 Polymers, 180s
- **Stats**: 300 HP, medium speed, cloaked
- **Role**: Strategic bombing, AA bypass
- **Special**: Invisible to most detection, can bypass AA zones
- **Weapons**: Precision energy bombs, ignores armor

**Support Drone (Utility Air)**
- **Cost**: 120 Metal + 80 Fuel + 20 Food, 40s
- **Stats**: 150 HP, medium speed, no weapons
- **Role**: Battlefield support, logistics
- **Special**: Can repair other air units, recharge shields
- **Weapons**: None, pure support role

#### Auporan Dwellers Air Units

**Spore Drone (Light Air)**
- **Cost**: 100 Metal + 60 Fuel + 40 Food, 50s
- **Stats**: 160 HP, medium speed, organic
- **Role**: Harassment, area denial
- **Special**: Creates temporary toxic clouds on death
- **Weapons**: Spore launcher, applies slow/poison debuffs

**Bio-Flyer (Medium Air)**
- **Cost**: 220 Metal + 120 Fuel + 80 Food, 85s
- **Stats**: 320 HP, medium speed, regenerating
- **Role**: Sustained combat, attrition
- **Special**: Slowly regenerates HP, stronger in bio-zones
- **Weapons**: Acid sprayers, damage over time effects

**Plague Carrier (Heavy Air)**
- **Cost**: 350 Metal + 180 Fuel + 120 Food, 120s
- **Stats**: 450 HP, slow speed, area effect
- **Role**: Zone creation, biological warfare
- **Special**: Creates permanent hazard zones where it dies
- **Weapons**: Plague bombs, creates toxic areas

#### Industrial Warmachine Air Units

**Steel Interceptor (Fighter)**
- **Cost**: 280 Metal + 150 Fuel + 70 Food, 100s
- **Stats**: 350 HP, high speed, heavily armored
- **Role**: Air superiority, escort
- **Special**: Can ram other aircraft for mutual destruction
- **Weapons**: Rail cannons, high single-target damage

**Iron Bomber (Heavy Air)**
- **Cost**: 450 Metal + 250 Fuel + 120 Food, 160s
- **Stats**: 600 HP, slow speed, massive payload
- **Role**: Strategic bombing, siege support
- **Special**: Carpet bombing run, affects large area
- **Weapons**: Heavy bombs, devastating vs structures

**Cargo Lifter (Transport Air)**
- **Cost**: 200 Metal + 120 Fuel + 50 Food, 80s
- **Stats**: 400 HP, medium speed, no weapons
- **Role**: Troop transport, logistics
- **Special**: Can carry 2 squads, deploys via rappelling
- **Weapons**: None, pure transport role

### Anti-Air Systems

#### Static Anti-Air Buildings

**Scrapyard Survivors - Scrap Flak Tower**
- **Cost**: 150 Metal + 80 Fuel, 50s
- **Stats**: 300 HP, long range, area damage
- **Special**: Cheap but slow reload, can be overcharged with extra fuel
- **Effectiveness**: Good vs swarms, weak vs heavy armor

**Celestial Fists - Fortress AA Battery**
- **Cost**: 200 Metal + 120 Fuel, 70s
- **Stats**: 500 HP, very long range, high accuracy
- **Special**: Synergizes with walls, can be garrisoned for extra firepower
- **Effectiveness**: Excellent vs single targets, limited vs swarms

**Technomancers - Energy AA Node**
- **Cost**: 180 Metal + 150 Fuel, 60s
- **Stats**: 250 HP, medium range, energy shields
- **Special**: Can overcharge for burst damage, requires power grid
- **Effectiveness**: Versatile, can adapt damage type

**Auporan Dwellers - Spore Launcher**
- **Cost**: 160 Metal + 100 Fuel, 55s
- **Stats**: 280 HP, medium range, DoT effects
- **Special**: Creates toxic clouds, damages over time
- **Effectiveness**: Area denial, weakens rather than destroys

**Industrial Warmachine - Heavy Flak Battery**
- **Cost**: 250 Metal + 180 Fuel, 90s
- **Stats**: 600 HP, long range, devastating damage
- **Special**: Slow but extremely powerful, can be rail-mounted
- **Effectiveness**: Destroys anything it hits, very slow fire rate

#### Mobile Anti-Air Units

**Scrapyard Survivors - Shrapnel Cannon**
- **Cost**: 140 Metal + 70 Fuel + 35 Food, 55s
- **Stats**: 120 HP, medium speed, area damage
- **Style**: Glass cannon - cheap, effective, extremely fragile
- **Special**: Decent AoE damage, dies to almost any return fire
- **Tactics**: Swarm them, protect them, or accept losses

**Celestial Fists - Giant Ballista**
- **Cost**: 200 Metal + 100 Fuel + 50 Food, 80s
- **Stats**: 300 HP, slow speed, very high single-target damage
- **Style**: Precision weapon - disciplined, long-range
- **Special**: Can one-shot most air units, very slow reload
- **Tactics**: Position carefully, protect from rushes

**Technomancers - Siege Laser Tank**
- **Cost**: 250 Metal + 150 Fuel + 60 Food, 90s
- **Stats**: 350 HP, mode-switching (mobile/siege)
- **Style**: High-tech transformer - requires positioning
- **Special**: Must siege to shoot air, powerful laser when deployed
- **Tactics**: Anticipate air attacks, vulnerable while repositioning

**Auporan Dwellers - Rail Shotgun Tank**
- **Cost**: 220 Metal + 120 Fuel + 70 Food, 85s
- **Stats**: 280 HP, slow speed, cone attack
- **Style**: Organic brutality - devastating burst, long reload
- **Special**: Cone attack hits multiple air units, very slow fire rate
- **Tactics**: Ambush positioning, zone denial

**Industrial Warmachine - Rail Cart Mortar**
- **Cost**: 300 Metal + 180 Fuel + 80 Food, 110s
- **Stats**: 400 HP, rail-bound movement, area damage
- **Style**: Industrial artillery - devastating but predictable
- **Special**: Massive AoE damage, can only move on rails
- **Tactics**: Defend rail networks, create no-fly corridors

### Air Combat Balance

#### Air Unit Vulnerabilities
- **Light Air**: Vulnerable to fighters and mobile AA, good vs ground
- **Heavy Air**: Vulnerable to static AA and focused fire, devastating when protected
- **Fighters**: Strong vs other air, weak vs ground-based AA
- **Bombers**: High ground damage, defenseless vs fighters

#### Counter-Play Mechanics
- **AA Investment**: Expensive but creates safe zones
- **Air Raids**: Effective vs undefended areas
- **Combined Arms**: Ground forces must clear AA for air dominance
- **Economic Trade-offs**: AA investment slows economy/army growth

#### Faction Air Identities
- **Survivors**: Chaotic, unreliable, but cheap and numerous
- **Fists**: Disciplined, formation-flying, heavily armored
- **Technomancers**: High-tech, energy-based, stealth capabilities
- **Dwellers**: Organic, regenerating, area denial focused
- **Warmachine**: Industrial, heavily armored, devastating firepower

This air combat system ensures that air power remains strategically important while preventing air-only dominance through expensive but effective counter-measures and faction-specific asymmetric design.

## Terrain Manipulation System

### Terrain Manipulation Philosophy
Terrain manipulation is a slow, costly, macro-strategic decision that allows factions to reshape the battlefield over time. Each faction can interact with terrain features in ways that reinforce their identity, creating dynamic maps that evolve differently each match.

### Core Mechanics
- **Slow and Costly**: Terrain manipulation requires significant time and resource investment
- **Permanent Progress**: Any progress made leaves permanent visual changes on the map
- **Faction-Specific Methods**: Each faction has unique approaches to terrain manipulation
- **Strategic Weight**: Terrain projects are macro-level decisions that reshape the game

### Terrain Types and Manipulation

#### Mountains (Impassable Terrain)
Mountains block movement and create natural chokepoints that can be overcome through faction-specific methods.

**Scrapyard Survivors - Cableway System**
- **Method**: Jury-rigged cable cars and zip lines over mountain peaks
- **Cost**: 300 Metal + 150 Fuel, 180s construction time
- **Durability**: Fragile (200 HP), easily destroyed but quick to rebuild
- **Special**: Only Survivors can use cableways, provides escape routes
- **Progress**: Visible cable towers and lines appear as construction progresses

**Celestial Fists - Great Wall Pass**
- **Method**: Fortified tunnel through mountain with defensive walls
- **Cost**: 400 Metal + 200 Fuel, 240s construction time
- **Durability**: Sturdy (600 HP), can integrate with wall networks
- **Special**: Any faction can use, but Fists can extend pipelines through it
- **Progress**: Stone archway and fortified entrance visible during construction

**Technomancers - Monorail Pass**
- **Method**: High-tech elevated rail system over mountain
- **Cost**: 500 Metal + 300 Fuel + 100 Polymers, 300s construction time
- **Durability**: Balanced (800 HP), requires power grid connection
- **Special**: Any faction can use, but Technomancers can link power grids through it
- **Progress**: Sleek support pillars and rail segments appear during construction

**Auporan Dwellers - Bio-Tunnel**
- **Method**: Living tunnel grown through mountain using bio-engineering
- **Cost**: 350 Metal + 250 Fuel + 150 Food, 360s construction time
- **Durability**: Very tough (1200 HP), self-healing structure
- **Special**: Any faction can use, but connects to Dwellers' tunnel network
- **Progress**: Organic entrance and bioluminescent markers visible during growth

**Industrial Warmachine - Blasted Canyon**
- **Method**: Industrial explosives create permanent canyon through mountain
- **Cost**: 600 Metal + 400 Fuel + 200 Polymers, 420s construction time
- **Durability**: Indestructible terrain change, rails can be laid through
- **Special**: Permanent map alteration, any faction can use
- **Progress**: Blast holes and rubble piles appear, canyon widens over time

#### Water Bodies (Impassable Terrain)
Lakes and swamps block movement and building, but can be converted to buildable land through universal methods.

**Universal Water Manipulation** (Any faction can continue another's progress)
- **Scrapyard Survivors - Landfill**: Dump scrap metal and debris, 250 Metal + 100 Fuel, 150s
- **Celestial Fists - Ashfill**: Use industrial ash and concrete, 300 Metal + 150 Fuel, 180s
- **Technomancers - Forced Evaporation**: Energy-based water removal, 200 Metal + 200 Fuel, 120s
- **Auporan Dwellers - Bio-Overgrowth**: GMO plants absorb and process water, 150 Metal + 100 Fuel + 100 Food, 200s
- **Industrial Warmachine - Industrial Pumping**: Mechanical water removal, 350 Metal + 200 Fuel, 160s

#### Hazard Zones (Damage Over Time Areas)
Craters, lava vents, and toxic areas can be neutralized or exploited by different factions.

**Crater/Lava Vent Manipulation**
- **Survivors**: Scavenge for fuel (creates resource trickle, doesn't remove hazard)
- **Fists**: Cap with industrial plating (removes hazard, creates safe crossing)
- **Technomancers**: Harness as power nodes (removes hazard, provides electricity)
- **Dwellers**: Seed with extremophile organisms (converts to healing zone)
- **Warmachine**: Industrial capping (removes hazard, provides build space)

**Toxic Swamp Manipulation**
- **Survivors**: Jury-rig polymer extraction (creates resource trickle)
- **Fists**: Drain and fortify (removes hazard, creates defensive position)
- **Technomancers**: Energy purification (removes hazard, creates power node)
- **Dwellers**: Bio-remediation (converts to fertile growing zone)
- **Warmachine**: Industrial processing (removes hazard, provides polymer income)

### Durability Scaling by Faction
Terrain project durability scales with faction complexity (Platonic solid face count), reflecting their tempo and permanence philosophy:

- **Survivors (4 faces)**: Fragile projects (200-400 HP), quick to build, easy to destroy
- **Fists (6 faces)**: Sturdy projects (600-800 HP), reliable but destructible
- **Technomancers (8 faces)**: Balanced projects (800-1000 HP), moderate durability
- **Dwellers (12 faces)**: Tough projects (1200-1500 HP), very hard to destroy
- **Warmachine (20 faces)**: Permanent projects (indestructible terrain changes)

### Construction Mechanics
- **Progress Tracking**: Visual progress bars and physical changes appear during construction
- **Interruption**: Destroying workers halts progress but doesn't reset it
- **Faction Continuity**: Only same faction can continue mountain pass projects
- **Universal Projects**: Any faction can continue water manipulation projects
- **Resource Investment**: All projects require significant upfront resource commitment

### Strategic Implications

#### Early Game Impact
- Terrain manipulation too expensive for early game
- Focus on standard expansion and military buildup
- Scouting reveals terrain features for future planning

#### Mid Game Opportunities
- First terrain projects become economically viable
- Water manipulation opens new expansion sites
- Mountain passes can break stalemates and create new fronts

#### Late Game Transformation
- Multiple terrain projects reshape the entire map
- Faction-specific infrastructure networks emerge
- Superweapons can instantly complete terrain projects for dramatic moments

#### Superweapon Terrain Manipulation
Late-game superweapons can bypass normal terrain manipulation rules:
- **Survivors**: Colossus Rig instantly rips open terrain for scavenging
- **Fists**: Citadel Drop creates instant fortified position
- **Technomancers**: Planetary Beam instantly vaporizes water bodies
- **Dwellers**: Gaia Engine instantly grows forests or bio-zones
- **Warmachine**: Orbital Rail Cannon instantly blasts mountain passes

### Spectator and Competitive Features
- **Progress Visualization**: Clear progress bars and visual changes for viewers
- **Faction Identity**: Each manipulation method reinforces faction themes
- **Strategic Drama**: Long-term projects create tension and anticipation
- **Map Evolution**: Every match creates unique terrain layouts
- **Caster Moments**: Big terrain completions provide highlight moments

This terrain manipulation system ensures that the battlefield becomes a dynamic, evolving space where faction identity is literally carved into the landscape, creating unique strategic opportunities and memorable moments in every match.

This game design document provides the specific content and balance parameters that populate the technical systems outlined in the main design document.