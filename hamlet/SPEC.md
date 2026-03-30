# Macbeth: The Scottish Game - Specification

## 1. Concept & Vision

**"Macbeth: The Scottish Game"** is an interactive narrative adventure where students become characters navigating the tragic world of Shakespeare's Scotland. Players make choices that ripple through the story, interact with iconic characters, and attempt to alter fate itself. The tone balances educational content with engaging gameplay—think "Choose Your Own Adventure" meets medieval Scotland, with the dark poetry of Shakespeare woven throughout.

The experience should feel like stepping into an illustrated manuscript—dramatic, atmospheric, but accessible to young learners.

---

## 2. Design Language

### Aesthetic Direction
**Reference**: Medieval illuminated manuscripts meets dark fantasy RPG (like Darkest Dungeon meets illustrated Shakespeare editions)

### Color Palette
- **Primary**: `#2C1810` (Deep burgundy-brown - Scottish tartan feel)
- **Secondary**: `#4A6741` (Forest green - Scottish highlands)
- **Accent**: `#C9A227` (Burnished gold - royal/tragic irony)
- **Background**: `#1A1A1A` (Dark parchment)
- **Text**: `#E8DCC4` (Aged parchment cream)
- **Danger**: `#8B0000` (Blood red)
- **Magic**: `#6B4E9E` (Witch purple)

### Typography
- **Headers**: "Cinzel Decorative" (Google Font) - medieval serif
- **Body**: "Crimson Text" (Google Font) - readable old-style serif
- **UI Elements**: "MedievalSharp" (Google Font) - game interface

### Spatial System
- 8px base unit
- Card-based layouts with ornate borders
- Generous padding for readability
- Clear visual hierarchy

### Motion Philosophy
- Subtle fade-ins for narrative text (typewriter effect)
- Dice roll animations (3D tumble feel)
- Location transitions with mist/fog overlay
- Success/failure with appropriate dramatic feedback
- Quoted text appears letter-by-letter

### Visual Assets
- 12 character tokens (SVG-based, silhouette style with distinguishing features)
- Map with illustrated location markers
- Dice visualization (6-sided)
- Item icons (potion bottles, weapons, scrolls)
- Ornate frame borders for content cards

---

## 3. Layout & Structure

### Game Flow
```
[Title Screen] → [Character Creation] → [Main Game Loop] → [Game Over/Ending]
                     ↓
              [Tutorial Modal]
```

### Main Game Screen Layout
```
┌─────────────────────────────────────────────────────────┐
│  [Token] Character Name    ❤️Health  💰Gold  📅Day 1   │
├─────────────────────────────────────────────────────────┤
│                                                         │
│                    [MAP AREA]                           │
│           Interactive Scotland Map                      │
│        (Click locations to travel)                      │
│                                                         │
├─────────────────────────────────────────────────────────┤
│  [Stats Panel]  │  [Action Buttons]  │  [Mini-Game]    │
│  Power: ███░░  │  [Inventory]       │  [Current       │
│  Speed: ██░░░  │  [Shop]            │   Location      │
│  Intel: ████░  │  [Character Info]  │   Details]      │
│  Reput: ██░░░  │  [Rest/Advance]    │                 │
└─────────────────────────────────────────────────────────┘
```

### Responsive Strategy
- Desktop-first (school computers)
- Tablet-friendly layout
- Mobile: Stack layout vertically
- Minimum width: 320px

---

## 4. Features & Interactions

### 4.1 Character Creation
- **Name Input**: English text, 2-20 characters, validated
- **Token Selection**: Grid of 12 character silhouettes
  - Macbeth, Lady Macbeth, Banquo, Macduff, Duncan, Malcom
  - Witch 1 (Heccate), Witch 2 (Veiled), Witch 3 (Croaking)
  - Lennox, Ross, Fleance
- **Attribute Allocation**: 5 points to distribute
  - Base: 5 each → Max: 10
  - Visual slider or +/- buttons
  - Points remaining counter

### 4.2 Attribute System
| Attribute | Description | Used For |
|-----------|-------------|----------|
| **Power** | Combat strength, physical prowess | Combat challenges, intimidation |
| **Speed** | Agility, quick thinking | Chase scenes, time-based puzzles |
| **Intelligence** | Wisdom, knowledge, deduction | Riddle solving, strategy, witch encounters |
| **Sanity** | Mental stability (key theme!) | Witch interactions, pressure situations |
| **Reputation** | Honor, social standing, beauty | Political challenges, NPC reactions |

### 4.3 Challenge System (Dice + Modifier)
```
Roll: 1D6 + Attribute Modifier ≥ Challenge Rating (CR)
```

| CR Level | Description | Example |
|----------|-------------|---------|
| 1-3 | Easy | Simple questions, light tasks |
| 4-6 | Moderate | Standard combat, puzzles |
| 7-9 | Hard | Boss encounters, complex riddles |
| 10+ | Legendary | Altering major plot points |

**Outcomes**:
- **Critical Success** (Roll 6 + modifier ≥ CR+3): Double rewards, special narrative
- **Success** (Roll + modifier ≥ CR): Normal rewards
- **Failure** (Roll + modifier < CR): Partial/no rewards, consequences
- **Critical Failure** (Roll 1): Severe penalty, sanity damage

### 4.4 The Map - Scotland

| Location | Description | Available Mini-Games | Special |
|----------|-------------|---------------------|---------|
| **Forres (The Heath)** | Where the witches prophesy | Witch's Riddle, Fate Reading | Starting location, 3 daily games |
| **Battlefield** | Opening battle site | Combat Trial, Sword Practice | Power challenges, loot |
| **Inverness Castle** | Macbeth's home | Servant's Quiz, Wine Memory | Lady Macbeth's domain |
| **Dunsinane Palace** | Macbeth's throne | Court Intrigue, Political Debate | Influence/power challenges |
| **Cawdor Castle** | Duncan's seat | Honor Trial, Loyalty Test | Reputation challenges, main quest |
| **Glamis Castle** | Ancient ruins | Ghost Whispers, Ancient Riddle | Intelligence/Sanity challenges |
| **Fife (Macduff's)** | Macduff's estate | Investigation, Evidence Hunt | Unlocks key plot points |
| **Birnham Wood** | The prophecy's forest | Stealth Mission, Wood Lore | Speed challenges |

### 4.5 Mini-Games (5 Per Day)

**Type 1: Combat Challenge (Power)**
- Turn-based dice duel against opponents
- Player rolls 2D6 vs opponent's CR
- Win: Gold + possible weapon
- Lose: Health damage + lose reputation

**Type 2: Witch's Riddle (Intelligence + Sanity)**
- 3 riddles from the play
- Each correct: Points toward prophecy manipulation
- Wrong: Sanity damage
- Special: Answer with quote = bonus

**Type 3: Memory/Trivia Quiz**
- Questions about the play's events
- Correct answers earn gold + hints
- Wrong: Lose a turn, small sanity hit

**Type 4: Stealth Mission (Speed + Intelligence)**
- Avoid detection challenges
- Multiple choice navigation
- Success: Secret items, plot intel

**Type 5: Political Intrigue (Reputation + Intelligence)**
- Navigate court gossip
- Choose correct responses
- Affects reputation and unlocks options

### 4.6 Item Shop

| Item | Cost | Effect | Description |
|------|------|--------|-------------|
| Health Potion | 10g | Restore 20 HP | "Doctor's mixture" |
| Sanity Elixir | 15g | Restore 10 Sanity | "Dew of mountain herbs" |
| Lucky Charm | 25g | +1 to one roll | "A horse's horseshoe" |
| Steel Dagger | 30g | +2 Power in combat | "Bare bodkin" |
| Informant's Scroll | 20g | Hint for riddle | "Words without thoughts" |
| Noble's Mask | 40g | +2 Reputation | "Face to face in the mirror" |
| Witch's Eye | 50g | See CR before challenge | "What the eye sees not" |
| Macduff's Letter | 35g | Special quest unlock | "All my precious children" |

### 4.7 Day/Night Cycle & Progression
- Each "day" represents an Act
- 5 Days = Complete game
- Each day: 5 mini-games max, must rest to continue
- Advancing day: Rest action, heals slightly, triggers next Act

### 4.8 Story Integration - Act References

**Act 1 - "Fair and Foul"**
- Opening: Battlefield introduction
- Witch encounter at Forres
- Duncan's arrival at Inverness
- The murder decision point

**Act 2 - "Is This a Dagger"**
- The murder night at Inverness
- Ghost appearances
- Morning after guilt

**Act 3 - "Blood Will Have Blood"**
- Banquo's murder plot
- Fleance escapes
- Growing paranoia

**Act 4 - "Double, Double"**
- Witch confrontations
- Macduff's family tragedy
- Prophecy revelations

**Act 5 - "Out, Damned Spot"**
- Final battles
- Lady Macbeth's fate
- Birnham Wood prophecy
- Multiple endings

### 4.9 Key Quotes Integration
Quotes appear as:
- Tutorial hints
- Success/failure messages
- Location descriptions
- Character dialogue
- Ending narration

**Notable Quotes to Include**:
- "Fair is foul, and foul is fair" (Act 1, Scene 1)
- "Unbidden, unconstrained" (Macbeth)
- "I have no spur to prick the sides of my intent" (Act 1)
- "I dare do all that may become a man" (Act 1)
- "Is this a dagger which I see before me?" (Act 2, Scene 1)
- "Out, damned spot! Out, I say!" (Act 5, Scene 1)
- "Life's but a walking shadow, a poor player" (Act 5, Scene 5)
- "Nothing is, but what is not" (Macbeth)
- "All hail, Macbeth, that shalt be king hereafter!" (Witches)
- "To crown my thoughts with acts, be it thought and done" (Macbeth)

### 4.10 Player Choices & Multiple Endings

**Choice Points**:
1. Listen to the witches' prophecy?
2. Kill King Duncan?
3. Kill Banquo?
4. Trust Lady Macbeth?
5. Join Macduff's rebellion?
6. Flee or fight at the end?

**Endings**:
1. **The True King** (Good): Malcolm takes throne, Macbeth dies nobly
2. **The Tyrant Falls** (Neutral): Macbeth defeated, Lady Macbeth mad
3. **The Prophecy Fulfilled** (Dark): Macbeth rules but at terrible cost
4. **The Scholar's Victory** (Secret): Player collected all knowledge, alternate fate

---

## 5. Component Inventory

### 5.1 Title Screen
- Game logo with atmospheric background
- "Begin Quest" button (ornate gold border)
- "How to Play" button (opens tutorial)
- Fade-in animation on load

### 5.2 Character Creation Panel
- Name input field (parchment style)
- Token grid (3x4, hover highlights)
- Selected token glow effect
- Attribute sliders with point counter
- "Begin Adventure" button (disabled until complete)

### 5.3 Main Game HUD
- **Top Bar**: Character token, name, HP bar, Sanity bar, Gold, Day counter
- **Map**: Interactive SVG map with location markers
- **Location Panel**: Current location name, description, available actions
- **Action Bar**: Inventory, Shop, Rest, Advance Day buttons

### 5.4 Mini-Game Modal
- Full-screen overlay with close option
- Game-specific UI
- Timer (optional for some games)
- Roll animation area
- Result display with quote

### 5.5 Shop Interface
- Item cards with icon, name, cost, effect
- Buy button (disabled if insufficient gold)
- Current gold display
- "Continue" button to return

### 5.6 Inventory Panel
- Grid of owned items
- Item tooltip on hover
- "Use" button for consumables
- Equipment slots display

### 5.7 Dialogue/Story Screen
- Character portrait
- Dialogue text (typewriter effect)
- Choice buttons (2-4 options)
- Quote attribution

### 5.8 Challenge Resolution Display
- Animated dice roll
- Modifier breakdown
- CR comparison
- Win/Lose animation
- Rewards/penalties list

### States for All Interactive Elements
- **Default**: Base appearance
- **Hover**: Slight glow/lift
- **Active/Selected**: Gold border, highlighted
- **Disabled**: Grayed out, no pointer
- **Loading**: Subtle pulse animation

---

## 6. Technical Approach

### Architecture
- **Single HTML file** with embedded CSS and JavaScript
- **No external dependencies** except Google Fonts
- **LocalStorage** for game saves
- **Modular JavaScript** with clear separation of concerns

### Data Structure

```javascript
// Game State
const gameState = {
  player: {
    name: "",
    token: "",
    attributes: { power: 5, speed: 5, intelligence: 5, sanity: 5, reputation: 5 },
    hp: 100,
    maxHp: 100,
    gold: 50,
    inventory: [],
    achievements: []
  },
  day: 1,
  currentLocation: "forres",
  challengesCompleted: [],
  storyFlags: {},
  gamesPlayedToday: 0,
  gameComplete: false
};

// Locations Data
const locations = {
  forres: {
    name: "Forres - The Heath",
    description: "Where the three sisters gather in the mist...",
    challenges: ["witchRiddle", "fateReading"],
    unlocked: true
  },
  // ... etc
};

// Mini-games Data
const miniGames = {
  witchRiddle: {
    name: "The Witch's Riddle",
    type: "riddle",
    primaryStat: "intelligence",
    secondaryStat: "sanity",
    cr: 5,
    questions: [...]
  }
};
```

### Save System
- Auto-save after each major action
- Manual save button
- Load game on return
- New game clears save

### Audio (Optional Enhancement)
- No audio required for MVP
- Could add ambient sounds later

---

## 7. Educational Value

### Learning Outcomes
1. **Literary Knowledge**: Characters, plot, quotes
2. **Decision Making**: Consequence of choices
3. **Probability**: Dice mechanics, odds
4. **Reading Comprehension**: Riddle solving, trivia
5. **Historical Context**: Medieval Scotland, Shakespeare

### Teacher Features
- Printable quiz at end
- Score/completion tracking
- Discussion prompts after game

---

## 8. Implementation Priorities

### MVP (Must Have)
1. Title screen
2. Character creation
3. Map navigation
4. Basic mini-game (riddle/trivia)
5. Dice challenge system
6. Win/lose conditions
7. Basic ending

### Phase 2 (Should Have)
1. All 5 mini-games
2. Item shop
3. Multiple endings
4. Day progression
5. Save/load

### Phase 3 (Nice to Have)
1. Animations and polish
2. Sound effects
3. Achievement system
4. Teacher resources
