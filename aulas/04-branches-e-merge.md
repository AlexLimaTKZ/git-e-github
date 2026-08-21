# 04 — Branches e merge

Branches permitem desenvolver alterações isoladamente sem modificar diretamente a linha principal do projeto.

## Criando e trocando de branch

```bash
git branch
git switch -c feat/minha-feature
```

Para trocar para uma branch existente:

```bash
git switch main
```

`git checkout` ainda é válido, mas `git switch` deixa a intenção de troca de branch mais explícita.

## Fazendo merge

Depois de concluir uma alteração:

```bash
git switch main
git merge feat/minha-feature
```

Depois, se a branch não for mais necessária:

```bash
git branch -d feat/minha-feature
```

## Fluxo simplificado

```text
main        A────B──────────E
                 \        /
feature           C──────D
```

A branch `feature` nasce a partir da `main`, recebe novos commits e depois é integrada novamente.

## Antes do merge

Confira sempre:

```bash
git status
git log --oneline --graph --all
```

Isso reduz a chance de integrar alterações inesperadas.