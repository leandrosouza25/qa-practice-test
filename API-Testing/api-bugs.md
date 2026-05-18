BUG-01 — PUT Update Booking retorna 403 Forbidden

Endpoint: PUT {{base_url}}/booking/{{booking_id}}
booking_id: 2780
Status recebido: 403 Forbidden
Status esperado: 200 OK
Tempo de resposta: 173 ms
Body da resposta: Forbidden
Descrição: Ao tentar atualizar uma reserva existente via PUT, a API retorna 403 Forbidden. O token de autenticação está presente nas variáveis de ambiente (token: d5d2eed74c4...), porém a requisição é rejeitada. O teste automatizado pm.test("Booking updated", () => pm.response.to.have.status(200)) falha.
Possível causa: Token inválido, expirado ou não enviado corretamente no header da requisição.


BUG-02 — DELETE Booking retorna 403 Forbidden

Endpoint: DELETE {{base_url}}/booking/{{booking_id}}
booking_id: 3368
Status recebido: 403 Forbidden
Status esperado: 201 (conforme script do teste)
Tempo de resposta: 147 ms
Body da resposta: Forbidden
Descrição: Ao tentar deletar uma reserva via DELETE, a API retorna 403 Forbidden. O teste automatizado pm.test("Booking deleted", () => pm.response.to.have.status(201)) falha. Assim como no BUG-01, o problema parece estar relacionado à autenticação.
Possível causa: Ausência ou invalidade do token de autenticação no header. Vale verificar se o token gerado no POST Auth está sendo corretamente propagado para as requisições seguintes.


BUG-03 — POST Create Booking com campos ausentes retorna 500 ao invés de 400

Endpoint: POST {{base_url}}/booking
Status recebido: 500 Internal Server Error
Status esperado: 400 Bad Request
Tempo de resposta: 140 ms
Body da resposta: Internal Server Error
Descrição: Ao enviar uma requisição de criação de reserva com campos obrigatórios ausentes (missing fields), o esperado seria que a API retornasse 400 Bad Request com uma mensagem de validação. Porém, a API retorna 500 Internal Server Error, indicando que o servidor não trata adequadamente entradas incompletas.
Possível causa: Ausência de validação no backend antes do processamento da requisição. O servidor tenta processar os dados mesmo com campos nulos/ausentes e quebra internamente.


Observação geral: Os BUGs 01 e 02 provavelmente têm a mesma origem — problema com autenticação. Vale verificar primeiro o fluxo do POST Auth e confirmar se o token está sendo salvo e repassado corretamente nas variáveis de ambiente antes de investigar separadamente.