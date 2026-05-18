#  API Testing — Restful Booker

Base URL: https://restful-booker.herokuapp.com

Testes executados utilizando Postman com scripts automatizados na aba Tests (Post-response).

##  Plano de Testes

O objetivo é validar o funcionamento da API Restful-Booker cobrindo autenticação, CRUD completo de reservas, validações de dados, tratamento de erros e cenários negativos.

Os testes foram divididos em:
- Nível Obrigatório (fluxos essenciais)
- Nível Diferencial (performance, segurança e automação)



##  Cenários Principais

Durante a análise da API, foram identificados os seguintes cenários críticos:

- Fluxo de autenticação
- Gestão de reservas (Create, Read, Update, Delete)
- Filtros e buscas de reservas
- Tratamento de erros (status codes)
- Validações de dados enviados no payload



## Collection de Requests

A collection utilizada nos testes encontra-se na pasta:

API-Testing/Restful-Booker.postman_collection.json

Esta collection foi criada e executada utilizando o Postman e contém:

- Todas as requisições necessárias para validar o CRUD completo da API
- Scripts automatizados na aba **Tests (Post-response)** para validação de status code e respostas
- Uso de variáveis de ambiente como {{base_url}}, {{token}} e {{booking_id}}
- Execução sequencial validando o fluxo completo da API (Auth → Create → Get → Update → Delete)

A collection pode ser executada manualmente pelo Postman Runner ou de forma automatizada via Newman.



##  CT-API-01 — Autenticação Básica (`POST /auth`)

**Testes:**
- Credenciais válidas
- Credenciais inválidas

**Resultado esperado:**
- Retorno do token para acesso autorizado
- Erro para login inválido



##  CT-API-02 — Criar reserva (`POST /booking`)

**Validações:**
- Payload completo e válido
- Campos obrigatórios ausentes
- Datas inválidas (checkout < checkin)
- Tipos de dados incorretos

**Resultado esperado:**
- Reserva criada com ID
- Retorno de erro para payload inválido



##  CT-API-03 — Consultar reserva (`GET /booking/{id}`)

**Testes:**
- ID existente
- ID inexistente

**Resultado esperado:**
- 200 para reserva existente
- 404 para inexistente
- Estrutura JSON correta



##  CT-API-04 — Atualizar reserva (`PUT / PATCH`)

**Testes:**
- Atualização total
- Atualização parcial
- Sem token
- Token inválido

**Resultado esperado:**
- 200 para sucesso
- 403 para falha de autenticação



##  CT-API-05 — Deletar reserva (`DELETE /booking/{id}`)

**Testes:**
- Delete com sucesso
- Delete sem token
- Validar que não retorna dados após exclusão



##  Análise de Bugs

Durante os testes, foram observados possíveis comportamentos problemáticos:

- API aceita alguns tipos de dados incorretos sem validação rígida.
- Mensagens de erro pouco descritivas.
- Falta de validação mais forte nas regras de datas.



##  Sugestões de Melhoria

- Implementar validação de schema no backend.
- Melhorar mensagens de erro retornadas pela API.
- Implementar regras de negócio mais rígidas para datas de reserva.



##  Análise de Riscos

- Falta de validação adequada pode permitir dados inconsistentes.
- Possibilidade de uso indevido da API sem tratamento adequado de autenticação.
- Retornos pouco descritivos dificultam diagnóstico de falhas.


#  Nível 2 — Diferenciais


##  Testes de Performance

- Medir tempo de resposta dos endpoints principais.
- Validar comportamento com múltiplas requisições seguidas.

##  Testes de Segurança

- Tentativa de acesso sem token.
- Token inválido.
- Envio de payload malformado.

##  Automação via Scripts

- Execução automatizada da collection via Postman Runner ou Newman.
- Validação automática dos status codes e respostas.
