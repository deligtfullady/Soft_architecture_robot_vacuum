# p. Регрессионное тестирование

Запускать **перед каждым релизом** и после hotfix.

## Smoke (15 мин)

1. Login  
2. Список роботов  
3. Старт / пауза / dock  
4. Health `/tech/ready` = 200  

## Полный регресс (по приоритету)

| Приоритет | Область | Набор |
|-----------|---------|--------|
| P0 | Pairing, start/pause/dock | Unit + E2E Postman + UAT-01,02,03 |
| P1 | Schedules, history | E2E schedules, UAT-04,05 |
| P2 | Service / OTA | UAT-06, vendor mock tests |
| P3 | BFF aggregation, cache invalidation | API tests |

## Автоматизация

- CI: unit + Postman/Newman на MR  
- Nightly: полный E2E на staging  
- Перед prod: чеклист smoke + подпись UAT при major release  

## Данные

Фикстуры: тестовый serial, homeId, робот в статусе docked battery=100%.  
После прогона — cleanup jobs/schedules тестового пользователя.
