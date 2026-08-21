# 🧪 Desafios práticos

Use estes exercícios para transformar os comandos estudados em prática.

## Desafio 01 — Primeiro repositório

1. Crie uma pasta e inicialize um repositório Git.
2. Crie um `README.md`.
3. Consulte o estado com `git status`.
4. Adicione o README à staging area.
5. Faça um commit com uma mensagem clara.
6. Consulte o histórico com `git log --oneline`.

## Desafio 02 — Trabalhando com branch

1. Crie `feat/profile` a partir da `main`.
2. Altere o README.
3. Faça um commit na feature.
4. Volte para `main`.
5. Integre a feature com `git merge`.
6. Exclua a branch depois do merge.

## Desafio 03 — Repositório remoto e Pull Request

1. Publique um repositório no GitHub.
2. Crie uma branch local.
3. Faça uma alteração e um commit.
4. Execute `git push -u origin <branch>`.
5. Abra um Pull Request.
6. Revise o diff antes de fazer merge.

## Desafio 04 — Conflito controlado

1. Crie duas branches alterando a mesma linha de um arquivo.
2. Faça commits diferentes em cada branch.
3. Tente integrá-las.
4. Leia os marcadores de conflito.
5. Resolva manualmente.
6. Finalize o merge.

## Desafio 05 — Recuperação

Pratique em um repositório descartável:

- `git restore`;
- `git restore --staged`;
- `git revert`;
- `git stash` e `git stash pop`.

> Faça experimentos destrutivos apenas em repositórios de treino. Errar de propósito em ambiente controlado é uma ótima forma de entender o Git.