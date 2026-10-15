# e. BFF + бизнес-логика

```
[Web SPA] ──► [Web BFF]  ──┐
                            ├──► [API Gateway] ──► [BL: RobotService]
[Mobile]  ──► [Mobile BFF]─┘         │              [BL: ScheduleService]
                                     │              [BL: CleaningService]
                                     │              [BL: ServiceMaintenance]
                                     ▼
                              [Repository / DB]
                                     │
                              [Vendor Adapter]
```

**BFF (Backend for Frontend):**  
- Web BFF — агрегация dashboard (статус + последние jobs + сервис) одним запросом  
- Mobile BFF — урезанные DTO, push tokens, offline-friendly payloads  

# f. Кеширование

| Уровень | Что кешировать | TTL / стратегия |
|---------|----------------|-----------------|
| Клиент (app) | Карта комнат, список расписаний | stale-while-revalidate, 5–15 мин |
| API Gateway / BFF | Статус робота, battery | 5–15 с, invalidate по webhook |
| Бизнес-логика | Справочник программ, firmware metadata | 1 ч, cache-aside |
| Репозиторий | Read-replicas для history jobs | eventual consistency |
| Не кешировать | Команды start/pause/dock, pairing | — |
