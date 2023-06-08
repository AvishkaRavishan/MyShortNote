Describe the 5 steps of Asynchronous communication in a graphical way.
Sides are client and host. there is a RMI registry in host side.
It start with client class to RMI registry.
SomeInterface stub Class / SomeInterface skel Class / Some Server Class / Callback Interface




    Client                        Host (Server)
+--------------+           +-------------------+
|   Client     |           |    RMI Registry   |
+--------------+           +-------------------+
       |                              |
 1.    |                              |
       |      Lookup RMI registry     |
       +----------------------------->|
       |                              |
 2.    |                              |
       |     Return RMI stub object   |
       |<-----------------------------+
       |                              |
 3.    |                              |
       |   Invoke remote method       |
       +----------------------------->|
       |                              |
 4.    |                              |
       |   Register callback object   |
       +----------------------------->|
       |                              |
 5.    |                              |
       |    Return callback stub      |
       |<-----------------------------+
       |                              |
 6.    |                              |
       |  Callback method invocation |
       +----------------------------->|
       |                              |
       |                              |
















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
                                       
                                       
                                       
                                       
                                       
                                      
                 +------------------------+
                |        Client          |
                +------------------------+
                           |
                           |(1) Lookup
                           |
                +------------------------+
                |      RMI Registry      |
                +------------------------+
                           |
                           |(2) Return stub
                           |
                +------------------------+
                |   SomeInterface stub   |
                +------------------------+
                           |
                           |(3) Remote method call
                           |
                +------------------------+
                |    Some Server Class   |
                +------------------------+
                           |
                           |(4) Callback
                           |
                +------------------------+
                |   Callback Interface   |
                +------------------------+







    Client                        Host (Server)
+--------------+           +-------------------+
|   Client     |           |    RMI Registry   |
+--------------+           +-------------------+
       |                              |
 1.    |                              |
       |      Lookup RMI registry     |
       +----------------------------->|
       |                              |
 2.    |                              |
       |     Return RMI stub object   |
       |<-----------------------------+
       |                              |
 3.    |                              |
       |   Invoke remote method       |
       +----------------------------->|
       |                              |
 4.    |                              |
       |   Register callback object   |
       +----------------------------->|
       |                              |
 5.    |                              |
       |    Return callback stub      |
       |<-----------------------------+
       |                              |
 6.    |                              |
       |  Callback method invocation |
       +----------------------------->|
       |                              |
       |                              |
