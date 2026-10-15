# a. Пользовательский интерфейс (Web-SPA + Native Mobile)

## Экраны / компоненты

| Компонент | Web-SPA | Mobile native |
|-----------|---------|---------------|
| Подключение робота | Wizard: QR / Wi‑Fi / pairing code | Camera QR + BLE |
| Управление помещениями | Карта квартиры, зоны, no-go | Touch map, жесты |
| Программы уборки | Список: авто, зона, точечная | Bottom sheet |
| Расписание | Календарь + cron-like UI | Local notifications |
| Сервисное обслуживание | Статус щёток, фильтр, прошивка | Push о сервисе |
| История уборок | Таблица + графики | Timeline |
| Статистика | Dashboard (м², часы, батарея) | Widgets |

## Wireframe (текстовый)

```
[Header: Robot status ● Online | 87%]
[Nav: Home | Rooms | Schedule | History | Service]
[Map canvas]
[Actions: Start | Pause | Dock | Zones]
```

Диаграммы UI: `diagrams/ui-components.drawio` (структура для diagrams.net / Figma).
