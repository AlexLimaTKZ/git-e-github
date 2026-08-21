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
