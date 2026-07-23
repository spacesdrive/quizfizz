# Leaderboard

```mermaid
flowchart TD

    A([Finish Quiz])

    A --> B[Calculate Score]

    B --> C[Save Attempt]

    C --> D[Update Rankings]

    D --> E[Display Leaderboard]

    E --> F([End])
```