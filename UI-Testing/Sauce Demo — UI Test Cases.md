#  Sauce Demo — UI Test Cases (Nível Obrigatório)

**Objetivo:** Validar os principais fluxos do usuário: login, ordenação, carrinho, checkout, navegação e logout.


## CT-UI-01 — Login com diferentes tipos de usuários

**Pré-condição:** Estar na tela de login.

**Cenários:**
- standard_user / secret_sauce
- locked_out_user / secret_sauce
- Senha inválida
- Campos vazios

**Resultado esperado:**
- Usuário válido acessa a inventory.
- Usuário bloqueado exibe mensagem de erro.
- Validações para senha inválida e campos vazios.
- Sessão permanece ativa após refresh.



## CT-UI-02 — Ordenação de produtos

**Pré-condição:** Usuário logado.

**Passos:**
- Ordenar por Name (A–Z / Z–A)
- Ordenar por Price (low–high / high–low)

**Resultado esperado:**
- Produtos reordenados corretamente.
- Ordenação mantida ao navegar e retornar.



## CT-UI-03 — Fluxo completo de compra

**Pré-condição:** Usuário logado.

**Passos:**
1. Adicionar 2 itens ao carrinho.
2. Acessar carrinho → Checkout.
3. Preencher dados obrigatórios.
4. Finalizar compra.

**Resultado esperado:**
- Itens corretos no carrinho.
- Valores corretos no overview (item + taxa).
- Mensagem de sucesso exibida.



## CT-UI-04 — Remoção de itens do carrinho

**Pré-condição:** Item adicionado.

**Passos:**
- Remover item do carrinho.

**Resultado esperado:**
- Item removido.
- Badge do carrinho atualizado.



## CT-UI-05 — Navegação entre páginas

**Passos:**
- Navegar entre Inventory → Produto → Carrinho → Checkout → Cancelar.
- Utilizar botão "Back" do navegador.

**Resultado esperado:**
- Aplicação mantém estado.
- Carrinho preservado.
- Sem erros de sessão.



## CT-UI-06 — Logout

**Pré-condição:** Usuário logado.

**Passos:**
- Realizar logout.
- Tentar acessar páginas internas pelo botão "Back".

**Resultado esperado:**
- Redireciona para login.
- Acesso bloqueado a páginas internas.




# Nível 2 — Diferenciais

## CT-UI-07 — Testes de Responsividade

**Objetivo:** Validar o comportamento da aplicação em diferentes tamanhos de tela.

**Cenários:**
- Desktop (1920x1080)
- Tablet (768x1024)
- Mobile (375x667)

**Validações:**
- Elementos não sobrepostos
- Botões e campos visíveis
- Menu lateral funcional
- Fluxo de compra possível em telas menores



## CT-UI-08 — Testes de Acessibilidade

**Objetivo:** Validar requisitos básicos de acessibilidade.

**Cenários:**
- Navegação utilizando apenas o teclado (TAB/ENTER)
- Verificar contraste de cores dos botões e textos
- Verificar presença de labels nos campos de login e checkout

**Validações:**
- Foco visível ao navegar com TAB
- Leitura compreensível dos campos
- Elementos clicáveis acessíveis via teclado



## CT-UI-09 — Testes Automatizados (Cypress)

**Objetivo:** Automatizar os principais fluxos críticos da aplicação.

**Cenários automatizados:**
- Login com usuário válido
- Adicionar item ao carrinho
- Remover item
- Finalizar checkout com sucesso
- Logout

**Resultado esperado:**
- Execução automatizada validando os fluxos principais sem intervenção manual.