# 07 — Stash, rebase e boas práticas

## Guardando alterações temporariamente

Quando precisar trocar de contexto sem criar um commit incompleto:

```bash
git stash
git stash list
git stash pop
```

## Rebase

`git rebase` reaplica commits sobre outra base e pode deixar um histórico linear:

```bash
git switch feat/minha-feature
git fetch origin
git rebase origin/main
```

Como o rebase reescreve commits, evite usá-lo de forma descuidada em branches compartilhadas.

## Boas práticas

- faça commits pequenos e com propósito claro;
- escreva mensagens que expliquem a intenção da mudança;
- evite trabalhar diretamente na `main` quando a mudança merece revisão;
- confira `git status` e `git diff` antes do commit;
- atualize sua base antes de integrar uma branch longa;
- não versione segredos, chaves ou arquivos de ambiente;
- prefira Pull Requests para mudanças relevantes.

## Checklist antes do push

```bash
git status
git diff --staged
git log --oneline -5
git push
```

Mais importante que memorizar dezenas de comandos é saber inspecionar o estado do repositório antes de executar operações destrutivas.