# b. Доменная модель

| Домен / сущность | Атрибуты |
|------------------|----------|
| **User** | id, email, name, locale, createdAt |
| **Home** | id, userId, name, address, timezone |
| **Robot** | id, homeId, serialNumber, model, firmwareVersion, status (online/offline/cleaning/docked/error), batteryPercent, lastSeenAt |
| **Room** | id, homeId, name, areaM2, floorType, mapPolygon |
| **NoGoZone** | id, roomId, polygon |
| **CleaningProgram** | id, code (auto/zone/spot), name, suctionLevel, waterLevel, passes |
| **Schedule** | id, robotId, programId, roomIds[], cronExpression, enabled, nextRunAt |
| **CleaningJob** | id, robotId, programId, roomIds[], status (queued/running/paused/done/failed), startedAt, finishedAt, areaCleanedM2, batteryUsed |
| **ServiceEvent** | id, robotId, type (brush/filter/firmware/error), description, dueAt, completedAt |
| **Firmware** | id, model, version, releaseNotes, packageUrl, mandatory |
| **DiagnosticReport** | id, robotId, payload(json), sentToVendorAt |

### Связи (кратко)

User 1—N Home → 1—N Robot, Room  
Robot 1—N Schedule, CleaningJob, ServiceEvent, DiagnosticReport  
Room N—M CleaningJob; Room 1—N NoGoZone  
CleaningJob → CleaningProgram
