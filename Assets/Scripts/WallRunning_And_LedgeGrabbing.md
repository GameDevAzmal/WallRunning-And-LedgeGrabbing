# Physics-Based Implementation of Advanced Movement Mechanics: Wall Running and Ledge Grabbing Systems in 3D Game Environments

**Author:** M. Azmal Baig

---

## Abstract

This thesis presents a comprehensive analysis of physics-based advanced movement mechanics in 3D game environments, specifically focusing on wall running and ledge grabbing systems. The study examines the mathematical foundations, physics principles, and algorithmic implementations that enable realistic and responsive player movement beyond traditional locomotion. Through detailed code analysis and theoretical examination, this research demonstrates how Unity's physics engine can be leveraged to create sophisticated movement systems using vector mathematics, force dynamics, and state machine architectures. The implementation utilizes raycast detection algorithms, rigidbody manipulation, and finite state machines to achieve seamless transitions between different movement states. Key findings include the critical importance of force application timing, the mathematical relationships governing wall adhesion and ledge detection, and the integration patterns required for cohesive multi-modal movement systems. This work contributes to the understanding of physics-based game mechanics and provides a foundation for implementing advanced player movement in 3D environments.

## Table of Contents

- [Physics-Based Implementation of Advanced Movement Mechanics: Wall Running and Ledge Grabbing Systems in 3D Game Environments](#physics-based-implementation-of-advanced-movement-mechanics-wall-running-and-ledge-grabbing-systems-in-3d-game-environments)
  - [Abstract](#abstract)
  - [Table of Contents](#table-of-contents)
  - [1. Introduction](#1-introduction)
  - [2. Literature Review](#2-literature-review)
    - [2.1 Foundations of Physics-Based Movement](#21-foundations-of-physics-based-movement)
    - [2.2 Advanced Movement Mechanics](#22-advanced-movement-mechanics)
    - [2.3 State Management in Movement Systems](#23-state-management-in-movement-systems)
  - [3. Methodology](#3-methodology)
    - [3.1 Research Approach](#31-research-approach)
    - [3.2 Analysis Framework](#32-analysis-framework)
    - [3.3 Technical Environment](#33-technical-environment)
  - [4. Results and Analysis](#4-results-and-analysis)
    - [4.1 Wall Running System Implementation](#41-wall-running-system-implementation)
      - [4.1.1 Core Physics Principles](#411-core-physics-principles)
        - [Figure 4.1: Wall Detection System](#figure-41-wall-detection-system)
        - [Figure 4.2: Ground Height Validation](#figure-42-ground-height-validation)
      - [4.1.2 Wall Forward Direction Calculation](#412-wall-forward-direction-calculation)
        - [Figure 4.3: Cross Product Vector Calculation](#figure-43-cross-product-vector-calculation)
        - [Figure 4.4: Wall Forward And Backword Direction Selection](#figure-44-wall-forward-and-backword-direction-selection)
      - [4.1.3 Force Application and Physics Integration](#413-force-application-and-physics-integration)
      - [4.1.4 Vertical Movement Control](#414-vertical-movement-control)
      - [4.1.5 Wall Jump Mechanics](#415-wall-jump-mechanics)
      - [4.1.6 State Management and Timing](#416-state-management-and-timing)
    - [4.2 Ledge Grabbing System Implementation](#42-ledge-grabbing-system-implementation)
      - [4.2.1 Collision Detection and Spherecasting](#421-collision-detection-and-spherecasting)
        - [Figure 4.1: Raycast vs Spherecast Detection Comparison](#figure-41-raycast-vs-spherecast-detection-comparison)
        - [Figure 4.2: Unity Layer Mask Configuration](#figure-42-unity-layer-mask-configuration)
        - [Figure 4.3: Spherecast Detection System](#figure-43-spherecast-detection-system)
        - [Figure 4.4: Ledge Detection Sequence](#figure-44-ledge-detection-sequence)
        - [Figure 4.5: Ledge Grab Execution](#figure-45-ledge-grab-execution)
        - [Figure 4.6: Rigidbody Physics State Control](#figure-46-rigidbody-physics-state-control)
      - [4.2.2 Distance Calculation and Grab Validation](#422-distance-calculation-and-grab-validation)
      - [4.2.3 Physics State Manipulation During Ledge Hold](#423-physics-state-manipulation-during-ledge-hold)
      - [4.2.5 Ledge Jump Implementation](#425-ledge-jump-implementation)
      - [4.2.6 State Transition and Exit Conditions](#426-state-transition-and-exit-conditions)
    - [4.3 Mathematical Foundations and Physics Principles](#43-mathematical-foundations-and-physics-principles)
      - [4.3.1 Vector Mathematics in 3D Movement](#431-vector-mathematics-in-3d-movement)
      - [4.3.2 Force Dynamics and Newton's Laws](#432-force-dynamics-and-newtons-laws)
      - [4.3.3 Collision Detection Mathematics](#433-collision-detection-mathematics)
      - [4.3.4 Time Integration and Frame Rate Independence](#434-time-integration-and-frame-rate-independence)
    - [4.4 System Integration and State Management](#44-system-integration-and-state-management)
      - [4.4.1 Central Movement State Architecture](#441-central-movement-state-architecture)
      - [4.4.2 State Priority Hierarchy and Control Flow](#442-state-priority-hierarchy-and-control-flow)
      - [4.4.3 Advanced Movement Integration Patterns](#443-advanced-movement-integration-patterns)
      - [4.4.4 Movement Parameter Coordination](#444-movement-parameter-coordination)
      - [4.4.5 Movement Restriction and Override System](#445-movement-restriction-and-override-system)
      - [4.4.6 Speed Control and Momentum Management](#446-speed-control-and-momentum-management)
      - [4.4.7 Smooth State Transitions and Momentum Preservation](#447-smooth-state-transitions-and-momentum-preservation)
      - [4.4.8 Inter-System Communication and Conflict Resolution](#448-inter-system-communication-and-conflict-resolution)
      - [4.4.9 Gravity and Physics State Coordination](#449-gravity-and-physics-state-coordination)
    - [4.5 Complete Movement Architecture Analysis](#45-complete-movement-architecture-analysis)
      - [4.5.1 Base Movement Physics Implementation](#451-base-movement-physics-implementation)
      - [4.5.2 Slope Handling and Terrain Adaptation](#452-slope-handling-and-terrain-adaptation)
      - [4.5.3 Air Movement and Jump Mechanics](#453-air-movement-and-jump-mechanics)
      - [4.5.4 Speed Control and Velocity Management](#454-speed-control-and-velocity-management)
      - [4.5.5 Dynamic Speed Adjustment and State Transitions](#455-dynamic-speed-adjustment-and-state-transitions)
      - [4.5.6 Ground Detection and Physics State Management](#456-ground-detection-and-physics-state-management)
      - [4.5.7 Integration with Advanced Movement Systems](#457-integration-with-advanced-movement-systems)
  - [5. Discussion](#5-discussion)
    - [5.1 Implementation Effectiveness](#51-implementation-effectiveness)
    - [5.2 Mathematical Sophistication](#52-mathematical-sophistication)
    - [5.3 Performance Considerations](#53-performance-considerations)
    - [5.4 Integration Architecture](#54-integration-architecture)
    - [5.5 Extensibility and Modularity](#55-extensibility-and-modularity)
    - [5.6 Physical Accuracy vs. Gameplay Requirements](#56-physical-accuracy-vs-gameplay-requirements)
    - [5.8 Base Movement System Integration Excellence](#58-base-movement-system-integration-excellence)
    - [5.9 Comprehensive System Architecture](#59-comprehensive-system-architecture)
    - [5.10 Performance and Scalability Analysis](#510-performance-and-scalability-analysis)
  - [6. Conclusion](#6-conclusion)
    - [6.1 Key Findings](#61-key-findings)
    - [6.2 Theoretical Contributions](#62-theoretical-contributions)
    - [6.3 Practical Applications](#63-practical-applications)
    - [6.4 Technical Excellence](#64-technical-excellence)
    - [6.5 Future Research Directions](#65-future-research-directions)
    - [6.6 Industry Impact](#66-industry-impact)
    - [6.7 Limitations and Considerations](#67-limitations-and-considerations)
    - [6.8 Synthesis of Findings](#68-synthesis-of-findings)
    - [6.9 Final Assessment](#69-final-assessment)
  - [7. References](#7-references)
    - [Primary Sources](#primary-sources)
    - [Mathematical and Physics References](#mathematical-and-physics-references)
    - [Online Sources](#online-sources)
  - [Appendices](#appendices)
    - [Appendix A: Complete Code Implementations](#appendix-a-complete-code-implementations)
      - [A.1 WallRunningAdvanced.cs - Complete Implementation](#a1-wallrunningadvancedcs---complete-implementation)
      - [A.2 LedgeGrabbing.cs - Complete Implementation](#a2-ledgegrabbingcs---complete-implementation)
    - [Appendix B: Mathematical Derivations](#appendix-b-mathematical-derivations)
      - [B.1 Cross Product Calculation for Wall Forward Vector](#b1-cross-product-calculation-for-wall-forward-vector)
      - [B.2 Distance Calculation in 3D Space](#b2-distance-calculation-in-3d-space)
      - [B.3 Force Vector Composition](#b3-force-vector-composition)
    - [Appendix C: Performance Analysis Data](#appendix-c-performance-analysis-data)
      - [C.1 Computational Complexity](#c1-computational-complexity)
      - [C.2 Memory Usage Analysis](#c2-memory-usage-analysis)
    - [Appendix D: Configuration Parameters Guide](#appendix-d-configuration-parameters-guide)
      - [D.1 Wall Running Parameters](#d1-wall-running-parameters)
      - [D.2 Ledge Grabbing Parameters](#d2-ledge-grabbing-parameters)
    - [Appendix E: Troubleshooting Guide](#appendix-e-troubleshooting-guide)
      - [E.1 Common Implementation Issues](#e1-common-implementation-issues)
      - [E.2 Performance Optimization Tips](#e2-performance-optimization-tips)

## 1. Introduction

Modern 3D game environments demand increasingly sophisticated movement mechanics that transcend basic walking and jumping paradigms. Advanced movement systems, particularly wall running and ledge grabbing mechanics, have become essential components in creating immersive and dynamic gameplay experiences. These systems present unique challenges in physics simulation, requiring precise mathematical calculations, robust detection algorithms, and seamless state management to achieve realistic and responsive player control.

This thesis examines the implementation of two interconnected advanced movement mechanics: wall running and ledge grabbing systems. The research focuses on the practical application of physics principles within Unity's game engine, analyzing how theoretical concepts translate into functional code implementations. The study addresses the fundamental question of how complex movement behaviors can be achieved through the systematic application of force dynamics, vector mathematics, and algorithmic state management.

The significance of this research lies in its comprehensive examination of the bridge between theoretical physics and practical game development. By analyzing actual implementation code, this work provides insights into the challenges and solutions involved in creating responsive, realistic movement systems. The wall running system demonstrates principles of surface adhesion, momentum conservation, and gravity manipulation, while the ledge grabbing system illustrates precise collision detection, position interpolation, and state transition management.

The integrated approach of these two systems reveals the complexity inherent in modern movement mechanics, where multiple subsystems must coordinate seamlessly to provide a cohesive player experience. The implementation utilizes Unity's Rigidbody component for physics simulation, combining it with custom algorithms for detection, force application, and state management.

This thesis contributes to the field of game physics by providing a detailed technical analysis of advanced movement implementations, offering both theoretical understanding and practical guidance for developers seeking to implement similar systems. The research methodology involves comprehensive code analysis, mathematical derivation of underlying principles, and examination of the algorithmic structures that enable these complex behaviors.

## 2. Literature Review

### 2.1 Foundations of Physics-Based Movement

Physics-based movement in 3D environments builds upon fundamental principles of classical mechanics, particularly Newton's laws of motion and vector calculus. The implementation of realistic movement requires understanding of force application, momentum conservation, and the mathematical representation of motion in three-dimensional space.

### 2.2 Advanced Movement Mechanics

Wall running mechanics in video games represent a specialized application of surface adhesion principles combined with momentum preservation. Ledge grabbing systems require sophisticated collision detection algorithms combined with precise position matching and state management.

### 2.3 State Management in Movement Systems

Complex movement mechanics require robust state management systems to handle transitions between different movement modes. Finite state machines provide a structured approach to managing these transitions, ensuring that conflicting movement states cannot occur simultaneously.

## 3. Methodology

### 3.1 Research Approach

This research employs a code-analysis methodology, examining the actual implementation of wall running and ledge grabbing systems within Unity's game engine. The analysis focuses on the mathematical principles, physics implementations, and algorithmic structures that enable these advanced movement mechanics.

### 3.2 Analysis Framework

The methodology involves detailed examination of two primary source files: `WallRunningAdvanced.cs` and `LedgeGrabbing.cs`. These implementations provide concrete examples of how theoretical physics principles are translated into functional game mechanics through programmatic solutions.

### 3.3 Technical Environment

The implementations analyzed utilize Unity 2022.3 LTS with the following key components:
- Unity's built-in physics engine for rigidbody simulation
- Input system for player control detection
- Transform and camera systems for spatial calculations
- LayerMask system for selective collision detection

## 4. Results and Analysis

### 4.1 Wall Running System Implementation

#### 4.1.1 Core Physics Principles

The wall running system uses raycast detection for wall presence:

```csharp
wallRight = Physics.Raycast(transform.position, orientation.right, out rightWallhit, wallCheckDistance, whatIsWall);
wallLeft = Physics.Raycast(transform.position, -orientation.right, out leftWallhit, wallCheckDistance, whatIsWall);
```

**Detailed Code Analysis:**
- `Physics.Raycast()` casts rays from player position in left and right directions simultaneously
- `orientation.right` and `-orientation.right` provide bilateral detection vectors
- `out rightWallhit`/`out leftWallhit` store collision data including surface normals and hit points
- `wallCheckDistance` controls detection range (typically 0.7-1.2 units)
- `whatIsWall` LayerMask enables selective detection of wall objects only
- Bilateral approach allows detection of walls on either side for comprehensive coverage

##### Figure 4.1: Wall Detection System

<img src="wall%20check.png" alt="Wall Check Mechanism" width="300"/>

*Figure 4.1: Bilateral wall detection system showing raycasts extending from the player position in both left and right directions, with configurable detection distance and ground height validation.*

##### Figure 4.2: Ground Height Validation

<img src="min%20height.png" alt="Ground Height Check" width="300"/>

*Figure 4.2: Ground detection raycast system demonstrating the minimum jump height requirement for wall running activation, ensuring players are sufficiently above ground level.*

The `AboveGround()` method prevents wall running at ground level:
```csharp
private bool AboveGround()
{
    return !Physics.Raycast(transform.position, Vector3.down, minJumpHeight, whatIsGround);
}
```

**Detailed Code Analysis:**
- Downward raycast from player position checks for ground within `minJumpHeight` distance
- `Vector3.down` represents downward direction (0, -1, 0)
- `whatIsGround` LayerMask filters detection to ground objects only
- Negation operator `!` inverts result: returns `true` when NO ground detected (player is above ground)
- Prevents wall running activation when player is too close to ground level

#### 4.1.2 Wall Forward Direction Calculation

The system calculates movement direction along the wall surface:

```csharp
Vector3 wallNormal = wallRight ? rightWallhit.normal : leftWallhit.normal;
Vector3 wallForward = Vector3.Cross(wallNormal, transform.up);

if ((orientation.forward - wallForward).magnitude > (orientation.forward - -wallForward).magnitude)
    wallForward = -wallForward;
```

**Detailed Code Analysis:**
- Ternary operator selects appropriate wall normal based on detected wall side
- `Vector3.Cross(wallNormal, transform.up)` calculates perpendicular vector using cross product operation
- Cross product creates horizontal vector tangent to wall surface: **wallForward = wallNormal × transform.up**
- Direction alignment logic compares vector magnitudes to determine optimal movement direction
- `(orientation.forward - wallForward).magnitude` measures alignment with player's facing direction
- Flips direction if opposite alignment is closer: ensures natural forward movement along walls
- Result provides intuitive wall movement direction relative to camera orientation

The cross product creates a tangent vector: **wallForward = wallNormal × transform.up**

##### Figure 4.3: Cross Product Vector Calculation

<img src="vector3wallfront.png" alt="Cross Product Visualization" width="300"/>

*Figure 4.3: 3D visualization of the cross product operation between wall normal vector and world up vector, showing how the perpendicular wall forward vector is calculated for movement direction.*

##### Figure 4.4: Wall Forward And Backword Direction Selection

<img src="wallforword.png" alt="Wall Forward Direction" width="300"/> <img src="wallbackword.png" alt="Wall Backword Direction" width="300"/>

*Figure 4.4: Visual demonstration of the directional alignment algorithm, showing how the system chooses between wallForward and -wallForward based on player facing direction to ensure natural movement flow.*

The direction selection uses vector magnitude comparison:
**|orientation.forward - wallForward| vs |orientation.forward - (-wallForward)|**

#### 4.1.3 Force Application and Physics Integration

The wall running movement system applies multiple forces simultaneously to achieve the desired movement behavior:

```csharp
// forward force
rb.AddForce(wallForward * wallRunForce, ForceMode.Force);

// push to wall force
if (!(wallLeft && horizontalInput > 0) && !(wallRight && horizontalInput < 0))
    rb.AddForce(-wallNormal * 100, ForceMode.Force);

// weaken gravity
if (useGravity)
    rb.AddForce(transform.up * gravityCounterForce, ForceMode.Force);
```

**Detailed Code Analysis:**

**Forward Propulsion Force:**
- `rb.AddForce(wallForward * wallRunForce, ForceMode.Force)` applies continuous directional force
- `wallRunForce` scalar controls movement speed along wall surface (typically 200-800)
- `ForceMode.Force` provides frame-rate dependent continuous application

**Wall Adhesion Force:**
- `rb.AddForce(-wallNormal * 100, ForceMode.Force)` pushes player toward wall surface
- Negative normal direction points into wall, preventing player from falling away
- Conditional logic prevents force when player actively moves toward wall:
  - `!(wallLeft && horizontalInput > 0)` = "NOT (on left wall AND pushing right)"
  - Allows natural wall release when player pushes away

**Gravity Counter Force:**
- `rb.AddForce(transform.up * gravityCounterForce, ForceMode.Force)` partially counteracts gravity
- Creates characteristic "floating" sensation while maintaining some downward pull
- `useGravity` flag allows designers to toggle this effect

#### 4.1.4 Vertical Movement Control

The system provides precise control over vertical movement during wall running through direct velocity manipulation:

```csharp
if (upwardsRunning)
    rb.linearVelocity = new Vector3(rb.linearVelocity.x, wallClimbSpeed, rb.linearVelocity.z);
if (downwardsRunning)
    rb.linearVelocity = new Vector3(rb.linearVelocity.x, -wallClimbSpeed, rb.linearVelocity.z);
```

**Detailed Code Analysis:**
- Direct velocity manipulation replaces Y-component while preserving horizontal momentum
- `wallClimbSpeed` provides immediate vertical control (typically 3-8 units)
- Negative value for downward movement: `-wallClimbSpeed`
- Input flags `upwardsRunning`/`downwardsRunning` control activation
- Bypasses physics acceleration for responsive vertical movement

This implementation demonstrates direct velocity control, where the Y-component of the velocity vector is explicitly set while preserving horizontal velocity components for responsive wall climbing mechanics.

#### 4.1.5 Wall Jump Mechanics

The wall jump system implements impulse-based force application to achieve explosive movement away from the wall:

```csharp
Vector3 forceToApply = transform.up * wallJumpUpForce + wallNormal * wallJumpSideForce;
rb.linearVelocity = new Vector3(rb.linearVelocity.x, 0f, rb.linearVelocity.z);
rb.AddForce(forceToApply, ForceMode.Impulse);
```

**Detailed Code Analysis:**
- Composite force vector combines upward and outward components through vector addition
- `transform.up * wallJumpUpForce` provides vertical lift (typically 7-15 units)
- `wallNormal * wallJumpSideForce` creates outward push from wall (typically 7-12 units)
- Y-velocity reset ensures consistent jump height regardless of current vertical movement
- `ForceMode.Impulse` applies instantaneous explosive force for immediate wall separation

The delayed force application addresses timing issues in physics state transitions, ensuring clean separation between wall running and jump states.

#### 4.1.6 State Management and Timing

The wall running system implements a finite state machine with three primary states:

1. **Active Wall Running**: Player is running along a wall surface
2. **Exiting Wall**: Transitional state preventing immediate re-entry
3. **Inactive**: Normal movement, not wall running

The state transitions are governed by specific conditions and timing mechanisms:

```csharp
if((wallLeft || wallRight) && verticalInput > 0 && AboveGround() && !exitingWall)
{
    if (!pm.wallrunning)
        StartWallRun();

    if (wallRunTimer > 0)
        wallRunTimer -= Time.deltaTime;

    if(wallRunTimer <= 0 && pm.wallrunning)
    {
        exitingWall = true;
        exitWallTimer = exitWallTime;
    }
}
```

The timer mechanism implements time-based state control, where the maximum wall run duration is enforced through countdown logic. The mathematical relationship is:

**t_remaining = t_max - Σ(Δt)**

Where t_max is `maxWallRunTime` and Σ(Δt) represents the accumulated frame time deltas.

---

Having detailed the mechanics of wall running with its surface adhesion and momentum-based movement, we now shift focus to another vertical movement system that handles discrete attachment points — ledge grabbing.

### 4.2 Ledge Grabbing System Implementation

#### 4.2.1 Collision Detection and Spherecasting

##### Figure 4.1: Raycast vs Spherecast Detection Comparison

<img src="ledgecollision.png" alt="Raycast Detection Limitations" width="300"/>

*Figure 4.1: Comparison showing how raycasts only detect colliders at specific points, while spherecasts provide volumetric detection for more reliable wall and ledge detection.*

The ledge grabbing system employs spherecasting for robust edge detection:

```csharp
bool ledgeDetected = Physics.SphereCast(transform.position, ledgeSphereCastRadius, cam.forward, out ledgeHit, ledgeDetectionLength, whatIsLedge);
```

**Detailed Code Analysis:**
- Spherecast provides volumetric detection using swept sphere collision
- `ledgeSphereCastRadius` defines detection sphere size (typically 0.2-0.5 units)
- `cam.forward` direction ensures detection aligns with player's view for intuitive grabbing
- `out ledgeHit` stores collision information for distance validation and positioning
- More reliable than raycasting as it accounts for player movement imprecision
- `whatIsLedge` LayerMask filters detection to ledge objects only

##### Figure 4.2: Unity Layer Mask Configuration

<img src="layers.png" alt="Unity Layer System" width="300"/>

*Figure 4.2: Unity's layer mask system configuration showing how different collision layers are organized for selective detection between walls, ground, ledges, and player objects. The ledge layer and player layer collision is unchecked to prevent the player colliding with ledge.*

##### Figure 4.3: Spherecast Detection System

<img src="raycastdetectledge.png" alt="Spherecast Detection" width="300"/>

*Figure 4.3: Spherecast detection algorithm showing detection radius, forward projection distance, and collision point identification for ledge grabbing validation.*

The spherecast creates a swept sphere collision detection with path defined by:
**P(t) = P_start + t × cam.forward × ledgeDetectionLength**

##### Figure 4.4: Ledge Detection Sequence

<img src="viewledge.png" alt="Ledge Detection Approach" width="300"/>

*Figure 4.4: Player approaching a ledge showing the spherecast detection zone and the transition from approach to grab state.*

##### Figure 4.5: Ledge Grab Execution

<img src="pushtoledge.png" alt="Ledge Grab Movement" width="300"/>

*Figure 4.5: Demonstration of the player character moving toward the detected ledge with directional force application.*

##### Figure 4.6: Rigidbody Physics State Control

<img src="freezonledge.png" alt="Freeze Rigidbody State" width="300"/>

*Figure 4.6: Visualization of the rigidbody freeze state during ledge holding, showing how physics properties are manipulated to maintain ledge attachment.*

#### 4.2.2 Distance Calculation and Grab Validation

The system implements precise distance validation to determine grab eligibility:

```csharp
float distanceToLedge = Vector3.Distance(transform.position, ledgeHit.transform.position);

if (ledgeHit.transform == lastLedge) return;

if (distanceToLedge < maxLedgeGrabDistance && !holding) EnterLedgeHold();
```

**Detailed Code Analysis:**
- `Vector3.Distance()` calculates 3D Euclidean distance between player and ledge positions
- Object reference comparison `ledgeHit.transform == lastLedge` prevents immediate re-grabbing
- Dual validation: proximity check AND not currently holding state
- `maxLedgeGrabDistance` prevents unrealistic long-range grabs (typically 2.0-4.0 units)
- Early returns optimize performance by skipping unnecessary calculations

The distance calculation utilizes the Euclidean distance formula in 3D space:

**d = √[(x₂-x₁)² + (y₂-y₁)² + (z₂-z₁)²]**

This is implemented through Unity's `Vector3.Distance()` method, which calculates the magnitude of the vector difference between two positions. The comparison against `maxLedgeGrabDistance` ensures that ledge grabbing only occurs within a reasonable proximity range, preventing unrealistic long-distance grabs.

The `lastLedge` comparison prevents immediate re-grabbing of the same ledge, implementing a cooldown mechanism through object reference tracking rather than time-based delays.

#### 4.2.3 Physics State Manipulation During Ledge Hold

When entering a ledge hold state, the system must carefully manipulate physics properties to create the grabbing effect:

```csharp
private void EnterLedgeHold()
{
    holding = true;

    pm.unlimited = true;
    pm.restricted = true;

    currLedge = ledgeHit.transform;
    lastLedge = ledgeHit.transform;

    rb.useGravity = false;
    rb.linearVelocity = Vector3.zero;
}
```

**Detailed Code Analysis:**
- `holding = true` activates primary ledge grab state flag
- `pm.unlimited = true` allows unlimited approach speed during grab sequence
- `pm.restricted = true` disables base movement system to prevent force conflicts
- `currLedge` and `lastLedge` references track current and previous ledge objects
- `rb.useGravity = false` disables gravity to prevent falling during attachment
- `rb.linearVelocity = Vector3.zero` immediately stops all motion for clean grab execution

The physics manipulation involves several key operations for seamless ledge attachment state coordination.

The position adjustment system implements proportional control through force application targeting the ledge position.

#### 4.2.5 Ledge Jump Implementation

The ledge jump system provides explosive movement away from the ledge using delayed force application:

```csharp
private void LedgeJump()
{
    ExitLedgeHold();
    Invoke(nameof(DelayedJumpForce), 0.05f);
}

private void DelayedJumpForce()
{
    Vector3 forceToAdd = cam.forward * ledgeJumpForwardForce + orientation.up * ledgeJumpUpwardForce;
    rb.linearVelocity = Vector3.zero;
    rb.AddForce(forceToAdd, ForceMode.Impulse);
}
```

**Detailed Code Analysis:**

**LedgeJump() Method:**
- `ExitLedgeHold()` immediately calls the ledge exit routine to clean up the hold state
- Resets physics properties, clears state flags, and re-enables gravity
- `Invoke(nameof(DelayedJumpForce), 0.05f)` schedules delayed execution of jump force
- `nameof(DelayedJumpForce)` gets the method name as a string for the Invoke call
- `0.05f` creates a 50-millisecond delay before applying jump forces
- This delay ensures ledge hold state is completely exited before force application
- Prevents conflicts between state transitions and physics manipulations

**DelayedJumpForce() Method:**
- 50-millisecond delay ensures clean state transition before force application
- Composite force combines camera-directed forward movement with consistent upward lift
- `cam.forward * ledgeJumpForwardForce` provides directional jumping based on player view
- `orientation.up * ledgeJumpUpwardForce` ensures upward force regardless of camera angle
- Velocity reset removes residual motion before explosive jump execution

The delayed force application addresses timing issues in physics state transitions, ensuring clean separation between ledge holding and jump states.

The jump force combines two components for directional explosive movement away from the ledge surface.

#### 4.2.6 State Transition and Exit Conditions

The ledge grabbing system implements multiple exit conditions and state management:

```csharp
private void SubStateMachine()
{
    float horizontalInput = Input.GetAxisRaw("Horizontal");
    float verticalInput = Input.GetAxisRaw("Vertical");
    bool anyInputKeyPressed = horizontalInput != 0 || verticalInput != 0;

    // SubState 1 - Holding onto ledge
    if (holding)
    {
        FreezeRigidbodyOnLedge();
        timeOnLedge += Time.deltaTime;

        if (timeOnLedge > minTimeOnLedge && anyInputKeyPressed) ExitLedgeHold();
        if (Input.GetKeyDown(jumpKey)) LedgeJump();
    }
}
```

The state machine implements time-based minimum hold duration combined with input-based exit conditions:

```csharp
// SubState 1 - Holding onto ledge
if (holding)
{
    FreezeRigidbodyOnLedge();
    timeOnLedge += Time.deltaTime;

    if (timeOnLedge > minTimeOnLedge && anyInputKeyPressed) ExitLedgeHold();
    if (Input.GetKeyDown(jumpKey)) LedgeJump();
}
```

**Detailed Code Analysis:**
- `anyInputKeyPressed` aggregates all movement input into single boolean check
- Time accumulation: `timeOnLedge += Time.deltaTime` tracks hold duration
- Dual exit condition: minimum time elapsed AND input detected prevents accidental release
- Jump input provides immediate alternative exit method
- `FreezeRigidbodyOnLedge()` handles positioning and physics state during hold

### 4.3 Mathematical Foundations and Physics Principles

#### 4.3.1 Vector Mathematics in 3D Movement

Both movement systems utilize fundamental vector operations:

**Vector Addition for Force Composition:**
```csharp
Vector3 forceToAdd = cam.forward * ledgeJumpForwardForce + orientation.up * ledgeJumpUpwardForce;
```
This implements the mathematical principle: **v_result = v₁ + v₂ = (x₁+x₂, y₁+y₂, z₁+z₂)**

**Vector Normalization for Direction:**
```csharp
rb.AddForce(directionToLedge.normalized * moveToLedgeSpeed * 1000f * Time.deltaTime);
```
Normalization converts any vector to unit length: **v_normalized = v / |v| = v / √(x² + y² + z²)**

**Cross Product for Perpendicular Calculations:**
```csharp
Vector3 wallForward = Vector3.Cross(wallNormal, transform.up);
```
The cross product formula in 3D: **A × B = (AyBz - AzBy, AzBx - AxBz, AxBy - AyBx)**
This creates a vector perpendicular to both the wall normal and world up, lying in the horizontal plane and tangent to the wall surface.

**Distance Calculations:**
```csharp
float distanceToLedge = Vector3.Distance(transform.position, currLedge.position);
```
Implements the Euclidean distance formula: **d = √[(x₂-x₁)² + (y₂-y₁)² + (z₂-z₁)²]**

#### 4.3.2 Force Dynamics and Newton's Laws

The implementations demonstrate practical application of Newton's laws:

**First Law (Inertia) - Objects at rest stay at rest, objects in motion stay in motion unless acted upon by forces:**
```csharp
// Momentum cancellation to overcome inertia
rb.linearVelocity = Vector3.zero;
```

**Second Law (F = ma) - Force equals mass times acceleration:**
```csharp
// Force accumulation where multiple forces sum vectorially
rb.AddForce(wallForward * wallRunForce, ForceMode.Force);
rb.AddForce(-wallNormal * 100, ForceMode.Force);
rb.AddForce(transform.up * gravityCounterForce, ForceMode.Force);
```
Total force relationship: **F_total = F_forward + F_adhesion + F_gravity_counter + F_gravity_natural**

**Third Law (Action-Reaction) - For every action, there's an equal and opposite reaction:**
The wall running system applies forces toward walls to maintain contact, while walls provide implicit reaction forces preventing penetration.

**Impulse-Momentum Theorem:**
```csharp
// Impulse application for explosive movements
rb.AddForce(forceToApply, ForceMode.Impulse);
```
Implements: **J = Δp = m × Δv** where J is impulse, Δp is change in momentum, m is mass, and Δv is change in velocity.

Unity's physics engine handles mass-acceleration relationships automatically through the `AddForce` method implementations.

#### 4.3.3 Collision Detection Mathematics

The collision detection systems implement various geometric algorithms:

**Ray-Line Intersection for Wall Detection:**
```csharp
wallRight = Physics.Raycast(transform.position, orientation.right, out rightWallhit, wallCheckDistance, whatIsWall);
```
Calculates intersection between ray and wall surfaces for binary presence detection.

**Ray-Sphere Intersection for Ledge Detection:**
```csharp
bool ledgeDetected = Physics.SphereCast(transform.position, ledgeSphereCastRadius, cam.forward, out ledgeHit, ledgeDetectionLength, whatIsLedge);
```
Solves for intersection where: Given ray R(t) = O + tD and sphere center C with radius r, find intersection where **|R(t) - C|² = r²**

**Point-to-Point Distance for Proximity Testing:**
Used extensively for grab eligibility and positioning validation using the Euclidean metric.

#### 4.3.4 Time Integration and Frame Rate Independence

Both systems implement frame rate independence through proper time integration:

```csharp
timeOnLedge += Time.deltaTime;
wallRunTimer -= Time.deltaTime;
rb.AddForce(directionToLedge.normalized * moveToLedgeSpeed * 1000f * Time.deltaTime);
```

**Time-based Accumulation:**
The integration follows the principle: **value_new = value_old + rate × Δt**
Where Δt is the frame time delta, ensuring linear accumulation or decay over real time rather than frame count.

**Force Application Scaling:**
Using `Time.deltaTime` in force calculations ensures consistent behavior regardless of frame rate by scaling applied forces to match actual elapsed time.

---

With the mathematical and physical principles established, we now examine how these individual movement systems integrate within a unified movement architecture that coordinates state transitions and prevents conflicts between different movement modes.

### 4.4 System Integration and State Management

#### 4.4.1 Central Movement State Architecture

The `PlayerMovementAdvanced` script serves as the central hub for all movement behaviors, implementing a comprehensive finite state machine. For the context of wall running and ledge grabbing integration, the relevant states are:

```csharp
public enum MovementState
{
    freeze,
    unlimited,
    walking,
    sprinting,
    wallrunning,
    air
}
```

This enumeration provides the core states necessary for integrating advanced movement mechanics with base movement behaviors. The state management follows a hierarchical priority system implemented in the `StateHandler()` method.

#### 4.4.2 State Priority Hierarchy and Control Flow

The base movement system implements a priority-based state selection mechanism relevant to wall running and ledge grabbing:

```csharp
private void StateHandler()
{
    // Mode - Freeze (Highest Priority - Used by Ledge Grabbing)
    if (freeze)
    {
        state = MovementState.freeze;
        rb.linearVelocity = Vector3.zero;
        desiredMoveSpeed = 0f;
    }
    // Mode - Unlimited (Used by Ledge Grabbing for approach)
    else if (unlimited)
    {
        state = MovementState.unlimited;
        desiredMoveSpeed = 999f;
    }
    // Mode - Wallrunning
    else if (wallrunning)
    {
        state = MovementState.wallrunning;
        desiredMoveSpeed = wallrunSpeed;
    }
    // Mode - Sprinting
    else if (grounded && Input.GetKey(sprintKey))
    {
        state = MovementState.sprinting;
        desiredMoveSpeed = sprintSpeed;
    }
    // Mode - Walking
    else if (grounded)
    {
        state = MovementState.walking;
        desiredMoveSpeed = walkSpeed;
    }
    // Mode - Air
    else
    {
        state = MovementState.air;
        if (moveSpeed < airMinSpeed)
            desiredMoveSpeed = airMinSpeed;
    }
}
```

The mathematical representation of this priority system follows:

**state_active = freeze ∨ (¬freeze ∧ unlimited) ∨ (¬freeze ∧ ¬unlimited ∧ wallrunning) ...**

#### 4.4.3 Advanced Movement Integration Patterns

The integration between advanced movement systems and the base movement controller demonstrates sophisticated coordination patterns:

**Ledge Grabbing Integration:**
```csharp
// In LedgeGrabbing.cs
private void EnterLedgeHold()
{
    holding = true;
    pm.unlimited = true;  // Allow unlimited speed during grab approach
    pm.restricted = true; // Prevent base movement calculations
}

private void FreezeRigidbodyOnLedge()
{
    if (!pm.freeze) pm.freeze = true;        // Stop all movement
    if (pm.unlimited) pm.unlimited = false;  // Remove speed override
}
```

**Wall Running Integration:**
```csharp
// In WallRunningAdvanced.cs  
private void StartWallRun()
{
    pm.wallrunning = true; // Set state flag
    // Physics handled by wall running system
}
```

This integration pattern implements **state delegation**, where advanced movement systems can override base movement behavior through boolean flags while maintaining centralized state tracking.

#### 4.4.4 Movement Parameter Coordination

The base movement system provides speed parameters that are relevant to wall running integration:

```csharp
[Header("Movement")]
public float walkSpeed;
public float sprintSpeed;
public float wallrunSpeed;    // Used by wall running system
public float airMinSpeed;
```

The wall running system references these parameters to maintain consistency with the overall movement design:

```csharp
// In PlayerMovementAdvanced.cs StateHandler()
else if (wallrunning)
{
    state = MovementState.wallrunning;
    desiredMoveSpeed = wallrunSpeed;
}
```

This ensures that wall running speeds are balanced with base movement and can be adjusted from a central configuration location.

#### 4.4.5 Movement Restriction and Override System

The base movement system implements a restriction mechanism that allows advanced movement systems to prevent conflicting physics calculations:

```csharp
private void MovePlayer()
{
    if (restricted) return; // Exit early if movement is restricted
    
    // calculate movement direction
    moveDirection = orientation.forward * verticalInput + orientation.right * horizontalInput;
    // ... movement calculations
}
```

The `restricted` flag is used by advanced movement systems to prevent the base movement system from applying conflicting forces:

```csharp
// In LedgeGrabbing.cs
pm.restricted = true;  // Prevent base movement during ledge hold
```

This implements the **override pattern** where specialized systems can completely disable base movement when necessary.

#### 4.4.6 Speed Control and Momentum Management

The base movement system includes sophisticated speed control mechanisms that interact with advanced movement systems:

```csharp
private void SpeedControl()
{
    // limiting speed on slope
    if (OnSlope() && !exitingSlope)
    {
        if (rb.linearVelocity.magnitude > moveSpeed)
            rb.linearVelocity = rb.linearVelocity.normalized * moveSpeed;
    }
    // limiting speed on ground or in air
    else
    {
        Vector3 flatVel = new Vector3(rb.linearVelocity.x, 0f, rb.linearVelocity.z);
        if (flatVel.magnitude > moveSpeed)
        {
            Vector3 limitedVel = flatVel.normalized * moveSpeed;
            rb.linearVelocity = new Vector3(limitedVel.x, rb.linearVelocity.y, limitedVel.z);
        }
    }
}
```

The speed control system implements **velocity clamping** to prevent unrealistic speeds while allowing advanced movement systems to temporarily override these limits through the `unlimited` state.

#### 4.4.7 Smooth State Transitions and Momentum Preservation

The base movement system includes momentum preservation logic for smooth transitions between movement states:

```csharp
bool keepMomentum;
private void StateHandler()
{
    // ... state selection logic
    
    bool desiredMoveSpeedHasChanged = desiredMoveSpeed != lastDesiredMoveSpeed;
    
    if (desiredMoveSpeedHasChanged)
    {
        if (keepMomentum)
        {
            StopAllCoroutines();
            StartCoroutine(SmoothlyLerpMoveSpeed());
        }
        else
        {
            moveSpeed = desiredMoveSpeed;
        }
    }
}

private IEnumerator SmoothlyLerpMoveSpeed()
{
    float time = 0;
    float difference = Mathf.Abs(desiredMoveSpeed - moveSpeed);
    float startValue = moveSpeed;
    
    while (time < difference)
    {
        moveSpeed = Mathf.Lerp(startValue, desiredMoveSpeed, time / difference);
        time += Time.deltaTime * speedIncreaseMultiplier;
        yield return null;
    }
    moveSpeed = desiredMoveSpeed;
}
```

This coroutine-based interpolation system ensures smooth speed transitions when switching between movement states, preventing jarring velocity changes that could disrupt gameplay flow.

#### 4.4.8 Inter-System Communication and Conflict Resolution

The advanced movement systems implement mutual exclusion to prevent conflicting behaviors:

```csharp
// In WallRunningAdvanced.cs
private void WallJump()
{
    if (lg.holding || lg.exitingLedge) return;
    // ... wall jump logic
}
```

This pattern ensures that wall jumping cannot occur during ledge grabbing states, preventing physics conflicts and maintaining realistic movement behavior.

#### 4.4.9 Gravity and Physics State Coordination

The base movement system coordinates gravity settings with advanced movement systems:

```csharp
private void MovePlayer()
{
    // ... movement logic
    
    // turn gravity off while on slope
    if(!wallrunning) rb.useGravity = !OnSlope();
}
```

This coordination ensures that gravity is properly managed across different movement states, with wall running taking precedence over slope-based gravity control.

### 4.5 Complete Movement Architecture Analysis

#### 4.5.1 Base Movement Physics Implementation

The `PlayerMovementAdvanced` script implements the foundational physics calculations that support all movement behaviors. The core movement function demonstrates sophisticated force application based on terrain conditions:

```csharp
private void MovePlayer()
{
    if (restricted) return;

    // calculate movement direction
    moveDirection = orientation.forward * verticalInput + orientation.right * horizontalInput;

    // on slope
    if (OnSlope() && !exitingSlope)
    {
        rb.AddForce(GetSlopeMoveDirection(moveDirection) * moveSpeed * 20f, ForceMode.Force);
        if (rb.linearVelocity.y > 0)
            rb.AddForce(Vector3.down * 80f, ForceMode.Force);
    }
    // on ground
    else if (grounded)
        rb.AddForce(moveDirection.normalized * moveSpeed * 10f, ForceMode.Force);
    // in air
    else if (!grounded)
        rb.AddForce(moveDirection.normalized * moveSpeed * 10f * airMultiplier, ForceMode.Force);

    if(!wallrunning) rb.useGravity = !OnSlope();
}
```

The force application follows terrain-adaptive principles:

**Slope Movement**: Uses projected force vectors to maintain consistent movement along slopes regardless of incline angle.

**Ground Movement**: Applies standard horizontal forces with a force multiplier of 10f.

**Air Movement**: Reduces force effectiveness through the `airMultiplier`, simulating reduced air control.

The mathematical relationship for force application is:

**F_applied = direction_normalized × moveSpeed × multiplier**

Where the multiplier varies based on terrain conditions (20f for slopes, 10f for ground, 10f × airMultiplier for air).

#### 4.5.2 Slope Handling and Terrain Adaptation

The slope handling system demonstrates sophisticated geometric calculations for terrain adaptation:

```csharp
public bool OnSlope()
{
    if (Physics.Raycast(transform.position, Vector3.down, out slopeHit, playerHeight * 0.5f + 0.3f))
    {
        float angle = Vector3.Angle(Vector3.up, slopeHit.normal);
        return angle < maxSlopeAngle && angle != 0;
    }
    return false;
}

public Vector3 GetSlopeMoveDirection(Vector3 direction)
{
    return Vector3.ProjectOnPlane(direction, slopeHit.normal).normalized;
}
```

The slope detection implements angular analysis using the dot product relationship:

**cos(θ) = (V₁ · V₂) / (|V₁| × |V₂|)**

Where θ is the angle between the world up vector and surface normal.

The `GetSlopeMoveDirection` method uses vector projection to calculate movement direction tangent to the slope surface:

**projected_vector = original_vector - (original_vector · normal) × normal**

This ensures that movement input is always applied parallel to the slope surface, preventing the player from "fighting" the terrain geometry.

#### 4.5.3 Air Movement and Jump Mechanics

The jump system implements impulse-based vertical movement with velocity reset for consistent behavior:

```csharp
private void Jump()
{
    exitingSlope = true;
    
    // reset y velocity
    rb.linearVelocity = new Vector3(rb.linearVelocity.x, 0f, rb.linearVelocity.z);
    
    rb.AddForce(transform.up * jumpForce, ForceMode.Impulse);
}
```

The velocity reset ensures consistent jump height regardless of current vertical velocity, implementing the principle:

**v_new = (v_x, 0, v_z) + (0, jumpForce/mass, 0)**

The `exitingSlope` flag prevents slope-based gravity modification during jump execution, ensuring that jumps from slopes behave consistently with flat ground jumps.

Air movement control uses reduced force effectiveness:

```csharp
else if (!grounded)
    rb.AddForce(moveDirection.normalized * moveSpeed * 10f * airMultiplier, ForceMode.Force);
```

The `airMultiplier` typically ranges from 0.1 to 0.4, reducing air control to prevent unrealistic mid-air maneuvering while maintaining some player agency.

#### 4.5.4 Speed Control and Velocity Management

The speed control system implements velocity clamping with terrain-specific logic:

```csharp
private void SpeedControl()
{
    // limiting speed on slope
    if (OnSlope() && !exitingSlope)
    {
        if (rb.linearVelocity.magnitude > moveSpeed)
            rb.linearVelocity = rb.linearVelocity.normalized * moveSpeed;
    }
    // limiting speed on ground or in air
    else
    {
        Vector3 flatVel = new Vector3(rb.linearVelocity.x, 0f, rb.linearVelocity.z);
        
        if (flatVel.magnitude > moveSpeed)
        {
            Vector3 limitedVel = flatVel.normalized * moveSpeed;
            rb.linearVelocity = new Vector3(limitedVel.x, rb.linearVelocity.y, limitedVel.z);
        }
    }
}
```

**Slope Speed Control**: Limits total velocity magnitude, allowing for natural acceleration down slopes while preventing unrealistic speeds.

**Horizontal Speed Control**: Limits only horizontal velocity components, preserving vertical velocity for natural falling and jumping behavior.

The velocity clamping implements the mathematical principle:

**v_clamped = (v / |v|) × v_max** when **|v| > v_max**

#### 4.5.5 Dynamic Speed Adjustment and State Transitions

The movement system includes sophisticated speed interpolation for smooth state transitions:

```csharp
bool desiredMoveSpeedHasChanged = desiredMoveSpeed != lastDesiredMoveSpeed;

if (desiredMoveSpeedHasChanged)
{
    if (keepMomentum)
    {
        StopAllCoroutines();
        StartCoroutine(SmoothlyLerpMoveSpeed());
    }
    else
    {
        moveSpeed = desiredMoveSpeed;
    }
}
```

The `SmoothlyLerpMoveSpeed()` coroutine implements time-based interpolation with slope acceleration bonuses:

```csharp
private IEnumerator SmoothlyLerpMoveSpeed()
{
    float time = 0;
    float difference = Mathf.Abs(desiredMoveSpeed - moveSpeed);
    float startValue = moveSpeed;

    while (time < difference)
    {
        moveSpeed = Mathf.Lerp(startValue, desiredMoveSpeed, time / difference);

        if (OnSlope())
        {
            float slopeAngle = Vector3.Angle(Vector3.up, slopeHit.normal);
            float slopeAngleIncrease = 1 + (slopeAngle / 90f);
            time += Time.deltaTime * speedIncreaseMultiplier * slopeIncreaseMultiplier * slopeAngleIncrease;
        }
        else
            time += Time.deltaTime * speedIncreaseMultiplier;

        yield return null;
    }
    moveSpeed = desiredMoveSpeed;
}
```

The slope angle multiplier implements realistic acceleration bonuses on steep terrain:

**acceleration_bonus = 1 + (slope_angle / 90°)**

This provides faster speed transitions when moving downhill, simulating gravitational assistance.

#### 4.5.6 Ground Detection and Physics State Management

The ground detection system uses raycast-based terrain analysis:

```csharp
// In Update()
grounded = Physics.Raycast(transform.position, Vector3.down, playerHeight * 0.5f + 0.2f, whatIsGround);

// handle drag
if (grounded)
    rb.linearDamping = groundDrag;
else
    rb.linearDamping = 0;
```

The ground detection implements a safety margin (0.2f) beyond the player's physical bounds to ensure reliable ground state detection even during minor physics fluctuations.

The drag system provides realistic friction simulation:
- **Ground**: Applies `groundDrag` to simulate surface friction
- **Air**: Removes drag for realistic ballistic motion

#### 4.5.7 Integration with Advanced Movement Systems

The base movement system provides multiple integration points for advanced movement mechanics:

**State Flags**: Boolean flags (`wallrunning`, `climbing`, `vaulting`) allow advanced systems to override base behavior.

**Control Flags**: The `freeze`, `unlimited`, and `restricted` flags provide fine-grained control over movement behavior during advanced maneuvers.

**Speed Parameters**: Dedicated speed values for each movement mode ensure consistent performance tuning across all systems.

This architecture demonstrates the **Strategy Pattern** from software engineering, where different movement behaviors can be swapped in and out while maintaining a consistent interface and base functionality.

## 5. Discussion

### 5.1 Implementation Effectiveness

The analyzed implementations demonstrate sophisticated applications of physics principles to create believable and responsive advanced movement mechanics. The wall running system successfully creates the illusion of defying gravity while maintaining physical plausibility through careful force balance and surface adhesion simulation. The mathematical foundation built on vector operations and force dynamics provides both realistic behavior and responsive player control.

The ledge grabbing system showcases effective collision detection and position control algorithms. The use of spherecasting for detection provides robust edge finding that accounts for player movement imprecision, while the position interpolation system ensures smooth visual alignment with ledge positions. The state management prevents common issues such as infinite grabbing loops and conflicting movement states.

### 5.2 Mathematical Sophistication

Both systems demonstrate appropriate mathematical complexity for their intended purposes. The wall running system's use of cross products for surface tangent calculations shows sophisticated understanding of 3D vector mathematics. The force combination approaches in both systems properly implement vector addition principles to create complex movement behaviors from simple force components.

The collision detection algorithms employed represent efficient solutions to geometric problems. The spherecasting approach in ledge detection trades some computational cost for improved reliability, while the raycasting in wall detection provides efficient binary surface presence detection.

### 5.3 Performance Considerations

The implementations show awareness of performance implications through efficient algorithm choices. The use of Unity's built-in Physics.Raycast and Physics.SphereCast methods leverages optimized native implementations rather than custom geometric calculations. The state management systems minimize unnecessary calculations by performing expensive operations only when relevant states are active.

The frame rate independence achieved through proper Time.deltaTime usage ensures consistent behavior across different hardware configurations, critical for maintaining gameplay integrity in distributed environments.

### 5.4 Integration Architecture

The integration between wall running and ledge grabbing systems demonstrates thoughtful architecture design. The mutual exclusion patterns prevent conflicting behaviors while allowing appropriate transitions between movement modes. The centralized player movement state coordination ensures that base movement behaviors adapt appropriately to advanced movement states.

However, the integration could benefit from more sophisticated transition handling between movement modes. Currently, the systems primarily use boolean flags and timer-based cooldowns, which could be enhanced with more nuanced transition criteria and smoother interpolation between movement states.

### 5.5 Extensibility and Modularity

The modular design of both systems allows for independent tuning and modification. The extensive use of public parameters exposed in the Unity inspector enables designers to adjust behavior without code modifications. This separation of implementation logic from configuration parameters represents good software engineering practice for game development.

The state machine architectures provide clear extension points for additional movement behaviors. New states can be integrated into existing systems without major structural changes, demonstrating forward-thinking design considerations.

### 5.6 Physical Accuracy vs. Gameplay Requirements

Both implementations strike appropriate balances between physical accuracy and gameplay requirements. While neither system attempts to simulate real-world physics with complete accuracy, they maintain sufficient plausibility to preserve player immersion while prioritizing responsive controls and enjoyable gameplay.

The wall running system's partial gravity negation and surface adhesion forces would be impossible in reality but create an engaging gameplay experience. Similarly, the ledge grabbing system's position snapping and hold mechanics prioritize player convenience over strict physical simulation.

### 5.8 Base Movement System Integration Excellence

The integration of the `PlayerMovementAdvanced` script with the specialized movement systems demonstrates exceptional software architecture principles. The centralized state management through enumerations, combined with the priority-based state selection system, creates a robust foundation that can accommodate additional movement modes without structural modifications.

The speed control system's terrain-adaptive behavior showcases sophisticated understanding of physics simulation requirements. The differentiation between slope, ground, and air movement, each with appropriate force multipliers and velocity constraints, creates realistic movement feel while maintaining gameplay responsiveness.

The coroutine-based speed interpolation system represents advanced implementation of smooth state transitions. The inclusion of slope-angle-based acceleration bonuses demonstrates attention to physical realism while enhancing gameplay dynamics. This level of detail in transition handling significantly improves the overall player experience quality.

### 5.9 Comprehensive System Architecture

The complete movement architecture reveals a well-designed hierarchy where the base system provides foundational physics calculations while specialized systems handle advanced behaviors. The restriction and override mechanisms (`freeze`, `unlimited`, `restricted` flags) provide clean separation of concerns while maintaining centralized control.

The mutual exclusion patterns between advanced movement systems prevent edge cases and impossible state combinations that could break physics simulation or create exploitable behaviors. The integration demonstrates understanding of both technical requirements and gameplay design considerations.

### 5.10 Performance and Scalability Analysis

The architecture demonstrates excellent performance characteristics through efficient algorithm choices and appropriate use of Unity's physics systems. The raycast-based detection methods provide O(1) detection complexity per frame, while the state management systems use simple boolean logic for decision making.

The coroutine-based speed interpolation prevents frame rate hitches that could occur with complex mathematical calculations, distributing computational load across multiple frames. This approach maintains smooth gameplay while providing sophisticated movement behavior.

The modular architecture supports easy extension with additional movement modes, demonstrating forward-thinking design that can accommodate future gameplay requirements without major refactoring.

## 6. Conclusion

This thesis has presented a comprehensive analysis of advanced movement mechanics implementation in 3D game environments, specifically examining wall running and ledge grabbing systems. Through detailed code analysis and mathematical examination, the research demonstrates how theoretical physics principles can be effectively translated into functional game mechanics that balance realism with gameplay requirements.

### 6.1 Key Findings

The analysis reveals several critical insights into advanced movement system implementation:

**Mathematical Foundation**: Both systems rely heavily on vector mathematics, particularly normalization, cross products, and distance calculations. The proper application of these mathematical principles is essential for creating believable and responsive movement behaviors.

**Force Dynamics**: The effective use of Newton's laws through Unity's physics engine demonstrates how classical mechanics principles can be applied in game contexts. The combination of multiple force vectors to achieve complex behaviors showcases sophisticated understanding of force dynamics.

**State Management**: The finite state machine architectures employed in both systems provide robust frameworks for managing complex behavioral transitions while preventing impossible state combinations.

**Detection Algorithms**: The choice of collision detection methods significantly impacts system reliability. Spherecasting for ledge detection provides more robust results than simple raycasting, while directional raycasting for wall detection offers efficient binary surface presence detection.

### 6.2 Theoretical Contributions

This research contributes to the understanding of physics-based game mechanics in several ways:

**Implementation Patterns**: The analysis identifies common implementation patterns for advanced movement systems, including force combination strategies, state management architectures, and integration approaches.

**Mathematical Applications**: The work demonstrates practical applications of vector mathematics and force dynamics in game development contexts, bridging theoretical understanding with implementation reality.

**System Integration**: The examination of inter-system communication and state coordination provides insights into managing complex, multi-modal movement systems.

### 6.3 Practical Applications

The findings have direct applications for game developers implementing similar movement systems:

**Design Guidelines**: The analysis provides concrete guidance on parameter selection, algorithm choices, and architectural decisions for advanced movement implementations.

**Performance Optimization**: The performance considerations discussed offer strategies for maintaining efficient execution while implementing sophisticated behaviors.

**Integration Strategies**: The integration patterns demonstrated provide blueprints for coordinating multiple movement systems without conflicts.

### 6.4 Technical Excellence

The implementations analyzed demonstrate technical excellence in several areas:

**Code Organization**: Both systems exhibit clear separation of concerns, with distinct methods handling detection, state management, and force application.

**Parameter Exposure**: Extensive use of public parameters enables designer control without requiring code modifications, demonstrating good software engineering practices.

**Error Handling**: The implementations include appropriate safeguards and fallback behaviors to maintain system stability under edge conditions.

### 6.5 Future Research Directions

This analysis suggests several areas for future investigation:

**Machine Learning Integration**: Advanced movement systems could potentially benefit from machine learning approaches for parameter optimization and behavior prediction.

**Procedural Animation**: Integration with procedural animation systems could enhance visual quality and reduce animation asset requirements.

**Multi-Player Synchronization**: Investigation of network synchronization challenges for advanced movement systems in multiplayer environments.

**Accessibility Considerations**: Research into making advanced movement mechanics accessible to players with different motor abilities.

### 6.6 Industry Impact

The principles and patterns identified in this research have broader implications for the game development industry:

**Development Efficiency**: Understanding these implementation patterns can reduce development time for similar systems.

**Quality Standards**: The analysis provides benchmarks for technical quality in advanced movement system implementation.

**Educational Value**: The detailed technical analysis serves as educational material for developers learning to implement physics-based movement systems.

### 6.7 Limitations and Considerations

While this research provides valuable insights, certain limitations should be acknowledged:

**Engine Specificity**: The analysis focuses on Unity-specific implementations, which may not directly translate to other game engines.

**Performance Context**: The performance analysis is based on desktop gaming contexts and may not apply to mobile or web-based implementations.

**User Experience Scope**: While technical implementation is thoroughly examined, broader user experience considerations such as accessibility and player skill requirements are not deeply explored.

### 6.8 Synthesis of Findings

The comprehensive analysis of both movement systems reveals a sophisticated understanding of how to bridge theoretical physics with practical game development requirements. The wall running system demonstrates masterful application of vector mathematics and force dynamics to create believable surface adhesion behaviors, while the ledge grabbing system showcases robust collision detection and smooth state transition management.

The mathematical foundations underlying both systems—vector operations, force dynamics, collision detection algorithms, and state management—represent core competencies required for advanced game physics implementation. The successful integration of these mathematical principles with Unity's physics engine demonstrates how theoretical knowledge translates into functional gameplay mechanics.

### 6.9 Final Assessment

The implementations analyzed in this thesis represent high-quality examples of advanced movement system development. They successfully balance multiple competing requirements: physical plausibility, responsive controls, performance efficiency, and maintainable code architecture. The mathematical sophistication demonstrated in vector calculations, force applications, and collision detection algorithms provides a solid foundation for creating engaging and reliable gameplay experiences.

The modular architecture and extensive parameterization enable both technical flexibility and designer control, essential characteristics for production game development. The careful attention to state management and system integration prevents common failure modes while providing smooth player experiences.

This research contributes significantly to the understanding of physics-based movement implementation, providing both theoretical insights and practical guidance for developers working on similar systems. The detailed analysis of mathematical principles, algorithmic choices, and integration patterns offers valuable resources for the game development community.

The work demonstrates that sophisticated movement mechanics can be achieved through systematic application of fundamental physics and mathematics principles, combined with thoughtful software architecture and careful attention to player experience requirements. This synthesis of theoretical understanding and practical implementation serves as a model for advanced game physics development.

## 7. References

### Primary Sources

Unity Technologies. (2023). *Unity Physics Documentation*. Unity Manual 2022.3 LTS. Retrieved from https://docs.unity3d.com/Manual/Physics.html

Unity Technologies. (2023). *Rigidbody Component Reference*. Unity Scripting API 2022.3 LTS. Retrieved from https://docs.unity3d.com/ScriptReference/Rigidbody.html

Unity Technologies. (2023). *Physics.Raycast Documentation*. Unity Scripting API 2022.3 LTS. Retrieved from https://docs.unity3d.com/ScriptReference/Physics.Raycast.html

### Mathematical and Physics References

Halliday, D., Resnick, R., & Walker, J. (2018). *Fundamentals of Physics* (11th ed.). John Wiley & Sons.

Stewart, J. (2020). *Calculus: Early Transcendentals* (9th ed.). Cengage Learning.

Anton, H., & Rorres, C. (2019). *Elementary Linear Algebra: Applications Version* (12th ed.). John Wiley & Sons.

### Online Sources

YouTube. (2025). *[Ledge Climbing System]*. Retrieved from https://www.youtube.com/watch?v=72b4P3AztH4

YouTube. (2025). *[Wall running]*. Retrieved from https://www.youtube.com/watch?v=gNt9wBOrQO4 *[wall Jumping]*https://www.youtube.com/watch?v=WfW0k5qENxM

Anthropic. (2025). *Claude AI – Conversational Assistance*. Retrieved from https://claude.ai

---

## Appendices

### Appendix A: Complete Code Implementations

#### A.1 WallRunningAdvanced.cs - Complete Implementation

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class WallRunningAdvanced : MonoBehaviour
{
    [Header("Wallrunning")]
    public LayerMask whatIsWall;
    public LayerMask whatIsGround;
    public float wallRunForce;
    public float wallJumpUpForce;
    public float wallJumpSideForce;
    public float wallClimbSpeed;
    public float maxWallRunTime;
    private float wallRunTimer;

    [Header("Input")]
    public KeyCode jumpKey = KeyCode.Space;
    public KeyCode upwardsRunKey = KeyCode.LeftShift;
    public KeyCode downwardsRunKey = KeyCode.LeftControl;
    private bool upwardsRunning;
    private bool downwardsRunning;
    private float horizontalInput;
    private float verticalInput;

    [Header("Detection")]
    public float wallCheckDistance;
    public float minJumpHeight;
    private RaycastHit leftWallhit;
    private RaycastHit rightWallhit;
    private bool wallLeft;
    private bool wallRight;

    [Header("Exiting")]
    private bool exitingWall;
    public float exitWallTime;
    private float exitWallTimer;

    [Header("Gravity")]
    public bool useGravity;
    public float gravityCounterForce;

    [Header("References")]
    public Transform orientation;
    public PlayerCam cam;
    private PlayerMovementAdvanced pm;
    private LedgeGrabbing lg;
    private Rigidbody rb;

    private void Start()
    {
        rb = GetComponent<Rigidbody>();
        pm = GetComponent<PlayerMovementAdvanced>();
        lg = GetComponent<LedgeGrabbing>();
    }

    private void Update()
    {
        CheckForWall();
        StateMachine();
    }

    private void FixedUpdate()
    {
        if (pm.wallrunning)
            WallRunningMovement();
    }

    private void CheckForWall()
    {
        wallRight = Physics.Raycast(transform.position, orientation.right, out rightWallhit, wallCheckDistance, whatIsWall);
        wallLeft = Physics.Raycast(transform.position, -orientation.right, out leftWallhit, wallCheckDistance, whatIsWall);
    }

    private bool AboveGround()
    {
        return !Physics.Raycast(transform.position, Vector3.down, minJumpHeight, whatIsGround);
    }

    private void StateMachine()
    {
        // Getting Inputs
        horizontalInput = Input.GetAxisRaw("Horizontal");
        verticalInput = Input.GetAxisRaw("Vertical");

        upwardsRunning = Input.GetKey(upwardsRunKey);
        downwardsRunning = Input.GetKey(downwardsRunKey);

        // State 1 - Wallrunning
        if((wallLeft || wallRight) && verticalInput > 0 && AboveGround() && !exitingWall)
        {
            if (!pm.wallrunning)
                StartWallRun();

            // wallrun timer
            if (wallRunTimer > 0)
                wallRunTimer -= Time.deltaTime;

            if(wallRunTimer <= 0 && pm.wallrunning)
            {
                exitingWall = true;
                exitWallTimer = exitWallTime;
            }

            // wall jump
            if (Input.GetKeyDown(jumpKey)) WallJump();
        }

        // State 2 - Exiting
        else if (exitingWall)
        {
            if (pm.wallrunning)
                StopWallRun();

            if (exitWallTimer > 0)
                exitWallTimer -= Time.deltaTime;

            if (exitWallTimer <= 0)
                exitingWall = false;
        }

        // State 3 - None
        else
        {
            if (pm.wallrunning)
                StopWallRun();
        }
    }

    private void StartWallRun()
    {
        pm.wallrunning = true;

        wallRunTimer = maxWallRunTime;

        rb.linearVelocity = new Vector3(rb.linearVelocity.x, 0f, rb.linearVelocity.z);

        // apply camera effects
        cam.DoFov(90f);
        if (wallLeft) cam.DoTilt(-5f);
        if (wallRight) cam.DoTilt(5f);
    }

    private void WallRunningMovement()
    {
        rb.useGravity = useGravity;

        Vector3 wallNormal = wallRight ? rightWallhit.normal : leftWallhit.normal;

        Vector3 wallForward = Vector3.Cross(wallNormal, transform.up);

        if ((orientation.forward - wallForward).magnitude > (orientation.forward - -wallForward).magnitude)
            wallForward = -wallForward;

        // forward force
        rb.AddForce(wallForward * wallRunForce, ForceMode.Force);

        // upwards/downwards force
        if (upwardsRunning)
            rb.linearVelocity = new Vector3(rb.linearVelocity.x, wallClimbSpeed, rb.linearVelocity.z);
        if (downwardsRunning)
            rb.linearVelocity = new Vector3(rb.linearVelocity.x, -wallClimbSpeed, rb.linearVelocity.z);

        // push to wall force
        if (!(wallLeft && horizontalInput > 0) && !(wallRight && horizontalInput < 0))
            rb.AddForce(-wallNormal * 100, ForceMode.Force);

        // weaken gravity
        if (useGravity)
            rb.AddForce(transform.up * gravityCounterForce, ForceMode.Force);
    }

    private void StopWallRun()
    {
        pm.wallrunning = false;

        // reset camera effects
        cam.DoFov(80f);
        cam.DoTilt(0f);
    }

    private void WallJump()
    {
        if (lg.holding || lg.exitingLedge) return;

        // enter exiting wall state
        exitingWall = true;
        exitWallTimer = exitWallTime;

        Vector3 wallNormal = wallRight ? rightWallhit.normal : leftWallhit.normal;

        Vector3 forceToApply = transform.up * wallJumpUpForce + wallNormal * wallJumpSideForce;

        // reset y velocity and add force
        rb.linearVelocity = new Vector3(rb.linearVelocity.x, 0f, rb.linearVelocity.z);
        rb.AddForce(forceToApply, ForceMode.Impulse);
    }
}
```

#### A.2 LedgeGrabbing.cs - Complete Implementation

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class LedgeGrabbing : MonoBehaviour
{
    [Header("References")]
    public PlayerMovementAdvanced pm;
    public Transform orientation;
    public Transform cam;
    public Rigidbody rb;

    [Header("Ledge Grabbing")]
    public float moveToLedgeSpeed;
    public float maxLedgeGrabDistance;

    public float minTimeOnLedge;
    private float timeOnLedge;

    public bool holding;

    [Header("Ledge Jumping")]
    public KeyCode jumpKey = KeyCode.Space;
    public float ledgeJumpForwardForce;
    public float ledgeJumpUpwardForce;

    [Header("Ledge Detection")]
    public float ledgeDetectionLength;
    public float ledgeSphereCastRadius;
    public LayerMask whatIsLedge;

    private Transform lastLedge;
    private Transform currLedge;

    private RaycastHit ledgeHit;

    [Header("Exiting")]
    public bool exitingLedge;
    public float exitLedgeTime;
    private float exitLedgeTimer;

    private void Update()
    {
        LedgeDetection();
        SubStateMachine();
    }

    private void SubStateMachine()
    {
        float horizontalInput = Input.GetAxisRaw("Horizontal");
        float verticalInput = Input.GetAxisRaw("Vertical");
        bool anyInputKeyPressed = horizontalInput != 0 || verticalInput != 0;

        // SubState 1 - Holding onto ledge
        if (holding)
        {
            FreezeRigidbodyOnLedge();

            timeOnLedge += Time.deltaTime;

            if (timeOnLedge > minTimeOnLedge && anyInputKeyPressed) ExitLedgeHold();

            if (Input.GetKeyDown(jumpKey)) LedgeJump();
        }

        // Substate 2 - Exiting Ledge
        else if (exitingLedge)
        {
            if (exitLedgeTimer > 0) exitLedgeTimer -= Time.deltaTime;
            else exitingLedge = false;
        }
    }

    private void LedgeDetection()
    {
        bool ledgeDetected = Physics.SphereCast(transform.position, ledgeSphereCastRadius, cam.forward, out ledgeHit, ledgeDetectionLength, whatIsLedge);

        if (!ledgeDetected) return;

        float distanceToLedge = Vector3.Distance(transform.position, ledgeHit.transform.position);

        if (ledgeHit.transform == lastLedge) return;

        if (distanceToLedge < maxLedgeGrabDistance && !holding) EnterLedgeHold();
    }

    private void LedgeJump()
    {
        ExitLedgeHold();

        Invoke(nameof(DelayedJumpForce), 0.05f);
    }

    private void DelayedJumpForce()
    {
        Vector3 forceToAdd = cam.forward * ledgeJumpForwardForce + orientation.up * ledgeJumpUpwardForce;
        rb.linearVelocity = Vector3.zero;
        rb.AddForce(forceToAdd, ForceMode.Impulse);
    }

    private void EnterLedgeHold()
    {
        holding = true;

        pm.unlimited = true;
        pm.restricted = true;

        currLedge = ledgeHit.transform;
        lastLedge = ledgeHit.transform;

        rb.useGravity = false;
        rb.linearVelocity = Vector3.zero;
    }

    private void FreezeRigidbodyOnLedge()
    {
        rb.useGravity = false;

        Vector3 directionToLedge = currLedge.position - transform.position;
        float distanceToLedge = Vector3.Distance(transform.position, currLedge.position);

        // Move player towards ledge
        if(distanceToLedge > 1f)
        {
            if(rb.linearVelocity.magnitude < moveToLedgeSpeed)
                rb.AddForce(directionToLedge.normalized * moveToLedgeSpeed * 1000f * Time.deltaTime);
        }

        // Hold onto ledge
        else
        {
            if (!pm.freeze) pm.freeze = true;
            if (pm.unlimited) pm.unlimited = false;
        }

        // Exiting if something goes wrong
        if (distanceToLedge > maxLedgeGrabDistance) ExitLedgeHold();
    }

    private void ExitLedgeHold()
    {
        exitingLedge = true;
        exitLedgeTimer = exitLedgeTime;

        holding = false;
        timeOnLedge = 0f;

        pm.restricted = false;
        pm.freeze = false;

        rb.useGravity = true;

        StopAllCoroutines();
        Invoke(nameof(ResetLastLedge), 1f);
    }

    private void ResetLastLedge()
    {
        lastLedge = null;
    }
}
```

### Appendix B: Mathematical Derivations

#### B.1 Cross Product Calculation for Wall Forward Vector

Given:
- Wall normal vector: **n** = (nx, ny, nz)
- World up vector: **u** = (0, 1, 0)

The cross product **wallForward = n × u** is calculated as:

**wallForward** = (ny × 0 - nz × 1, nz × 0 - nx × 0, nx × 1 - ny × 0)
                = (-nz, 0, nx)

This results in a vector perpendicular to both the wall normal and world up, lying in the horizontal plane and tangent to the wall surface.

#### B.2 Distance Calculation in 3D Space

For two points P1(x1, y1, z1) and P2(x2, y2, z2), the Euclidean distance is:

**d = √[(x2-x1)² + (y2-y1)² + (z2-z1)²]**

This formula is implemented in Unity's Vector3.Distance() method and used throughout both systems for proximity testing and validation.

#### B.3 Force Vector Composition

When multiple forces are applied to a rigidbody simultaneously:

**F_total = F1 + F2 + F3 + ... + Fn**

Each force vector contributes to the total force according to vector addition principles:

**F_total** = (ΣFx, ΣFy, ΣFz)

The resulting acceleration follows Newton's second law:

**a = F_total / m**

Where m is the rigidbody mass.

### Appendix C: Performance Analysis Data

#### C.1 Computational Complexity

**Wall Detection (per frame)**:
- 2 × Physics.Raycast operations: O(1) per cast
- Vector calculations: O(1)
- Total per-frame complexity: O(1)

**Ledge Detection (per frame)**:
- 1 × Physics.SphereCast operation: O(1)
- Distance calculation: O(1)
- Total per-frame complexity: O(1)

**State Management (per frame)**:
- Boolean logic evaluation: O(1)
- Timer updates: O(1)
- Total per-frame complexity: O(1)

#### C.2 Memory Usage Analysis

**Wall Running System**:
- Instance variables: ~100 bytes
- Temporary vectors: ~36 bytes per frame
- RaycastHit structures: ~40 bytes

**Ledge Grabbing System**:
- Instance variables: ~120 bytes
- Temporary vectors: ~24 bytes per frame
- RaycastHit structure: ~20 bytes

Total estimated memory footprint: ~340 bytes per player instance.

### Appendix D: Configuration Parameters Guide

#### D.1 Wall Running Parameters

| Parameter | Recommended Range | Description |
|-----------|-------------------|-------------|
| wallRunForce | 200-800 | Forward propulsion force |
| wallJumpUpForce | 7-15 | Vertical component of wall jump |
| wallJumpSideForce | 7-12 | Horizontal component of wall jump |
| wallClimbSpeed | 3-8 | Vertical climbing velocity |
| maxWallRunTime | 1.5-5.0 | Maximum continuous wall run duration |
| wallCheckDistance | 0.7-1.2 | Wall detection range |
| minJumpHeight | 1.0-2.0 | Minimum height requirement for wall running |
| gravityCounterForce | 400-800 | Upward force to counter gravity |
| wallrunSpeed | 12-20 | Base movement speed during wall running |

#### D.2 Ledge Grabbing Parameters

| Parameter | Recommended Range | Description |
|-----------|-------------------|-------------|
| moveToLedgeSpeed | 10-30 | Speed of movement toward ledge |
| maxLedgeGrabDistance | 2.0-4.0 | Maximum grab detection distance |
| minTimeOnLedge | 0.1-0.5 | Minimum hold duration before release |
| ledgeJumpForwardForce | 8-15 | Forward component of ledge jump |
| ledgeJumpUpwardForce | 15-25 | Upward component of ledge jump |
| ledgeDetectionLength | 0.8-1.5 | Forward detection range |
| ledgeSphereCastRadius | 0.2-0.5 | Detection sphere radius |
| exitLedgeTime | 0.2-1.0 | Cooldown period after ledge exit |

### Appendix E: Troubleshooting Guide

#### E.1 Common Implementation Issues

**Wall Running Not Activating**:
- Verify layer mask settings for `whatIsWall`
- Check wall geometry has appropriate colliders
- Ensure `verticalInput > 0` requirement is met
- Confirm `AboveGround()` returns true

**Ledge Grabbing False Positives**:
- Adjust `ledgeSphereCastRadius` to reduce detection area
- Implement more restrictive validation in `LedgeDetection()`
- Check for conflicting colliders in ledge layer

**System Integration Conflicts**:
- Verify mutual exclusion logic in `WallJump()` method
- Ensure proper state flag management
- Check timer-based cooldown implementations

#### E.2 Performance Optimization Tips

**Reduce Physics Calculations**:
- Implement distance-based activation/deactivation
- Use object pooling for temporary calculation objects
- Cache frequently accessed component references

**Optimize Detection Frequency**:
- Reduce detection frequency for distant players
- Implement level-of-detail systems for movement complexity
- Use coroutines for non-critical timer updates

---

**Word Count: Approximately 15,500 words**
**Estimated Page Count: 31-35 pages (depending on formatting)**

This comprehensive thesis provides detailed analysis of the wall running and ledge grabbing implementations, covering theoretical foundations, mathematical principles, code analysis, and practical considerations for game development. The document serves as both an academic examination of physics-based movement systems and a practical guide for developers implementing similar mechanics.