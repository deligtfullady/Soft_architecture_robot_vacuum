# n. E2E тесты (Postman)

1. Импортировать `RobotVacuum.postman_collection.json` в Postman.  
2. Задать `baseUrl`, `token`, `homeId`, `robotId`.  
3. Collection Runner: сценарий **Pair → Start → History → Schedule**.  
4. Tests scripts (пример на запросе Start):

```js
pm.test('Accepted 202', () => pm.response.to.have.status(202));
pm.test('Job id present', () => {
  const j = pm.response.json();
  pm.expect(j.id).to.be.ok;
});
```

Альтернативы: Newman CI, Playwright API, RestAssured.
