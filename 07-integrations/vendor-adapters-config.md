# h–j. Интеграции, адаптеры, конфигурация

## h. Vendor API (производитель)

Компонент `VendorCloudAdapter`:
- OTA firmware download/upload status  
- Diagnostic telemetry push  
- Serial validation on pairing  

```
[FirmwareService] ──► [VendorCloudAdapter] ──HTTPS──► vendor.api
[DiagnosticService] ─┘
```

## i. Адаптеры

| Адаптер | Назначение |
|---------|------------|
| PostgresRepository | CRUD домена |
| WebBffGateway / MobileBffGateway | DTO под клиент |
| VendorCloudAdapter | Третья сторона |
| RobotDeviceGateway | MQTT/WebSocket к устройству (опц.) |

## j. Внешнее конфигурирование

`Config Service` / feature flags (robot model parameters):
- suction defaults, battery thresholds, map resolution  
- Источник: env + remote config (Consul/AppConfig), per-model YAML
