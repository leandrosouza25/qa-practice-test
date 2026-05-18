#  Resultados dos Testes — API Restful Booker

## Resumo

| Total | Passaram | Falharam |
|-------|----------|----------|
| 7     | 4        | 3        |



## Detalhamento

| ID | Requisição | Método | Status Esperado | Status Recebido | Resultado |
|----|-----------|--------|-----------------|-----------------|-----------|
| CT-API-01 | POST Auth | POST | 200 | 200 | ✅ Passou |
| CT-API-02 | POST Create Booking | POST | 200 | 200 | ✅ Passou |
| CT-API-03 | GET Booking | GET | 200 | 200 | ✅ Passou |
| CT-API-04 | PUT Update Booking | PUT | 200 | 403 | ❌ Falhou |
| CT-API-05 | DELETE Booking | DELETE | 201 | 403 | ❌ Falhou |
| CT-API-06 | POST Create Booking - Missing Fields | POST | 400 | 500 | ❌ Falhou |
| CT-API-07 | GET Filter by Firstname | GET | 200 | 200 | ✅ Passou |
| CT-API-08 | GET Filter by Dates | GET | 200 | 200 | ✅ Passou |



## Observações

- CT-API-04 e CT-API-05 falharam por problema de autenticação — detalhes em `api-bugs.md` (BUG-01 e BUG-02)
- CT-API-06 falhou pois a API retornou 500 ao invés de 400 — detalhes em `api-bugs.md` (BUG-03)