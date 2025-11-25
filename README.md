# ClaySoldiers-Portfolio

**Clay Soldiers (2023)**

*Large Strategy / Skirmish Game • Released Free on Steam (June 2024)*

Steam Page

Availability: Free (no key required)

**⭐ Project Overview**

Clay Soldiers is a lightweight 3D strategy game inspired by large-scale titles such as Civilization, reimagined as fast-paced skirmishes with unique faction mechanics and resource systems. Development began as a full war-scale 4X game with deep resource chains, tech-tree progression, and large battles—but halfway through, the design pivoted toward shorter, replayable skirmishes inspired by a card game I developed for friends.

Players choose between three asymmetric factions—Mercenaries, Undead, and Angels—each with unique units, synergies, currencies, and playstyles. Clay Soldiers includes single-player skirmishes, campaign progression with encrypted saves, Steam achievements, and peer-to-peer multiplayer using Unity’s Netcode for GameObjects.

This was my first major project where all 3D art and animation were created in Blender by myself, marking the beginning of my asset-creation pipeline.

**🎮 Gameplay Summary**

Clay Soldiers combines lightweight real-time tactical gameplay with strategic resource management.

*Game Modes*

Campaign Mode
Progress through increasingly difficult AI opponents, unlocking new units and capturing land. Save data is fully encrypted.

Skirmish Mode
Quick matches against AI or online opponents with full faction choice and army composition.

Online Multiplayer (P2P)
Built using Unity Multiplayer (NGO), Relay, and Lobbies. Supports multiple players and AI opponents simultaneously.

**Factions & Currencies**

*Mercenaries (Gold)*

Earn gold over time

Optional passive bonuses

Gain additional gold by killing enemies

Balanced, flexible unit roster

*Undead (Corpses)*

Gain corpses from enemy deaths

Optional resurrection bonuses

Slow passive corpse generation

Swarm-based playstyle

*Angels (Faith)*

Gain faith by keeping follower units alive

Lose faith when followers die

Rewarded for protective play

Focused, elite unit roster

**Match Flow**

Choose faction

Build your army from unlocked units (DLC gated optional)

Place your castle on the tile grid

Spawn units using your faction’s currency

Fight enemies and destroy their castles to win

Campaign progression carries earned units forward so players build stronger armies over time.

**🧩 Key Features**

P2P Online Multiplayer using Unity Netcode for GameObjects

Steam achievements and campaign save encryption

Three asymmetric factions with unique currencies

3D models and animations fully created in Blender

Highly optimized for low-end hardware

Island generation system for "war mode"

Dynamic AI with point-based decision logic

Cinematic animated start screen

Serverless matchmaking with skill-based search

Skirmish, campaign, and online battle modes

Tile-based maps with hazards and biome variety

**🏗️ Architecture Overview**

Clay Soldiers reflects a significant leap in my architectural discipline compared to earlier projects. Key architectural features include:

Event-driven sequencing using coroutines for smooth, ordered gameplay flow

Nearly all gameplay logic is offloaded from Update to reduce overhead

AI built using a decision-based point-value evaluation system

Modular systems for spawning, currency handling, AI actions, and player input

Network logic split into server-authoritative systems and client-side prediction where needed

Extensive use of ScriptableObjects to define units, stats, factions, hazards, and map tiles

Clear pipeline for unit animations created in Blender using lightweight rigging

Although the AI could behave strangely at times, the architecture included safeguards:

Failsafe state resets

Timeout-based loop breakers

AI stalling detection

This ensured that even imperfect decision-making never led to frozen matches.

**🗂️ Key Scripts to Review**
*Core*

GameController – global game flow, turn pacing, and event sequencing

NetworkController (NGO) – handles P2P connections, relay, and lobby logic

CampaignController – encrypted progression saves, faction unlocks

*Systems*

FactionCurrencySystem – handles gold/corpses/faith income and modifiers

UnitSpawnSystem – spawns units based on faction, tile, and currency

TileMapSystem – grid/tile management, hazards, and castle placement

CombatResolutionSystem – direct combat rules, damage, and unit interactions

AIActionSystem – executes all AI decisions per turn

*AI*

AIStateDecisionSystem – point-based aggression, defense, and purchase logic

AITurnOrderController – determines which AI unit acts next

AIStructureBuilder – decides what buildings or bonuses to construct

IslandGenerationAI (War Mode) – optional system for older war prototype

*Managers*

UnitManager – registers all units, handles deaths/spawns

FactionManager – stores faction unlock data and campaign rewards

OnlineMatchManager – host settings, AI count, and game mode

*UI*

StartMenuController – cinematic start screen interactions

LobbyUIController – multiplayer selection and AI slot management

UnitSelectionUI – army building interface

ResourceUI – displays currency in real time

*Utilities*

CoroutineSequencer

SaveEncryptionUtility

MatchmakingHelper

**🧪 Development Notes**
*Performance & Optimization*

This project marked the beginning of your consistent focus on high performance:

Minimal Update usage

All gameplay driven by ordered coroutines

Optimized 3D models with low poly counts

Lightweight Blender animations

Networking messages kept extremely small

AI loops capped with timeouts

Game consistently runs on very low-spec machines

*Networking*

Clay Soldiers uses:

Unity Netcode for GameObjects

Unity Relay

Unity Lobby

Custom P2P session management

Skill-based matchmaking (rank proximity searching)

*AI*

The AI consisted of a multi-stage decision process:

Evaluate game state (economy, units, positioning)

Assign weights/points to possible actions

Pick the highest-value action

Execute actions in order per unit

If no valid action → fallback to failsafe

AI is imperfect, but robust enough to avoid softlocks.

**🚧 Why This Project Matters**

Clay Soldiers represents several milestones:

My first project with fully custom 3D art & animation

My first large-scale use of Unity Netcode

My first release with Steam achievements and encrypted saves

A major step forward in architecture, optimization, and pipelines

Demonstrates my growth into managing large, multi-system games

Shows my ability to integrate networking, AI, Blender assets, and UI cohesively

Most importantly, it shows my evolution into a developer capable of building complete vertical slices: art, engineering, networking, UI, design, and audio.

**📚 Lessons Learned**

Importance of good naming conventions and architectural consistency

How to develop clean Blender-to-Unity asset workflows

How to build network-safe gameplay systems

How to design asymmetrical factions without breaking balance

Sequencing game events using coroutines instead of Update

Early experience with campaign save encryption

Improved AI behavior trees through point-based evaluation

**🛠️ Tech Stack**

Unity 2021.x / 2022.x

C#

Unity Netcode for GameObjects

Unity Relay & Lobby

Steamworks.NET

Blender (models & animations)

ScriptableObject-based data architecture
