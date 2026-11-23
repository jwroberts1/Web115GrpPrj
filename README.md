# Hero Quest

## Team Members and Roles

This project is structured around a dual-branch architecture. The player's very first decision splits the game into two distinct storylines, allowing each team member to take full ownership of their own narrative, HTML/CSS structure, and interactive JavaScript features.

* **John Roberts**
  * **Storyline Ownership:** Branch A (The Volcano Mystery & Dragon Hunt)
  * **Responsibilities:** Narrative design, Mermaid flowchart architecture, state flag tracking, inventory array logic, text-input puzzle validation, and Quick Time Event (QTE) timer mechanics for Branch A.
* **Zachary Villard**
  * **Storyline Ownership:** Branch B *(To be added)*
  * **Responsibilities:** Narrative design, branching flowchart integration, HTML/CSS layout, and interactive JavaScript mechanics for Branch B.
* **Shared Responsibilities**
  * GitHub repository management, branch maintenance (`main`, `development`, and individual feature branches), peer code reviews via Pull Requests, and shared entry-screen styling.

---

## Application Overview

**Hero Quest** is a browser-based interactive fantasy/mystery adventure game built with HTML, CSS, and JavaScript. 

### Story Premise
A young swordsman trained by his older brother loses everything when a dragon attacks their village, slaying his brother and plundering the settlement's gold and jewels. Months later, with the village's economy in ruins, the Royal Family tasks the young swordsman with tracking down the dragon and recovering the stolen royal jewels. 

At the outset of the journey, the player makes a pivotal first decision that determines which path—and which mystery—they will uncover. In **Branch A**, the swordsman descends into the dragon's volcano lair, uncovering hidden clues, royal conspiracies, and family secrets that lead to three distinct victory endings—each guarded by a high-stakes failure condition.

### Gameplay & Navigation
* **Branching Choices:** Players navigate the story by making decisions at key crossroads, directly altering the narrative path and available endings.
* **Interactive Mechanics:** Depending on the path chosen, players will encounter text-input riddles, inventory management, health/stat tracking, and timed Quick Time Events (QTEs). *(Specific UI controls and navigation rules will be finalized during the build phase.)*

---

## Story Flowchart

The flowchart below outlines the initial split between both team members' storylines and maps out the complete branching structure for Branch A (26 nodes total, including 3 distinct victories and 3 unique death conditions).

```mermaid
flowchart TD
    %% Opening Split
    Start[Prologue: The Royal Summons] --> Split{First Decision: Choose Your Approach}
    
    %% Branch B: Zachary's Path (Act A: Hardship)
    Split -- Path B: Alternate Route --> Z1[Scene A: Start at Castle Town]
    A --> {Vengence?}
    B --> No --> A[Scene A1: Look for clues about the wrecked Town]
    B --> Yes --> B[Scene A2: Leave and Enter Canyon between Town and Volcano]

    %% Act B:
    
    %% Branch A: John's Path (Act 1: The Descent)
    Split -- Path A: Enter the Volcano Directly --> A[Scene 1: Enter the Volcano]
    A --> B{Crossroads}
    B -- Explore the Ruins --> C[Scene 2A: The Abandoned Royal Outpost]
    B -- Descend Deeper --> D[Scene 2B: The Hidden Crystal Caverns]
    
    %% Act 2: Gathering Clues
    C --> E[Scene 3A: Find the Mystic Control Jewel]
    D --> F[Scene 3B: Find the Torn Family Journal]
    
    %% Act 3: The Gate Puzzle
    E --> G[Scene 4: The Adamantine Gates]
    F --> G
    
    G --> H{How to bypass the gates?}
    H -- Solve the Lock (Text Input) --> I[Scene 4A: Gates Open Smoothly]
    H -- Crawl through Sulfur Vents --> J[Scene 4B: Enter Quietly but Lose Health]
    
    %% Act 4: The Dragon's Lair
    I --> K[Scene 5: Enter the Dragon's Lair]
    J --> K
    
    K --> L{Evaluate Clues / State Flags}
    
    %% Act 5: The Branching Finales
    L -- hasControlJewel == true --> M[Scene 6A: Speak the Command]
    L -- knowsLineage == true --> N[Scene 6B: Confront the Shadow Figure]
    L -- Default / No Clues --> O[Scene 6C: Draw Your Sword]
    
    %% Finale 1: The Royal Conspiracy
    M --> M1{Type the ancient word}
    M1 -- Correct --> P([Victory 1: Royal Conspiracy Exposed])
    M1 -- Incorrect --> S([Death 1: Incinerated by the Dragon])
    
    %% Finale 2: The Bastard Sibling
    N --> N1{Present evidence from Inventory}
    N1 -- Correct Item --> Q([Victory 2: Bastard Sibling Arrested])
    N1 -- Wrong Item --> T([Death 2: Backstabbed by Assassin])
    
    %% Finale 3: The Monster Hunt
    O --> O1{Dodge the attack QTE Timer}
    O1 -- Key pressed in time --> R([Victory 3: Dragon Slain in Combat])
    O1 -- Too slow --> U([Death 3: Devoured by the Dragon])
```
