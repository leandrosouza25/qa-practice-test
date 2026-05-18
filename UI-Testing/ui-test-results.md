#  Resultados dos Testes — UI Sauce Demo

## Resumo

| Total | Passaram | Falharam | Observações |
|-------|----------|----------|-------------|
| 9     | 7        | 2        | BUG-UI-01 e BUG-UI-02 identificados |



## Detalhamento

| ID | Cenário | Resultado | Observação |
|----|---------|-----------|------------|
| CT-UI-01 | Login com diferentes tipos de usuários | ✅ Passou | standard_user OK, locked_out_user exibe erro corretamente |
| CT-UI-02 | Ordenação de produtos | ✅ Passou | A-Z, Z-A, menor e maior preço funcionando |
| CT-UI-03 | Fluxo completo de compra | ✅ Passou | Itens, valores e mensagem de sucesso corretos |
| CT-UI-04 | Remoção de itens do carrinho | ✅ Passou | Item removido e badge atualizado corretamente |
| CT-UI-05 | Navegação entre páginas | ✅ Passou | Estado e carrinho preservados |
| CT-UI-06 | Logout | ⚠️ Parcial | Logout funciona, porém botão "Back" permite retorno — BUG-UI-01 |
| CT-UI-07 | Testes de Responsividade | ✅ Passou | Layouts funcionais em desktop, tablet e mobile |
| CT-UI-08 | Testes de Acessibilidade | ✅ Passou | Navegação por teclado e contraste validados |
| CT-UI-09 | Testes Automatizados (Cypress) | ⚠️ Pendente | Não implementado no prazo — documentado como pendente |



## Observações

- CT-UI-06 marcado como parcial devido ao BUG-UI-01 — acesso via botão "Back" após logout.
- CT-UI-09 (automação via Cypress) ficou pendente por limitação de tempo — os fluxos foram validados manualmente.
- Evidências capturadas disponíveis na pasta `evidencies/ui`.
Obs: Não foram capturadas 100% das evidências devido ao prazo. As evidências de ordenação estão junto com as de produtos.