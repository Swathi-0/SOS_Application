# SOS_Application
This  a SOS app for women’s safety using Java in Android Studio. The app sends the live location to saved emergency contacts when the phone is shaken.
# Flowchart
```mermaid
flowchart TD
    A[Start] --> B[Splash Screen]
    B --> C{Is Emergency Number Registered?}
    C -- Yes --> D[Main Activity]
    C -- No --> E[Register Number Activity]
    
    E --> F[Validate Number]
    F --> G{Is Number Valid?}
    G -- Yes --> H[Save Number]
    G -- No --> E
    
    H --> D
    
    D --> I[Activate Shake Detection Service]
    I --> J{Shake Event Detected?}
    J -- Yes --> K[Retrieve Location]
    J -- No --> I
    
    K --> L{Location Retrieved?}
    L -- Yes --> M[Format Location as Google Maps Link]
    L -- No --> N[Set Location Message to 'Unable to Find Location']
    
    M --> O[Send SOS SMS]
    N --> O
    
    O --> P[Display Notification]
    P --> Q{Stop Service?}
    Q -- Yes --> R[Stop SOS Service]
    Q -- No --> I
    
    R --> S[End] 
```
# Flowchart
```mermaid
%% UML Use Case Diagram for SOS Application

usecase
    actor User as "User"
    actor ShakeDetection as "Shake Detection Service"
    actor SMSService as "SMS Service"

    User --> (Launch Application)
    User --> (Register Emergency Contact)
    User --> (Shake Phone)

    (Launch Application) --> (Activate Shake Detection)
    (Activate Shake Detection) --> ShakeDetection
    (Shake Phone) --> ShakeDetection

    ShakeDetection --> (Retrieve Location)
    ShakeDetection --> (Send SOS SMS)

    (Retrieve Location) --> SMSService
    (Send SOS SMS) --> SMSService

    SMSService --> (Display Notification)

```



