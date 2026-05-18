# QA Practice Test — Leandro Souza 

Repositório com a solução completa do teste técnico para a vaga de QA.

O teste foi dividido em duas partes principais: UI Testing (Sauce Demo) e API Testing (Restful-Booker).



##  Ferramentas Utilizadas

- **Postman** — execução e automação dos testes de API
- **Newman** — execução da collection via linha de comando (opcional)
- **Navegador Google Chrome** — execução dos testes de UI
- **VSCode** — organização e documentação do projeto
- **Markdown** — documentação de todos os artefatos



##  Estrutura do Projeto

qa-practice-test/
├── API-Testing/
│   ├── collections/
│   │   ├── Restful-Booker.postman_collection.json
│   │   └── Restful-Booker.postman_environment.json
│   ├── evidencies-api/
│   │   ├── Bug-01/
│   │   ├── Bug-02/
│   │   ├── Bug-03/
│   │   ├── FILTER-01_GET-FilterByFirstname_200-OK.png
│   │   ├── FILTER-02_GET-FilterByDates_200-OK.png
│   │   ├── PERF-01_POST-Auth_response-time.png
│   │   ├── PERF-02_POST-CreateBooking_response-time.png
│   │   ├── PERF-03_GET-Booking_response-time.png
│   │   ├── PERF-04_PUT-UpdateBooking_response-time.png
│   │   ├── PERF-05_DELETE-Booking_response-time.png
│   │   ├── PERF-06_GET-FilterByFirstname_response-time.png
│   │   ├── PERF-07_GET-FilterByDates_response-time.png
│   │   ├── SEC-01_POST-Auth-InvalidCredentials.png
│   │   ├── SEC-02_PUT-NoToken_403.png
│   │   └── SEC-03_DELETE-NoToken_403.png
│   ├── API Testing — Restful Booker.md
│   ├── api-bugs.md
│   └── api-test-results.md
├── UI-Testing/
│   ├── evidencies/ui/
│   │   ├── cart/
│   │   ├── checkout/
│   │   ├── locked_user_error/
│   │   ├── login-success/
│   │   ├── logout/
│   │   ├── navegacao/
│   │   └── products/
│   ├── risks-and-improvements.md
│   ├── Sauce Demo — UI Test Cases.md
│   ├── ui-bugs.md
│   ├── ui-test-results.md
│   └── ui-testing-plan.md
└── README.md



##  Como Executar os Testes de API

### Via Postman

1. Abra o Postman
2. Clique em **Import**
3. Importe os dois arquivos da pasta `collections/`:
   - `Restful-Booker.postman_collection.json`
   - `Restful-Booker.postman_environment.json`
4. Selecione o environment **Restful Booker Env** no canto superior direito
5. Execute as requisições na ordem:
   - `01 - Auth` → `02 - Booking CRUD` → `03 - Negative Tests` → `04 - Filters` → `05 - Security Tests`

>  Execute sempre o **POST Auth primeiro** para gerar o token e o **POST Create Booking** antes do GET, PUT e DELETE, pois eles dependem do `booking_id` gerado automaticamente.

### Via Newman (opcional)

```bash
npm install -g newman

newman run collections/Restful-Booker.postman_collection.json \
  --environment collections/Restful-Booker.postman_environment.json
```



##  Como Executar os Testes de UI

1. Acesse [https://www.saucedemo.com/v1/](https://www.saucedemo.com/v1/)
2. Execute os cenários descritos em `UI-Testing/Sauce Demo — UI Test Cases.md`
3. Utilize os seguintes usuários de teste:

| Usuário | Senha | Comportamento |
|---------|-------|---------------|
| standard_user | secret_sauce | Acesso normal |
| locked_out_user | secret_sauce | Bloqueado — exibe erro |
| problem_user | secret_sauce | Problemas visuais |
| performance_glitch_user | secret_sauce | Login lento |



##  Premissas Assumidas

- A API Restful-Booker é pública e pode apresentar instabilidades ocasionais no ambiente Heroku.
- O token de autenticação gerado pelo POST Auth expira após um período — recomenda-se executar Auth antes de cada sessão de testes.
- Os testes de UI foram executados manualmente no navegador Google Chrome versão mais recente.
- Os testes de responsividade foram validados via DevTools do Chrome nas dimensões: 1920x1080, 768x1024 e 375x667.



##  Pendências e Dificuldades

- **Automação UI via Cypress** (CT-UI-09): não implementada por limitação de tempo. Os fluxos foram validados manualmente e documentados com evidências.
- **BUG-01 e BUG-02 (API)**: as requisições PUT e DELETE retornam 403 Forbidden mesmo com token presente. A causa raiz está sendo investigada — possivelmente relacionada ao formato de envio do token no header.
- **Evidências de responsividade e acessibilidade** (CT-UI-07 e CT-UI-08): os cenários estão documentados e foram validados manualmente via DevTools do Chrome, porém não foram geradas capturas de tela específicas por limitação de tempo.
- **Evidências de problem_user e performance_glitch_user**: os comportamentos foram observados e documentados nos casos de teste, porém capturas de tela específicas desses usuários ficaram pendentes por limitação de tempo.



##  Informações Adicionais

- Todos os bugs encontrados estão documentados em `api-bugs.md` e `ui-bugs.md`
- Os resultados dos testes estão em `api-test-results.md` e `ui-test-results.md`
- As evidências estão organizadas nas pastas `evidencies-api` e `evidencies/ui`
