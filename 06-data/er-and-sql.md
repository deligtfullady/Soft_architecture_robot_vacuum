# g. ER-модель и хранение

## Сущности (таблицы)

users, homes, robots, rooms, no_go_zones, cleaning_programs,  
schedules, schedule_rooms, cleaning_jobs, job_rooms,  
service_events, firmwares, diagnostic_reports

## Примеры запросов

```sql
-- История уборок робота за 30 дней
SELECT id, status, area_cleaned_m2, started_at, finished_at
FROM cleaning_jobs
WHERE robot_id = $1 AND started_at >= now() - interval '30 days'
ORDER BY started_at DESC;

-- Активные расписания на ближайший час
SELECT s.* FROM schedules s
WHERE s.enabled AND s.next_run_at BETWEEN now() AND now() + interval '1 hour';
```

СУБД: **PostgreSQL**. Карты комнат — JSONB / PostGIS (опционально).
