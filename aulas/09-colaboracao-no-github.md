# 09 — Trabalhando colaborativamente no GitHub

Git se torna muito mais poderoso quando várias pessoas trabalham no mesmo projeto. Nesta aula, o objetivo é entender o fluxo mais comum usado em equipes.

## Visão geral

```text
Issue
  ↓
Branch
  ↓
Commits
  ↓
Push
  ↓
Pull Request
  ↓
Code Review
  ↓
Ajustes
  ↓
Merge
  ↓
main
```

---

## 1. Clone x Fork

Esses termos são parecidos, mas representam coisas diferentes.

### Clone

`git clone` cria uma cópia local de um repositório que já existe.

```text
GitHub
  │
  └──── git clone ────► seu computador
```

Exemplo:

```bash
git clone https://github.com/usuario/projeto.git
```

### Fork

Um **fork** cria uma cópia do repositório na sua própria conta do GitHub.

```text
repositório original
        │
        └──── Fork ────► sua conta GitHub
                              │
                              └──── clone ────► computador
```

Forks são comuns quando você quer contribuir com um projeto no qual não possui permissão de escrita direta.

### Resumo

| Ação | Onde cria a cópia? | Uso comum |
|---|---|---|
| `clone` | no seu computador | trabalhar localmente |
| `fork` | na sua conta do GitHub | contribuir sem acesso direto ao original |

---

## 2. `origin` e `upstream`

Ao clonar seu próprio fork, normalmente:

```text
origin   → seu fork
upstream → repositório original
```

Adicione o repositório original como `upstream`:

```bash
git remote add upstream https://github.com/autor-original/projeto.git
```

Confira:

```bash
git remote -v
```

Exemplo mental:

```text
                    upstream
                       ▲
                       │
repositório original ──┘

seu fork ─────────────► origin
   ▲
   │
seu computador
```

---

## 3. Issue: definir o problema antes de codificar

Em muitas equipes, o trabalho começa com uma **Issue**.

Uma issue pode descrever:

- um bug;
- uma nova funcionalidade;
- uma melhoria de documentação;
- uma tarefa técnica.

Exemplo:

```text
Issue #42
Título: Corrigir validação do formulário de login

Problema:
O formulário permite envio sem e-mail.

Critério de aceite:
- e-mail obrigatório;
- mensagem de erro visível;
- envio bloqueado quando inválido.
```

Isso reduz ambiguidade antes de começar o código.

---

## 4. Crie uma branch para a tarefa

Evite desenvolver diretamente na `main`.

```bash
git switch main
git pull
git switch -c fix/validacao-login
```

Um padrão simples de nomes:

```text
feat/nova-funcionalidade
fix/correcao-de-bug
docs/documentacao
refactor/melhoria-interna
```

---

## 5. Faça commits pequenos e explicativos

Evite um único commit gigantesco chamado:

```text
arrumei tudo
```

Prefira algo como:

```text
fix: valida campo de email

test: cobre envio sem email

docs: documenta comportamento do formulario
```

Um bom commit facilita:

- revisar;
- encontrar quando algo mudou;
- reverter uma alteração específica;
- entender o histórico meses depois.

---

## 6. Atualize sua branch antes do Pull Request

Enquanto você trabalha, a `main` pode avançar.

```text
main       A────B────E
                \
feature          C────D
```

Sua branch possui trabalho novo (`C` e `D`), mas não possui `E`.

Atualize as referências remotas:

```bash
git fetch origin
```

Depois integre a `main` conforme o fluxo da equipe:

```bash
git merge origin/main
```

ou, se a equipe usar rebase:

```bash
git rebase origin/main
```

> Não escolha merge ou rebase no automático. Siga o padrão definido pelo projeto.

---

## 7. Envie sua branch

```bash
git push -u origin fix/validacao-login
```

Agora a branch existe também no GitHub.

```text
branch local
    │
    └──── push ────► branch remota
```

---

## 8. Abra um Pull Request

Um **Pull Request (PR)** é um pedido para integrar alterações de uma branch em outra.

```text
fix/validacao-login
         │
         └──── Pull Request ────► main
```

Um PR bem descrito deve responder:

1. **O que mudou?**
2. **Por que mudou?**
3. **Como verificar?**
4. **Há algum risco ou detalhe importante?**

Exemplo:

```markdown
## O que mudou
- adiciona validação obrigatória de e-mail;
- exibe mensagem quando o campo está vazio.

## Como testar
1. abrir o formulário;
2. deixar e-mail vazio;
3. clicar em enviar;
4. confirmar que o envio é bloqueado.
```

---

## 9. Code Review

No review, outra pessoa analisa o diff antes do merge.

O objetivo não é procurar culpados. O review ajuda a verificar:

- corretude;
- legibilidade;
- efeitos colaterais;
- testes;
- segurança;
- aderência ao padrão do projeto.

### Feedback saudável

Em vez de:

```text
Isso está errado.
```

Prefira algo específico:

```text
Podemos extrair essa validação para uma função? Assim evitamos duplicação nos dois formulários.
```

---

## 10. Recebi pedido de alteração. Preciso abrir outro PR?

Normalmente, não.

Continue na mesma branch:

```bash
# faça a correção
git add .
git commit -m "fix: ajusta validacao conforme review"
git push
```

O Pull Request é atualizado automaticamente.

```text
mesma branch
    ↓ novo commit
    ↓ push
mesmo Pull Request atualizado
```

---

## 11. Merge do Pull Request

Depois da aprovação, a branch pode ser integrada à `main`.

Os três métodos mais conhecidos são:

| Método | Resultado geral |
|---|---|
| Merge commit | preserva as linhas de histórico e cria um commit de merge |
| Squash and merge | transforma os commits do PR em um único commit na base |
| Rebase and merge | reaplica os commits sobre a base sem criar merge commit |

Nenhum é universalmente melhor. Projetos diferentes adotam políticas diferentes.

---

## 12. Depois do merge

Atualize sua `main` local:

```bash
git switch main
git pull
```

Exclua a branch local se ela já terminou:

```bash
git branch -d fix/validacao-login
```

---

## 13. Branch protegida

Em projetos colaborativos, a `main` pode ser protegida para impedir alterações diretas.

Um fluxo possível:

```text
push direto na main ❌

branch → Pull Request → aprovação → checks → merge ✅
```

Isso ajuda a evitar que código não revisado entre na linha principal.

---

## 14. Fluxo com fork em projeto open source

```text
1. Fork do projeto
       ↓
2. Clone do seu fork
       ↓
3. Adiciona upstream
       ↓
4. Cria branch
       ↓
5. Commits
       ↓
6. Push para origin (seu fork)
       ↓
7. PR para o repositório original
       ↓
8. Review
       ↓
9. Merge
```

Antes de contribuir, procure arquivos como:

```text
CONTRIBUTING.md
CODE_OF_CONDUCT.md
README.md
```

Eles podem conter regras específicas do projeto.

---

## 15. Pratique neste próprio repositório

Este repositório possui um [`CONTRIBUTING.md`](../CONTRIBUTING.md) com um fluxo de contribuição didático.

Você pode usar esse documento para entender como um projeto real comunica:

- como criar branches;
- padrão de commits;
- como montar um PR;
- o que revisar antes de enviar.

> Para praticar sem gerar PRs desnecessários no projeto original, você pode fazer um fork e abrir o Pull Request entre uma branch e a `main` do **seu próprio fork**.

---

## ✅ Checklist da aula

- [ ] Sei explicar clone x fork.
- [ ] Entendo `origin` x `upstream`.
- [ ] Sei por que equipes usam Issues.
- [ ] Sei criar uma branch para uma tarefa.
- [ ] Sei abrir e atualizar um Pull Request.
- [ ] Entendo o objetivo de code review.
- [ ] Sei o que acontece depois do merge.
- [ ] Entendo por que uma `main` pode ser protegida.