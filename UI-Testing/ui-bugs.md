# Bugs — Sauce Demo

## BUG-UI-01 — Acesso a páginas internas após logout via botão "Back"

**Tela:** Qualquer página interna (ex: /inventory.html)
**Severidade:** Alta
**Prioridade:** Alta

**Pré-condição:**
- Usuário logado na aplicação.

**Passos para Reprodução:**
1. Realizar login com usuário válido (standard_user).
2. Navegar até a página de produtos (/inventory.html).
3. Clicar no menu lateral e realizar logout.
4. Após ser redirecionado para a tela de login, clicar no botão "Back" do navegador.

**Resultado Atual:**
- A aplicação exibe a página interna novamente, sem redirecionar para o login.

**Resultado Esperado:**
- O sistema deve invalidar a sessão e redirecionar o usuário para a tela de login.

---

## BUG-UI-02 — Falta de validação nos campos do checkout

**Tela:** /checkout-step-one.html
**Severidade:** Média
**Prioridade:** Média

**Pré-condição:**
- Usuário logado com ao menos um item no carrinho.

**Passos para Reprodução:**
1. Adicionar um item ao carrinho.
2. Acessar o carrinho e clicar em "Checkout".
3. Deixar um ou mais campos obrigatórios em branco (First Name, Last Name ou Zip Code).
4. Clicar em "Continue".

**Resultado Atual:**
- A validação existe mas as mensagens de erro são genéricas e não indicam claramente qual campo está incorreto.

**Resultado Esperado:**
- O sistema deve exibir mensagens de erro específicas por campo, indicando exatamente o que precisa ser corrigido.

---

## BUG-UI-03 — Ausência de feedback visual sobre expiração de sessão

**Tela:** Qualquer página interna
**Severidade:** Baixa
**Prioridade:** Baixa

**Pré-condição:**
- Usuário logado na aplicação.

**Passos para Reprodução:**
1. Realizar login com usuário válido.
2. Deixar a sessão inativa por um período prolongado.
3. Tentar interagir com a aplicação.

**Resultado Atual:**
- A aplicação não exibe nenhum aviso de expiração de sessão nem redireciona o usuário automaticamente.

**Resultado Esperado:**
- O sistema deve notificar o usuário sobre a expiração da sessão e redirecionar para a tela de login automaticamente.
