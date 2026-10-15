# m. Unit-тесты бизнес-логики

Пример (псевдокод / PHPUnit / Jest / pytest — по стеку).

## CleaningService

| Кейс | Вход | Ожидание |
|------|------|----------|
| start when docked + battery≥20 | robot docked, 50% | Job status=queued/running |
| start when battery&lt;20 | battery 10% | DomainError LowBattery |
| start when already cleaning | status=cleaning | DomainError AlreadyRunning |
| pause when running | job running | status=paused |
| pause when idle | no job | DomainError NoActiveJob |

```typescript
// Пример Jest
describe('CleaningService.start', () => {
  it('creates job when robot docked and battery ok', async () => {
    const robot = { status: 'docked', batteryPercent: 80 };
    const job = await service.start(robot.id, { programCode: 'auto' });
    expect(job.status).toMatch(/queued|running/);
  });

  it('rejects low battery', async () => {
    await expect(service.start(robotLowBat.id, { programCode: 'auto' }))
      .rejects.toThrow(/LowBattery/);
  });
});
```

## ScheduleService

- cron parse invalid → ValidationError  
- create enabled schedule → nextRunAt calculated  
- disable → nextRunAt null / ignored by scheduler  

## RobotPairingService

- valid serial + vendor OK → Robot created  
- serial already linked → ConflictError  
- vendor timeout → RetryableError
