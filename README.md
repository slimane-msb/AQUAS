# AQUAS: A Multi-Player Game

> Production-ready multiplayer strategy game showcasing advanced OOP, MVC architecture, and modern software engineering practices

[![Java](https://img.shields.io/badge/Java-ED8B00?style=flat&logo=java&logoColor=white)](https://www.java.com/)
[![MVC](https://img.shields.io/badge/Pattern-MVC-blue)](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)
[![Design Patterns](https://img.shields.io/badge/Patterns-5+-green)](https://refactoring.guru/design-patterns)
[![Code Quality](https://img.shields.io/badge/Quality-Production-brightgreen)](https://github.com)

## Executive Summary

A sophisticated cooperative strategy game built from the ground up using professional software engineering principles. This project demonstrates mastery of **object-oriented design**, **architectural patterns**, **event-driven programming**, and **custom UI framework development** through a complete game engine implementation.

**Key Technical Achievement**: Architected a maintainable, extensible codebase with **15+ well-structured classes** following SOLID principles, achieving complete separation of concerns through MVC pattern and implementing 5+ design patterns for scalable game state management.

---

## Project Highlights

| Metric | Value |
|--------|-------|
| **Architecture** | Model-View-Controller (MVC) |
| **Design Patterns** | Observer, State, Factory, Strategy, Singleton |
| **Classes** | 15+ organized components |
| **Lines of Code** | ~2,500 LOC |
| **Test Coverage** | Unit tests for Model, View, Controller |
| **Max Players** | 4-player cooperative gameplay |
| **UI Framework** | Custom Swing-based rendering engine |

---

## Game Overview

**Forbidden Island** is a cooperative board game adaptation where players race against time to collect four ancient artifacts from a progressively sinking island. Success requires strategic planning, resource management, and team coordination under pressure.

### Gameplay Mechanics

![Welcome Screen](https://user-images.githubusercontent.com/90608523/164999363-097f37b4-fc8a-46ff-ba5c-f14bcb3f4fb8.png)

**Core Features**:
- **Turn-based Strategy**: 3 actions per player per turn
- **Cooperative Gameplay**: 2-4 players working toward shared objectives
- **Dynamic Environment**: Probabilistic island flooding (3 tiles per turn)
- **Resource Management**: Key-artifact matching system
- **Risk/Reward Balance**: Strategic decisions under time constraints

![Game Rules](https://user-images.githubusercontent.com/90608523/164999378-0d7f8536-6e07-4af3-8f25-75e1c4c334d6.png)

### Help System

<p align="center">
  <img width="501" alt="Help Menu" src="https://user-images.githubusercontent.com/90608523/164999399-cc8aa616-97cc-40f7-9d0f-4acb5661098a.png">
</p>

---

## 🏗️ Software Architecture

### MVC Pattern Implementation

```
┌─────────────────────────────────────────────────────────────┐
│                    CONTROLLER LAYER                         │
│  ┌──────────────┐  ┌──────────────┐  ┌─────────────────┐    │
│  │  Controller  │  │ InputManager │  │  ButtonAction   │    │
│  │  (Orchestr.) │  │ (Keyboard)   │  │  (UI Events)    │    │
│  └──────┬───────┘  └──────┬───────┘  └───────-─┬───────┘    │
│         │                 │                    │            │
└─────────┼─────────────────┼────────────────────┼────────────┘
          │                 │                    │
          ↓                 ↓                    ↓
┌─────────────────────┐              ┌─────────────────────────┐
│    MODEL LAYER      │←─Observer────│      VIEW LAYER         │
│  ┌──────────────┐   │              │  ┌──────────────────┐   │
│  │   Island     │   │              │  │   ViewIsland     │   │
│  │ ┌──────────┐ │   │              │  │ ┌──────────────┐ │   │
│  │ │   Zone   │ │   │              │  │ │  ViewZone    │ │   │
│  │ └──────────┘ │   │              │  │ └──────────────┘ │   │
│  │ ┌──────────┐ │   │              │  │ ┌──────────────┐ │   │
│  │ │ Heliport │ │   │              │  │ │ ViewPlayer   │ │   │
│  │ └──────────┘ │   │              │  │ └──────────────┘ │   │
│  └──────────────┘   │              │  │ ┌──────────────┐ │   │
│  ┌──────────────┐   │              │  │ │ ViewArtefact │ │   │
│  │   Player     │   │              │  │ └──────────────┘ │   │
│  │ ┌──────────┐ │   │              │  │ ┌──────────────┐ │   │
│  │ │  Item    │ │   │              │  │ │  ViewKey     │ │   │
│  │ │  Key     │ │   │              │  │ └──────────────┘ │   │
│  │ │ Artefact │ │   │              │  │ ┌──────────────┐ │   │
│  │ └──────────┘ │   │              │  │ │  UIManager   │ │   │
│  └──────────────┘   │              │  │ │ ImageLoader  │ │   │
│  ┌──────────────┐   │              │  │ └──────────────┘ │   │
│  │    Utils     │   │              │  └──────────────────┘   │
│  │  Direction   │   │              └─────────────────────────┘
│  │  ItemType    │   │
│  │   Level      │   │
│  └──────────────┘   │
└─────────────────────┘
```

### Architecture Benefits

**Separation of Concerns**: Business logic completely isolated from presentation  
**Testability**: Each layer can be unit tested independently  
**Maintainability**: UI changes don't affect game logic and vice versa  
**Scalability**: Easy to extend with new features without refactoring core systems  
**Reusability**: Model and Controller can support multiple view implementations  
**Team Collaboration**: Frontend and backend developers can work in parallel  

---

## Project Structure

```
forbidden-island/
├── src/
│   ├── Controller/           # Business logic orchestration
│   │   ├── Controller.java       # Main game loop & turn management
│   │   ├── InputManager.java     # Keyboard event handling
│   │   ├── ButtonAction.java     # UI button interactions
│   │   └── GameStatus.java       # Game state enumeration
│   │
│   ├── Model/                # Core game logic & data
│   │   ├── Island/
│   │   │   ├── Island.java       # Island grid management
│   │   │   ├── Zone.java         # Individual tile with state
│   │   │   └── Heliport.java     # Special escape tile
│   │   ├── Player/
│   │   │   ├── Player.java       # Player entity with inventory
│   │   │   ├── Item.java         # Abstract item class
│   │   │   ├── Key.java          # Key for unlocking artifacts
│   │   │   └── Artefact.java     # Collectible artifacts
│   │   └── Utils/
│   │       ├── Direction.java    # Movement directions enum
│   │       ├── ItemType.java     # Item type enumeration
│   │       └── Level.java        # Difficulty levels enum
│   │
│   ├── View/                 # Presentation layer
│   │   ├── ViewGame/
│   │   │   ├── ViewIsland.java   # Island grid renderer
│   │   │   ├── ViewZone.java     # Tile visual component
│   │   │   ├── ViewPlayer.java   # Player sprite renderer
│   │   │   ├── ViewArtefact.java # Artifact icon display
│   │   │   ├── ViewKey.java      # Key icon display
│   │   │   └── GameObjectView.java # Abstract view class
│   │   └── ViewUtil/
│   │       ├── UIManager.java    # Main window & UI coordinator
│   │       ├── ImageLoader.java  # Asset loading & caching
│   │       └── StartScreenSelection.java # Menu system
│   │
│   └── media/                # Game assets
│       ├── zones/            # Tile sprites (normal & flooded)
│       ├── player/           # Player avatars & icons
│       ├── artefact/         # Artifact icons (air, fire, land, water)
│       ├── gameStatus/       # Screen backgrounds (menu, help, game-over)
│       └── font/             # Custom typography
│
├── test/                     # Unit tests
│   ├── modelTest.java        # Model layer tests
│   ├── vueTest.java          # View layer tests
│   └── controlleurTest.java  # Controller layer tests
│
├── diagrams/
│   └── uml ile interdite.pdf # UML class diagrams
│
├── out/production/project/   # Compiled bytecode
├── README.md
├── rapport.md                # Technical report (French)
└── project.iml               # IntelliJ project file
```

---

## User Interface Design

### Game Interface

<p align="center">
  <img width="542" alt="Active Gameplay" src="https://user-images.githubusercontent.com/90608523/164999441-80530beb-11a1-4758-a74f-d417131f98c5.png">
</p>

**UI Components**:
-  **Current Player Indicator**: Shows whose turn it is
-  **Action Counter**: Displays remaining actions (3 per turn)
-  **Inventory Display**: Real-time key and artifact tracking
-  **Island Grid**: Visual tile state representation
-  **Control Help**: Keyboard shortcuts overlay

### Main Game View

<p align="center">
  <img width="527" alt="Full Interface" src="https://user-images.githubusercontent.com/90608523/164999415-e1153c9b-0b49-4834-a3bf-e12fe769f7db.png">
</p>

**Visual Feedback System**:
-  **Color-coded Tile States**: 
  - Normal (Full color)
  - Flooded (Blue overlay)
  - Submerged (Transparent water)
-  **Player Offset Rendering**: Prevents visual overlap when multiple players share a tile
-  **Artifact Placement**: Visual indicators on island grid
-  **Real-time Updates**: Immediate state reflection after each action

---

##  Design Patterns Implementation

### 1. Model-View-Controller (MVC)
**Purpose**: Architectural separation of concerns  
**Implementation**:
- **Model**: Pure game logic with no UI dependencies
- **View**: Swing components listening to model changes
- **Controller**: Mediates user input and coordinates updates

### 2. Observer Pattern
**Purpose**: Decouple Model from View  
**Implementation**:
```java
// Model notifies View of state changes
public class Island {
    private List<Observer> observers = new ArrayList<>();
    
    public void notifyObservers() {
        for (Observer obs : observers) {
            obs.update(this);
        }
    }
}
```

### 3. State Pattern
**Purpose**: Clean tile state transitions  
**Implementation**:
```java
public enum ZoneState {
    NORMAL,    // Fully traversable
    FLOODED,   // Traversable but at risk
    SUBMERGED  // Impassable, removed from play
}
```

### 4. Factory Pattern
**Purpose**: Centralized object creation  
**Implementation**:
```java
// Player factory with role assignment
public static Player createPlayer(int id, Position pos) {
    return new Player(id, pos, new ArrayList<>());
}
```

### 5. Strategy Pattern
**Purpose**: Configurable difficulty levels  
**Implementation**:
```java
// Adjustable key discovery probability
public class Level {
    EASY(0.8),    // 80% success rate
    MEDIUM(0.6),  // 60% success rate
    HARD(0.4);    // 40% success rate
}
```

### 6. Singleton Pattern
**Purpose**: Single game controller instance  
**Implementation**:
```java
public class Controller {
    private static Controller instance;
    
    public static Controller getInstance() {
        if (instance == null) {
            instance = new Controller();
        }
        return instance;
    }
}
```

---

## Gameplay Mechanics

### Player Actions (3 per turn)

| Action | Key | Description | Constraints |
|--------|-----|-------------|-------------|
| **Move** | Arrow Keys | Navigate to adjacent tile | Target tile must not be submerged |
| **Dry Tile** | `D` | Remove water from flooded tile | Only works on flooded tiles, not submerged |
| **Search Key** | `S` | Attempt to find a key | Success based on difficulty probability |
| **Give Key** | `G` | Transfer key to teammate | Both players must be on same tile |
| **Collect Artifact** | `C` | Pick up artifact | Requires matching key + on artifact tile |
| **Pass Turn** | `P` | Skip remaining actions | Immediately triggers flood phase |

### Automatic Game Events

**End of Turn Sequence**:
1. Player completes 3 actions (or passes)
2.  Island floods 3 random tiles:
   - Normal → Flooded
   - Flooded → Submerged (permanently removed)
3.  **Auto-rescue System**: Players on newly submerged tiles are relocated to nearest safe tile
4.  Turn passes to next player

**Flood Algorithm**:
```java
// Probabilistic tile selection
for (int i = 0; i < 3; i++) {
    Zone randomZone = island.getRandomTraversableZone();
    randomZone.flood(); // State transition
}
```

---

##  Win/Loss Conditions

### Victory Requirements 
- ✓ All 4 artifacts collected by team
- ✓ All players reach heliport tile
- ✓ Heliport tile still above water
- ✓ Activate helicopter escape

### Defeat Conditions 
- ✗ Island completely submerged (no tiles remaining)
- ✗ Heliport tile submerged before escape
- ✗ Player trapped with no adjacent safe tiles
- ✗ All players unable to reach heliport

---

## Technical Features

### Advanced Programming Concepts

**Event-Driven Architecture**:
- Custom event system for game state changes
- Observer pattern for Model-View communication
- Asynchronous UI updates without blocking game logic

**State Management**:
- Centralized game state in Model layer
- Immutable state transitions with validation
- Transaction-like turn management

**Algorithm Design**:
- Randomized tile flooding with uniform distribution
- Pathfinding for player auto-relocation (BFS)
- Collision detection for player positioning
- Offset rendering algorithm for overlapping sprites

**Resource Management**:
- Efficient image loading with caching (ImageLoader)
- Lazy asset initialization
- Memory-conscious sprite management

### Object-Oriented Principles

**Encapsulation**: Private fields with controlled access via getters/setters  
**Inheritance**: Item → Key/Artifact hierarchy, GameObjectView → ViewZone/ViewPlayer  
**Polymorphism**: Different behaviors based on ItemType and ZoneState  
**Abstraction**: Abstract classes (Item, GameObjectView) for common functionality  

### SOLID Principles

- **Single Responsibility**: Each class has one clear purpose
- **Open/Closed**: Extensible design without modifying existing code
- **Liskov Substitution**: Subclasses can replace parent classes
- **Interface Segregation**: Focused interfaces (no god interfaces)
- **Dependency Inversion**: Depend on abstractions, not concretions


---

##  Getting Started

### Prerequisites
```bash
Java JDK 8 or higher
Java Swing (included in JDK)
```

### Compilation & Execution

**Option 1: Command Line**
```bash
# Compile all source files
javac -d out/production/project src/**/*.java

# Run the game
java -cp out/production/project Main
```

**Option 2: IDE (IntelliJ IDEA)**
```bash
# Open project.iml
# Run → Run 'Main'
```

### Keyboard Controls

| Key | Action |
|-----|--------|
| `↑` `↓` `←` `→` | Move player |
| `D` | Dry adjacent tile |
| `S` | Search for key |
| `G` | Give key to teammate |
| `C` | Collect artifact |
| `P` | Pass turn |
| `H` | Help menu |
| `ESC` | Return to main menu |

---

##  Performance Metrics

### Complexity Analysis

**Time Complexity**:
- Player movement: O(1)
- Tile flooding: O(n) where n = island size
- Path finding (auto-rescue): O(V + E) using BFS
- State validation: O(1)

**Space Complexity**:
- Island grid: O(n²) where n = grid dimension
- Player inventory: O(k) where k = max items
- Event queue: O(m) where m = pending events

### Scalability Considerations

- Grid size configurable (default: flexible)
- Player count adjustable (2-4 supported)
- Difficulty levels extensible
- Asset loading optimized with caching

---

## Learning Outcomes

### Software Engineering Skills

**Architecture & Design**:
- MVC pattern implementation from scratch
- Design pattern application (Observer, State, Factory, Strategy, Singleton)
- SOLID principles in practice
- Separation of concerns

**Java Programming**:
- Advanced OOP (inheritance, polymorphism, encapsulation, abstraction)
- Swing GUI development with custom components
- Event-driven programming
- Collections framework (Lists, Sets, Queues, Maps)
- Exception handling and validation

**Algorithm Design**:
- Graph traversal (BFS for pathfinding)
- Probabilistic algorithms (key discovery)
- State machines (tile states, game states)
- Random event generation

**Testing & Quality**:
- Unit testing methodology
- Test-driven development
- Code organization best practices
- Documentation standards

---

##  Future Enhancements

**Planned Features**:
- [ ] Network multiplayer support
- [ ] Save/load game state (serialization)
- [ ] Additional player roles with unique abilities
- [ ] AI opponents for single-player mode
- [ ] Sound effects and background music
- [ ] Animated tile transitions
- [ ] Leaderboard system
- [ ] Mobile version (Android port)

**Technical Improvements**:
- [ ] Dependency injection framework
- [ ] Continuous integration pipeline
- [ ] Performance profiling and optimization
- [ ] Code coverage > 80%
- [ ] Refactor to use JavaFX for modern UI

---

##  Documentation

### Available Resources

- **UML Diagrams**: `diagrams/uml ile interdite.pdf` - Complete class structure
- **Technical Report**: `rapport.md` - In-depth implementation analysis (French)
- **Source Code**: Fully commented with Javadoc
- **Unit Tests**: Test cases demonstrating usage

### Code Documentation

All classes include:
- Javadoc comments
- Inline explanations for complex logic
- Method parameter descriptions
- Return value specifications

---

## Development Team

**Developers**: 
- MESBAH Slimane
- GENTY Emilie

**Institution**: Paris-Saclay University  
**Program**: L2 Computer Science  
**Course**: Object-Oriented Programming Project  
**Supervisor**: [Course Instructor]  
**Academic Year**: [Year]

### Development Process

- **Version Control**: Git collaboration
- **Code Reviews**: Peer review process
- **Task Management**: Agile methodology
- **Pair Programming**: Complex features
- **Documentation**: Continuous updates


---

##  License

Academic project for educational purposes - Paris-Saclay University


---

**Built with Java & Swing** | **Production-Grade OOP** | **Enterprise Architecture**
