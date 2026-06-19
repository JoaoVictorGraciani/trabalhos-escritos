# Exercício 32 – Planejamento e Execução de Testes em Interface Web

## Objetivo
Desenvolver a capacidade analítica para inspecionar uma interface de usuário (UI) a partir do código HTML e elaborar uma documentação profissional de casos de teste cobrindo cenários positivos, negativos e regras de negócio.

---

# Parte 1 – Mapeamento dos Elementos da Interface

| Elemento | ID | Tipo | Restrições/Regras Identificadas |
|-----------|------|------|--------------------------------|
| Nome Completo | `nome` | Input Text | Obrigatório (`required`), mínimo de 5 caracteres (`minlength="5"`), máximo de 100 caracteres (`maxlength="100"`). |
| CPF | `cpf` | Input Text | Obrigatório (`required`), exatamente 11 dígitos numéricos (`pattern="\d{11}"`), máximo de 11 caracteres. |
| E-mail Profissional | `email` | Input Email | Obrigatório e deve possuir formato válido de e-mail. |
| Seleção de Vaga | `vaga` | Select | Obrigatório, deve selecionar uma opção diferente da opção padrão. |
| Botão Cancelar | `btn-cancelar` | Button | Sem restrições visíveis no HTML. |
| Botão Iniciar Teste Técnico | `btn-iniciar-teste` | Button | Inicia desabilitado (`disabled`). |
| Botão Finalizar Cadastro | `btn-cadastrar` | Submit | Responsável pelo envio do formulário. |
| Mensagem de Erro Nome | `erro-nome` | Span | Inicialmente oculta. |
| Mensagem de Erro CPF | `erro-cpf` | Span | Inicialmente oculta. |

---

# Parte 2 – Casos de Teste

## CT-001 – Cadastro com Dados Válidos

### Pré-condições
- Tela carregada corretamente.

### Passos
1. Preencher `#nome` com "João da Silva".
2. Preencher `#cpf` com "12345678901".
3. Preencher `#email` com "joao@email.com".
4. Selecionar uma vaga.
5. Clicar em `#btn-cadastrar`.

### Resultado Esperado
- Nenhuma mensagem de erro exibida.
- Formulário enviado com sucesso.

---

## CT-002 – Nome Inválido

### Pré-condições
- Tela carregada.

### Passos
1. Informar "Ana" no campo `#nome`.
2. Preencher os demais campos com dados válidos.
3. Clicar em `#btn-cadastrar`.

### Resultado Esperado
- Exibição da mensagem "Nome inválido".
- Cadastro bloqueado.

---

## CT-003 – CPF Inválido

### Pré-condições
- Tela carregada.

### Passos
1. Informar CPF "ABC12345678".
2. Preencher os demais campos corretamente.
3. Clicar em `#btn-cadastrar`.

### Resultado Esperado
- Exibição da mensagem de erro do CPF.
- Cadastro bloqueado.

---

## CT-004 – Botão Iniciar Teste Técnico

### Pré-condições
- Página aberta pela primeira vez.

### Passos
1. Localizar o botão `#btn-iniciar-teste`.

### Resultado Esperado
- Botão permanece desabilitado.
- Usuário não consegue clicar.

---

# Parte 3 – Planejamento para Automação

## Seletores Recomendados

### Campo CPF

```css
#cpf
```

### Botão Finalizar Cadastro

```css
#btn-cadastrar
```

## Justificativa do uso de ID

- Unicidade do elemento.
- Maior estabilidade dos testes.
- Melhor desempenho na localização.
- Facilidade de manutenção.
- Melhor legibilidade do código automatizado.

### Exemplo Cypress

```javascript
cy.get('#cpf')
cy.get('#btn-cadastrar')
```

### Exemplo Selenium

```java
driver.findElement(By.id("cpf"));
driver.findElement(By.id("btn-cadastrar"));
```

---

# Conclusão

A documentação cobre os principais fluxos da interface, incluindo validações de campos obrigatórios, restrições de formato, cenários de erro e regras de negócio relacionadas ao estado dos componentes. Os casos de teste servem como base para execução manual e automação E2E com Selenium ou Cypress.
