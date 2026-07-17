# Autopilot Provisioning Flow

```mermaid
flowchart TD
    A[Autopilot Device]
    B[Group Tag:<br/>WIN11-CORP-STANDARD]
    C[Dynamic Device Group<br/>GRP-DYN-WIN11-AP-STANDARD]
    D[Autopilot Profile<br/>AP-WIN11-STANDARD]
    E[Enrolment Status Page<br/>ESP-WIN11-STANDARD]
    F[Expected Windows 11 Provisioning]

    A --> B
    B --> C
    C --> D
    C --> E
    D --> F
    E --> F
```
