# 📚 Git e GitHub — Do zero ao trabalho em equipe

Material gratuito e prático para aprender **Git e GitHub desde o primeiro contato até um fluxo colaborativo com branches, Pull Requests, conflitos e code review**.

O objetivo não é fazer você decorar comandos. É construir um **modelo mental do Git** para que consiga entender o estado do repositório, tomar decisões com segurança e investigar problemas sozinho.

> **Nunca usou Git?** Comece pela **[Aula 00 — Comece aqui](aulas/00-comece-aqui.md)**.

---

## 🎯 O que você deve conseguir fazer ao terminar

```text
instalar e configurar Git
         ↓
criar um repositório
         ↓
entender staging e commits
         ↓
trabalhar com branches
         ↓
publicar no GitHub
         ↓
abrir e revisar Pull Requests
         ↓
resolver conflitos
         ↓
entender ahead / behind
         ↓
investigar erros comuns
         ↓
trabalhar em um fluxo de equipe
```

Ao final, a meta é que você consiga usar Git e GitHub em um projeto real sem depender de uma receita pronta para cada situação.

---

## 🧭 Como usar este repositório

### 🌱 Sou iniciante absoluto

Siga a trilha na ordem, começando pela [Aula 00](aulas/00-comece-aqui.md).

```text
00 → 01 → 02 → 03 → 04 → 05 → 06 → 07 → 08 → 09 → 10
                                                  ↓
                                              Desafios
                                                  ↓
                                           Projeto final
```

### ⚡ Já uso Git e quero consultar algo

Use o [Cheat sheet](#-cheat-sheet), a trilha por assunto ou vá direto para:

- [Branches e merge](aulas/04-branches-e-merge.md)
- [Remotos e Pull Requests](aulas/05-remotos-github-e-pull-request.md)
- [Conflitos e recuperação](aulas/06-conflitos-e-desfazer-alteracoes.md)
- [Stash, rebase e boas práticas](aulas/07-stash-rebase-e-boas-praticas.md)
- [Colaboração no GitHub](aulas/09-colaboracao-no-github.md)
- [Erros comuns e diagnóstico](aulas/10-erros-comuns-e-diagnostico.md)

### 🧪 Quero aprender fazendo

Vá para os [desafios práticos](desafios/README.md) e, depois, para o [projeto final](projeto-final/README.md).

---

## 🧠 Modelo mental fundamental

Antes dos comandos, entenda o caminho de uma alteração:

```text
Working Directory
      ↓ git add
  Staging Area
      ↓ git commit
Local Repository
      ↓ git push
Remote Repository (GitHub)
```

Uma forma simples de pensar:

```text
editar      → você mudou algo
add         → você escolheu o que entrará no próximo commit
commit      → você registrou essa mudança no histórico local
push        → você enviou commits ao remoto
Pull Request→ você propôs integrar uma branch em outra
merge       → os históricos foram integrados
```

---

## 📖 Trilha completa

| # | Conteúdo | O que você aprende |
|---|---|---|
| 00 | **[Comece aqui](aulas/00-comece-aqui.md)** | instalação, preparação do ambiente, vocabulário mínimo e como estudar |
| 01 | [Introdução ao Git](aulas/01-introducao-ao-git.md) | Git x GitHub, repositório, commit, branch e staging area |
| 02 | [Configuração e primeiros passos](aulas/02-configuracao-e-primeiros-passos.md) | identidade, `git init`, `git clone` e terminal |
| 03 | [Commits e histórico](aulas/03-commits-e-historico.md) | status, diff, staging, commits e logs |
| 04 | [Branches e merge](aulas/04-branches-e-merge.md) | criação, troca, integração e exclusão de branches |
| 05 | [Remotos, GitHub e Pull Requests](aulas/05-remotos-github-e-pull-request.md) | fetch, pull, push, remotes e revisão |
| 06 | [Conflitos e desfazer alterações](aulas/06-conflitos-e-desfazer-alteracoes.md) | conflitos, restore, revert e reset |
| 07 | [Stash, rebase e boas práticas](aulas/07-stash-rebase-e-boas-praticas.md) | troca de contexto, rebase e práticas seguras |
| 08 | [Do zero ao primeiro repositório](aulas/08-do-zero-ao-primeiro-repositorio.md) | prática guiada completa: pasta → commit → GitHub |
| 09 | [Colaboração no GitHub](aulas/09-colaboracao-no-github.md) | fork, clone, upstream, Issues, PRs, review e merge |
| 10 | [Erros comuns e diagnóstico](aulas/10-erros-comuns-e-diagnostico.md) | investigar erros e recuperar-se sem executar comandos no impulso |

Depois das aulas:

| Etapa | Material | Objetivo |
|---|---|---|
| 🧪 | [Desafios práticos](desafios/README.md) | praticar conceitos isoladamente |
| ✅ | [Soluções comentadas](desafios/solucoes/README.md) | comparar sua tentativa e entender o raciocínio |
| 🎓 | [Projeto final](projeto-final/README.md) | executar um fluxo completo semelhante ao trabalho em equipe |

---

## ⚡ Cheat sheet

> Use como referência rápida. Se um comando ainda parecer misterioso, abra a aula relacionada e entenda o estado antes/depois.

### Inspeção

```bash
git status                         # Mostra o estado atual dos arquivos e da staging area
git diff                           # Exibe alterações ainda não adicionadas à staging area
git diff --staged                  # Exibe alterações preparadas para o próximo commit
git log --oneline                  # Mostra o histórico de commits em formato resumido
git log --oneline --graph --all    # Exibe o histórico de todas as branches em formato de grafo
```

### Repositório e commits

```bash
git init                           # Inicializa um repositório Git no diretório atual
git clone <url>                    # Cria uma cópia local de um repositório remoto
git add <arquivo>                  # Adiciona um arquivo à staging area
git commit -m "mensagem"           # Cria um commit com as alterações preparadas
```

### Branches

```bash
git branch                         # Lista as branches locais
git switch -c <branch>             # Cria uma nova branch e muda para ela
git switch <branch>                # Muda para uma branch existente
git merge <branch>                 # Integra a branch informada à branch atual
git branch -d <branch>             # Exclui uma branch local já integrada
```

### Remotos

```bash
git remote -v                      # Lista os repositórios remotos e suas URLs
git fetch origin                   # Baixa referências e commits do remoto sem fazer merge
git pull                           # Baixa e integra alterações da branch remota acompanhada
git push -u origin <branch>        # Envia a branch ao remoto e define seu upstream
```

### Recuperação e contexto

```bash
git restore <arquivo>              # Descarta alterações não staged de um arquivo
git restore --staged <arquivo>     # Remove da staging sem apagar as alterações locais
git revert <commit>                # Cria um novo commit que desfaz outro commit
git stash                          # Guarda temporariamente alterações não commitadas
git stash pop                      # Restaura o stash mais recente e o remove da lista
```

> `git checkout` continua válido, mas este material usa `git switch` para branches e `git restore` para arquivos quando isso torna a intenção mais clara.

---

## 🌿 Entendendo branches, merge, ahead e behind

### O que é uma branch?

Uma **branch** é uma linha de desenvolvimento independente. Ela permite trabalhar em uma funcionalidade, correção ou experimento sem alterar diretamente a `main`.

```text
                 C──D   ← feature/login
                /
main       A────B
```

Neste exemplo:

- `A` e `B` já pertencem à `main`;
- `feature/login` nasceu a partir de `B`;
- `C` e `D` existem apenas na feature.

Um fluxo comum:

```bash
git switch main
git switch -c feature/login

# faz alterações...
git add .
git commit -m "feat: adiciona tela de login"
```

### O que é merge?

**Merge** integra o histórico de uma branch em outra.

Antes:

```text
                 C────D   ← feature/login
                /
main       A────B
```

```bash
git switch main
git merge feature/login
```

Um merge com commit de integração pode resultar em:

```text
                 C────D
                /      \
main       A────B────────E   ← merge
```

`E` representa o ponto em que os históricos foram unidos.

> Se a `main` não avançou durante o trabalho da feature, o Git também pode realizar um **fast-forward**, apenas avançando o ponteiro da branch.

### ⏩ Ahead

**Ahead** significa que sua branch possui commits que a branch de comparação não possui.

```text
main       A────B
                \
feature          C────D
```

```text
feature: 2 commits ahead of main
```

`C` e `D` são trabalho novo aguardando integração.

### ⏪ Behind

**Behind** significa que sua branch ainda não possui commits que chegaram à branch de comparação.

```text
main       A────B────E
                \
feature          C────D
```

```text
feature: 1 commit behind main
```

A `main` avançou com `E` e a feature ainda precisa incorporar essa mudança.

### 🔄 Ahead e behind ao mesmo tempo

```text
main       A────B────E
                \
feature          C────D
```

Comparando `feature` com `main`:

```text
2 ahead  → C e D existem apenas na feature
1 behind → E existe apenas na main
```

| Situação | Significado |
|---|---|
| `0 ahead / 0 behind` | os históricos comparados estão alinhados |
| `2 ahead / 0 behind` | sua branch possui somente commits novos |
| `0 ahead / 3 behind` | sua branch apenas está desatualizada |
| `2 ahead / 1 behind` | os dois lados avançaram separadamente |

### Atualizando uma branch que está behind

Uma abordagem didática:

```bash
git switch feature/login
git fetch origin
git merge origin/main
```

Depois:

```text
main       A────B────E
                \    \
feature          C────D────F
```

`F` integra na feature as mudanças da `main`.

Em algumas equipes, o fluxo usa `rebase`; siga a convenção do projeto.

### 🧭 Modelo mental rápido

```text
main está estável
       ↓
cria branch
       ↓
faz commits
       ↓
compara com main
       ↓
atualiza se estiver behind
       ↓
abre Pull Request
       ↓
review
       ↓
merge
       ↓
mudanças chegam à main
```

---

## 🧪 Aprender fazendo

Os [desafios práticos](desafios/README.md) treinam cinco competências separadamente:

1. primeiro repositório e commits;
2. branches e merge;
3. remoto e Pull Request;
4. conflito controlado;
5. recuperação.

Quando terminar, consulte as [soluções comentadas](desafios/solucoes/README.md) e compare o raciocínio, não apenas os comandos.

Depois faça o **[Projeto final — Do zero ao fluxo de equipe](projeto-final/README.md)**.

O projeto final inclui:

```text
Fork
 ↓
Clone
 ↓
origin + upstream
 ↓
Issue
 ↓
Branch
 ↓
Commits
 ↓
Ahead / Behind
 ↓
Conflito
 ↓
Pull Request
 ↓
Review
 ↓
Merge
 ↓
Revert
```

---

## 🧯 Quando algo der errado

Não execute comandos aleatórios para fazer a mensagem desaparecer.

Comece por:

```bash
git status
```

Depois investigue com ferramentas como:

```bash
git branch -vv
git remote -v
git log --oneline --graph --decorate --all
git diff
git diff --staged
```

A [Aula 10 — Erros comuns e diagnóstico](aulas/10-erros-comuns-e-diagnostico.md) cobre situações como:

- `not a git repository`;
- `Author identity unknown`;
- branch sem upstream;
- `remote origin already exists`;
- `non-fast-forward`;
- conflitos;
- alterações que impedem `switch`;
- detached HEAD;
- erro de SSH;
- arquivo adicionado à staging por engano;
- commit que precisa ser desfeito.

---

## 🤝 Aprenda colaboração praticando colaboração

Este repositório possui um **[guia de contribuição](CONTRIBUTING.md)** e um template de Pull Request.

Eles existem por dois motivos:

1. manter contribuições organizadas;
2. permitir que estudantes vejam como um projeto real estrutura branch, commit, PR e revisão.

Para treinar sem gerar contribuições desnecessárias no original, faça um fork e abra PRs dentro do **seu próprio fork**.

---

## ✅ Boas práticas rápidas

- Faça commits pequenos e com propósito claro.
- Consulte `git status` e `git diff` antes de registrar alterações.
- Evite commitar senhas, tokens, chaves e arquivos de ambiente.
- Trabalhe em branches para mudanças relevantes.
- Revise o diff antes de fazer merge.
- Não use `git push --force` como resposta automática a um push rejeitado.
- Em histórico compartilhado, `git revert` costuma ser mais seguro quando você precisa desfazer um commit sem reescrever o passado.
- Antes de comandos destrutivos, descubra exatamente qual trabalho será afetado.

---

## 📚 Documentação oficial

- [Documentação do Git](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [GitHub Skills](https://skills.github.com/)

---

## 💡 Sobre este repositório

Este material começou como um exercício de versionamento de código da **Digital Innovation One (DIO)** e evoluiu para uma trilha aberta de aprendizagem.

A proposta atual é simples:

> **Uma pessoa sem experiência prévia deve conseguir entrar aqui, seguir a trilha, praticar, errar em ambiente controlado e terminar capaz de usar Git e GitHub em um fluxo real de desenvolvimento.**

Se você encontrar uma explicação confusa ou um exemplo que possa ser melhorado, consulte o [CONTRIBUTING.md](CONTRIBUTING.md).

---

Feito para aprender Git **usando Git**. 🚀