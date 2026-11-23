# Hero Quest

## Team Members and Roles

This project is structured around a dual-branch architecture. The player's very first decision splits the game into two distinct storylines, allowing each team member to take full ownership of their own narrative, HTML/CSS structure, and interactive JavaScript features.

* **John Roberts**
  * **Storyline Ownership:** Branch A (The Volcano Mystery & Dragon Hunt)
  * **Responsibilities:** Narrative design, Mermaid flowchart architecture, state flag tracking, inventory array logic, text-input puzzle validation, and Quick Time Event (QTE) timer mechanics for Branch A.
* **Zachary Villard**
  * **Storyline Ownership:** Branch B (Castle Town Investigation, Goblin Ambush & The Wizard's Jungle)
  * **Responsibilities:** Narrative design, branching flowchart integration, HTML/CSS layout, and interactive JavaScript mechanics for Branch B.
* **Shared Responsibilities**
  * GitHub repository management, branch maintenance (`main`, `development`, and individual feature branches), peer code reviews via Pull Requests, and shared entry-screen styling.

---

## Application Overview

**Hero Quest** is a browser-based interactive fantasy/mystery adventure game built with HTML, CSS, and JavaScript.

### Story Premise
A young swordsman trained by his older brother loses everything when a dragon attacks their village, slaying his brother and plundering the settlement's gold and jewels. Months later, with the village's economy in ruins, the Royal Family tasks the young swordsman with tracking down the dragon and recovering the stolen royal jewels.

At the outset of the journey, the player makes a pivotal first decision that determines which path—and which mystery—they will uncover:
* **Branch A (Volcano Descent):** The swordsman heads straight into the dragon's volcano lair, uncovering hidden clues, royal conspiracies, and family secrets that lead to three distinct victory endings—each guarded by a high-stakes failure condition.
* **Branch B (Castle Town):** The swordsman begins in Castle Town, choosing between immediate vengeance—fighting through a goblin ambush in the canyon to slay the dragon—or investigating the wreckage to uncover a wizard who hypnotized the dragon, leading to a showdown in the jungle against the wizard's illusions.

### Gameplay & Navigation
* **Branching Choices:** Players navigate the story by making decisions at key crossroads, directly altering the narrative path and available endings.
* **Interactive Mechanics:** Depending on the path chosen, players will encounter text-input riddles, inventory management, health/stat tracking, and timed Quick Time Events (QTEs). *(Specific UI controls and navigation rules will be finalized during the build phase.)*

---

## Story Flowchart

The flowchart below outlines the opening split between both team members' storylines and maps out the complete branching structure across both paths (45 nodes total).

```mermaid
flowchart TD
    %% Opening Split
    Start[Prologue: The Royal Summons] --> Split{First Decision: Choose Your Approach}
    
    %% Branch B: Zachary's Path (Castle Town, Canyon & Wizard's Jungle)
    Split -- Path B: Start at Castle Town --> ZA[Scene 1: Start at Castle Town]
    ZA --> ZB{"Vengeance?"}
    ZB -->|Yes| ZD[March straight to canyon between town and volcano]
    ZB -->|No| ZC[Investigate wreck before leaving]
    ZC --> ZE{"Found any clues?"}
    ZD --> ZF[A horde of goblins charge at you in your sight]
    ZE -->|No| ZM[No luck, just find the Dragon]
    ZM --> ZD
    ZE -->|Yes| ZG["Find out it was actually set up by a wizard that hypnotized the dragon into attacking the village."]
    ZF --> ZH{"Survive?"}
    ZH -->|No| ZI([Game Over])
    ZH -->|Yes| ZJ[Win and Proceed to Volcano]
    ZJ --> ZK[Find the Dragon and Slay it]
    ZK --> ZL(["The End...?"])
    ZG --> ZN[Go to the Jungle Instead Where the Wizard Lives]
    ZN --> ZO["Wizard Puts a Spell; you're lost until you look past the illusion of the spell"]
    ZO --> ZP{"Succeed?"}
    ZP -->|No| ZQ([Game Over])
    ZP -->|Yes| ZR["You go past the Wizard's defenses and defeat him"]
    ZR --> ZS([The End])
    
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
