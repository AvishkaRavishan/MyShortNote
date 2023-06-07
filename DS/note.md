Describe the 5 steps of Asynchronous communication in a graphical way.
Sides are client and host. there is a RMI registry in host side.
It start with client class to RMI registry.
SomeInterface stub Class / SomeInterface skel Class / Some Server Class / Callback Interface


    Client                                 Host
     Class                                  Side
      |                                        ▲
      |                                        |
      |               Step 1: Connect to        |
      └─────────────────── RMI Registry ────────┘
                          (Find SomeInterface)
                                       ▲
                                       |
                          Step 2: Retrieve SomeInterface
                                       ▼
                          ┌───────────────────────┐
                          │ SomeInterface Stub    │
                          └───────────────────────┘
                                       ▲
                                       |
                 Step 3: Invoke Method on SomeInterface Stub
                                       ▼
             ┌─────────────────────────────────────────┐
             │ SomeInterface Skeleton                   │
             │ (Forward Method Invocation to Server)     │
             └─────────────────────────────────────────┘
                                       ▲
                                       |
             Step 4: Execute Method on Some Server Class
                                       ▼
             ┌─────────────────────────────────────────┐
             │ Some Server Class                         │
             │ (Actual Implementation of SomeInterface)  │
             └─────────────────────────────────────────┘
                                       ▲
                                       |
             Step 5: Use Callback Interface for Asynchronous Communication
                                       |
                                       ▼
