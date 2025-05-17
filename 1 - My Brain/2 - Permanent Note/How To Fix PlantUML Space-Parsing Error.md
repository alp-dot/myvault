---
created: 2025-05-11
tags:
  - troubleshooting
  - plantuml
  - diagram
description: How to fix PlantUML space-related parsing errors in participant names
reference:
---

# PlantUML Space Handling in Participant Names

## Problem
When using PlantUML, you may encounter this error:
```
Error (Line 14): Ingest -> Pub/Sub : Publish message
```

This occurs because PlantUML has trouble parsing participant names that contain spaces (like `Pub/Sub`) when they're not properly formatted.

## Solution
Enclose the message in quotes:
```plantuml
Ingest -> Pub/Sub : "Publish message"
```

## Explanation
PlantUML needs to clearly identify participants in message exchanges. When participant names contain spaces and aren't properly quoted, the parser can't determine where the participant name ends and the message description begins.

## Additional Tips
1. Always use quotes around messages when participants have spaces
2. Alternatively, consider using aliases for participants with spaces
3. Use underscores or hyphens instead of spaces when possible