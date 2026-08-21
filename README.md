# 📚 Git e GitHub — Resumos e Prática

Repositório de estudos sobre **Git, GitHub e versionamento de código**, desenvolvido a partir do curso da [Digital Innovation One (DIO)](https://www.dio.me/) e expandido com exemplos, exercícios e boas práticas usadas em projetos reais.

## 🎯 Objetivo

Mais do que reunir comandos, este repositório busca documentar o **modelo mental do Git**: entender onde cada alteração está, como o histórico é construído e como trabalhar de forma segura em equipe.

```text
Working Directory
      ↓ git add
  Staging Area
      ↓ git commit
Local Repository
      ↓ git push
Remote Repository (GitHub)
```

## 🧠 Trilha de estudo

| # | Conteúdo | Resumo |
|---|---|---|
| 01 | [Introdução ao Git](aulas/01-introducao-ao-git.md) | Git x GitHub, repositório, commit, branch e staging area |
| 02 | [Configuração e primeiros passos](aulas/02-configuracao-e-primeiros-passos.md) | identidade, `git init`, `git clone` e terminal |
| 03 | [Commits e histórico](aulas/03-commits-e-historico.md) | status, diff, staging, commits e logs |
| 04 | [Branches e merge](aulas/04-branches-e-merge.md) | criação, troca, integração e exclusão de branches |
| 05 | [Remotos, GitHub e Pull Requests](aulas/05-remotos-github-e-pull-request.md) | fetch, pull, push, remotes e revisão |
| 06 | [Conflitos e desfazer alterações](aulas/06-conflitos-e-desfazer-alteracoes.md) | conflitos, restore, revert e reset |
| 07 | [Stash, rebase e boas práticas](aulas/07-stash-rebase-e-boas-praticas.md) | troca de contexto, histórico e práticas seguras |

## ⚡ Cheat sheet

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
git init                           # Inicializa um novo repositório Git no diretório atual
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
git restore <arquivo>              # Descarta alterações não adicionadas de um arquivo
git restore --staged <arquivo>     # Remove um arquivo da staging area sem apagar suas alterações
git revert <commit>                # Cria um novo commit que desfaz os efeitos de outro commit
git stash                          # Guarda temporariamente alterações não commitadas
git stash pop                      # Restaura o stash mais recente e o remove da lista
```

> `git checkout` continua válido, mas nos exemplos modernos deste material `git switch` é usado para branches e `git restore` para restaurar arquivos, deixando a intenção de cada comando mais clara.

## 🌿 Entendendo branches, merge, ahead e behind

### O que é uma branch?

Uma **branch** é uma linha de desenvolvimento independente. Ela permite trabalhar em uma funcionalidade, correção ou experimento sem alterar diretamente a `main`.

```text
                 C──D   ← feature/login
                /
main       A────B
```

Neste exemplo:

- `A` e `B` são commits que já pertencem à `main`;
- a branch `feature/login` nasceu a partir de `B`;
- `C` e `D` são novos commits feitos somente na branch de feature.

Um fluxo comum é:

```bash
git switch main
git switch -c feature/login

# faz alterações...
git add .
git commit -m "feat: adiciona tela de login"
```

### O que é merge?

**Merge** é a operação usada para integrar o histórico de uma branch em outra.

Antes do merge:

```text
                 C────D   ← feature/login
                /
main       A────B
```

Para integrar a feature:

```bash
git switch main
git merge feature/login
```

Depois de um merge com commit de integração, o histórico pode ficar assim:

```text
                 C────D
                /      \
main       A────B────────E   ← merge
```

O commit `E` representa o ponto em que os históricos foram unidos.

> Se a `main` não recebeu nenhum commit enquanto a feature era desenvolvida, o Git também pode fazer um **fast-forward**, apenas avançando o ponteiro da `main` até o commit mais recente.

### ⏩ O que significa estar "ahead"?

No GitHub, **ahead** significa que sua branch possui commits que ainda não existem na branch usada como comparação.

```text
main       A────B
                \
feature          C────D
```

Aqui a `feature` está **2 commits ahead da `main`**, pois possui `C` e `D` a mais.

```text
feature: 2 commits ahead of main
```

Isso normalmente significa: **há trabalho novo nessa branch esperando para ser integrado**.

### ⏪ O que significa estar "behind"?

**Behind** significa que sua branch ainda não possui commits que já chegaram à branch de comparação.

```text
main       A────B────E
                \
feature          C────D
```

A `feature` está **1 commit behind da `main`**, pois ainda não possui `E`.

```text
feature: 1 commit behind main
```

Isso significa: **a `main` avançou e sua branch precisa ser atualizada**.

### 🔄 Ahead e behind ao mesmo tempo

Uma branch pode estar à frente e atrás simultaneamente:

```text
main       A────B────E
                \
feature          C────D
```

Comparando `feature` com `main`:

```text
2 commits ahead   → C e D existem apenas na feature
1 commit behind   → E existe apenas na main
```

Ou seja, os dois lados possuem commits exclusivos.

| Situação | Significado |
|---|---|
| `0 ahead / 0 behind` | as branches apontam para o mesmo histórico |
| `2 ahead / 0 behind` | sua branch só possui commits novos |
| `0 ahead / 3 behind` | sua branch apenas está desatualizada |
| `2 ahead / 1 behind` | as duas branches avançaram separadamente |

### Como atualizar uma branch que está behind?

Uma forma didática é trazer a `main` para a branch atual:

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

`F` integra na feature as mudanças que haviam chegado à `main`.

Em equipes, também pode ser usado `rebase`, dependendo do fluxo adotado pelo projeto.

### 🧭 Modelo mental rápido

```text
1. main está estável
       ↓
2. cria uma branch
       ↓
3. faz commits na branch
       ↓
4. compara com a main
       ↓
5. atualiza se estiver behind
       ↓
6. abre Pull Request
       ↓
7. revisa e faz merge
       ↓
8. mudanças chegam à main
```

Resumo:

```text
branch  = linha paralela de desenvolvimento
commit  = ponto salvo no histórico
merge   = integração de históricos
ahead   = commits que só sua branch possui
behind  = commits da outra branch que a sua ainda não possui
```

## 🧪 Pratique

Acesse os [desafios práticos](desafios/README.md) para exercitar:

- primeiro repositório e commits;
- branches e merge;
- publicação no GitHub e Pull Requests;
- resolução de conflitos;
- restauração e recuperação de alterações.

## ✅ Boas práticas rápidas

- Faça commits pequenos e com propósito claro.
- Consulte `git status` e `git diff` antes de registrar alterações.
- Evite commitar segredos, tokens e arquivos de ambiente.
- Trabalhe em branches para mudanças relevantes.
- Revise o diff antes de fazer merge.
- Em histórico compartilhado, prefira `git revert` quando precisar desfazer um commit sem reescrever o histórico.

## 📚 Documentação oficial

- [Documentação do Git](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [GitHub Skills](https://skills.github.com/)

## 💡 Sobre este repositório

Este material começou como um exercício do curso de versionamento de código da DIO e evoluiu para um caderno de referência pessoal. A proposta é continuar refinando o conteúdo à medida que novos conceitos forem praticados em projetos reais.

---

Feito para aprender Git usando Git. 🚀
