# The Chronomancer's Echo

## Project Overview
This project is a 2D, story-driven puzzle game leveraging the Visual Novel format and Resident Evil-style environmental puzzles. 
The core mechanic is a 15-minute Time Loop, which forces the player to apply knowledge gained in previous loops to achieve permanent progress, ensuring a high density of player-environment interaction within a limited scope.
- Genre: 2D Narrative Puzzle / Time-Loop Detective
- Setting: The inherited office of the vanished chronomancer, Professor Eldrich, at a magical academy.
- Goal: Successfully execute a sequence of actions within a single loop to retrieve or destroy a dangerous artifact before the time reset.

## Final Project Requirements Checklist
| **Requirement** | **Implementation in _The Chronomancer's Echo_** | **Complexity / Feature Showcased** |
|------------------|-----------------------------------------------|------------------------------------|
| **Locomotion** | 2D character movement (walk/idle) within the single-scene office environment. | Basic Player Controller for movement and interaction raycasting. |
| **Sound Effects** | SFX for item pickups, UI clicks, successful puzzle solves, and environmental cues (e.g., the coffee maker sputtering, the clock ticking). | Diverse SFX usage to provide feedback on interaction. |
| **Music** | Dynamic, looping music with a low Chronometric Pulse. Music volume/pitch adjusts based on time remaining in the current loop (using the Audio Mixer). | Dynamic Audio Management driven by C# script. |
| **Artwork** | High-detail static 2D background art for the office. Sprite sheet for the main character (walk cycle, idle). Animated sprites for key interactable objects (e.g., the Pendulum Clock). | Consistent aesthetic and multi-layered 2D assets. |
| **Animation** | Animated States for the player (walk/idle). Tightly timed animations for the Vanishing Clue Ghost and object reactions (e.g., a lever moving, a book opening). | Use of Unity's Animator Controller with multiple state transitions and triggers. |
| **Narrative / Theme / Story** | Deep lore centered on Professor Eldrich's obsession with Achronicity. Progress is locked behind Dialogue Trees and successful Clue Synthesis. | Primary focus of the project; uses a structured Dialogue System. |
| **UI / Menus** | Start/Pause Menu, Health/Timer UI, and the complex Temporal Index (Clue Log) for clue combination. | Demonstrates advanced UI scripting (e.g., Drag-and-Drop system). |
| **Interaction (Player / Env)** | The game is built around complex RE-style puzzles requiring items to be found, combined via UI, and used on objects in the environment. | Heavy use of Raycasts, Collider Triggers, and conditional logic. |


## Core Mechanics: The Loop & State Management
### The Time Loop System
- Duration: 15 minutes (or less, adjusted for testing).
- Reset Condition: The clock hits zero, or the player triggers a Fail State (e.g., breaking a critical object).
- Persistence: Only two things persist through the loop:
  - The Player's Clue Log (Temporal Index).
  - The Global State Manager (GSM) tracking major, permanent puzzle progress.
### The Global State Manager (GSM)
The GSM is the single most critical object. It is a persistent DontDestroyOnLoad Unity script that uses a Dictionary or Enum to track the state of every major puzzle component.
GSM Data Tracked (Example)Data TypePurposePuzzle1_KeysFoundint (0-3)Tracks how many keys are inserted into the Chronometric Lock.HasSynthesizedClue_BetrayalboolLocks the narrative progression until the player combines the correct clues in the UI.Lantern_IsChargedboolDetermines if the Arcane Lantern has the charged crystal (RE Puzzle 2).Clock_TimeInput_CorrectboolChecks if the player has entered the 8:12 time into the pendulum lock.

## Puzzle Breakdown (RE-Style Complexity)
The office contains three interconnected, multi-step puzzles that must be solved sequentially to succeed:
| **Puzzle Name** | **Objective** | **Key Complexity** |
|------------------|---------------|--------------------|
| **P1: The Chronometric Lock** | Find three unique keys (Brass Gear, Crystal, Pendulum) and insert them into the desk lock. | Requires using environmental clues (telescope reflection) and a UI-based clue combination (Synthesis) to reveal item locations. |
| **P2: The Ethereal Projector** | Keep the power running long enough to read a message that reveals the door code. | A time-sensitive resource management puzzle. Player must use the charged crystal from their inventory on the Lantern power source before activating the projector. |
| **P3: The Narrative Seal** | Activate four gargoyle busts in the correct lore sequence (Failure, Obsession, Betrayal, Escape) to open the final door. | Requires triggering specific hidden dialogue and narrative events in the correct order to advance the puzzle state, forcing lore interaction. |

## Development Focus & Next Steps
The next phase of development must focus on laying the groundwork for the core systems that enable the complexity:
- Build the Global State Manager (GSM) Script: Create the persistent object and its core data structure for tracking states.
- Player Controller & Raycast Interaction: Implement basic 2D movement and a script that handles player clicks/interactions with environment objects.
- UI Framework: Set up the basic canvas and begin designing the Temporal Index (Clue Log) for the drag-and-drop synthesis feature.
