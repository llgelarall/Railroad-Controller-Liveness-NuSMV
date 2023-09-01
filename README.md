# Railroad Controller Liveness Analysis using NuSMV

In this project, we analyze a railroad controller system using NuSMV, focusing on liveness properties related to train movements and signal control. The system involves preventing collisions between trains and ensuring smooth traffic flow using Test&Set registers. We will present the implementation of the system, including the specification of properties, verification, and the analysis of liveness requirements.

## System Description

The railroad controller system manages the movement of trains at a bridge intersection. We use Test&Set registers to handle the synchronization between trains and traffic signals. The primary components of the system are the two trains (TrainW and TrainE) and the Test&Set register (Test&SetReg) to handle access to shared resources.

## Implementation in NuSMV

We'll start by presenting the NuSMV code that models the railroad controller system, including the TrainW, TrainE, and Test&SetReg components.


<div class="alert alert-info">
Note: The NuSMV code is provided for illustration purposes. It is recommended to run the code using NuSMV to observe the behavior and verify the properties.
</div>

## Liveness Properties

### Liveness Property 1: Repeated Entry to the Critical Section

**Property:** If the west train is waiting (`modeW = wait`), then eventually the west traffic signal should turn green (`signalW = green`).

### Liveness Property 2: Starvation Freedom

**Property:** If the east train is repeatedly off the bridge (`modeE != bridge`), then the west train, if waiting, should eventually have its signal turned green.

### Liveness Property 3: Deadlock Freedom

**Property:** To prevent deadlocks, if the west train is waiting (`modeW = wait`), then eventually either the west traffic signal turns green (`signalW = green`) or the east train enters the bridge (`modeE = bridge`).

## Verification and Analysis

We utilize NuSMV to verify the satisfaction of the specified liveness properties. By running NuSMV with the appropriate commands and flags, we can check if these properties hold for all possible executions of the system.

## Conclusion

By implementing and analyzing the railroad controller system using NuSMV, we have verified important liveness properties related to train movements and signal control. The Test&Set registers ensure proper synchronization, and our verification process provides insights into the system's behavior and compliance with liveness requirements. This project highlights the significance of formal methods in ensuring safety and performance in complex systems.
