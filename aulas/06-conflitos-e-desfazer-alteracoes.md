# 06 — Conflitos e como desfazer alterações

## Conflitos de merge

Um conflito acontece quando o Git não consegue decidir automaticamente qual versão manter.

Exemplo:

```text
<<<<<<< HEAD
const title = "Git";
=======
const title = "GitHub";
>>>>>>> feat/exemplo
```

Edite o arquivo, escolha o conteúdo correto, remova os marcadores e finalize:

```bash
git add arquivo.js
git commit
```

## Restaurando arquivo não preparado

```bash
git restore arquivo.js
```

## Removendo arquivo da staging area

```bash
git restore --staged arquivo.js
```

## Desfazendo um commit com segurança

Em histórico já compartilhado, prefira:

```bash
git revert <hash-do-commit>
```

Isso cria um novo commit que reverte o anterior sem reescrever o histórico.

## Reset

`git reset` altera referências locais e pode reescrever o histórico. Antes de utilizá-lo, entenda as diferenças entre `--soft`, `--mixed` e `--hard`.

> Evite `git reset --hard` quando não tiver certeza: ele pode descartar alterações locais.