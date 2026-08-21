# ✅ Soluções comentadas dos desafios

> Tente resolver cada desafio antes de consultar esta página. A solução não é uma sequência única e obrigatória: existem vários caminhos corretos no Git.

O objetivo aqui é explicar **por que** cada comando aparece, e não apenas entregar uma receita.

---

# Desafio 01 — Primeiro repositório

## Uma possível solução

```bash
mkdir desafio-git
cd desafio-git
git init
```

Crie um `README.md` e depois:

```bash
git status
```

O arquivo deve aparecer como `untracked`.

Prepare:

```bash
git add README.md
```

Confira:

```bash
git status
git diff --staged
```

Crie o commit:

```bash
git commit -m "docs: adiciona README inicial"
```

Veja o histórico:

```bash
git log --oneline
```

## O que você deveria ter percebido

```text
arquivo criado
    ↓
untracked
    ↓ git add
staged
    ↓ git commit
tracked no histórico
```

---

# Desafio 02 — Trabalhando com branch

Comece na `main`:

```bash
git switch main
```

Crie a feature:

```bash
git switch -c feat/profile
```

Altere o README.

```bash
git diff
git add README.md
git commit -m "docs: adiciona secao de perfil"
```

Confira o grafo:

```bash
git log --oneline --graph --all
```

Volte:

```bash
git switch main
```

Integre:

```bash
git merge feat/profile
```

Depois exclua a branch concluída:

```bash
git branch -d feat/profile
```

## Modelo mental

Antes:

```text
main       A
            \
feature     B
```

Depois do merge, dependendo do histórico, pode ocorrer fast-forward ou merge commit.

---

# Desafio 03 — Repositório remoto e Pull Request

Depois de criar um repositório no GitHub, configure o remote:

```bash
git remote add origin URL_DO_REPOSITORIO
```

Confira:

```bash
git remote -v
```

Crie a branch:

```bash
git switch -c docs/melhoria-readme
```

Faça uma alteração e commit:

```bash
git add README.md
git commit -m "docs: melhora README"
```

Publique a branch:

```bash
git push -u origin docs/melhoria-readme
```

No GitHub, abra um Pull Request de:

```text
docs/melhoria-readme → main
```

Antes do merge, revise **Files changed**.

## O aprendizado principal

```text
push envia a branch
PR propõe a integração
review inspeciona a mudança
merge integra na main
```

---

# Desafio 04 — Conflito controlado

Uma forma de provocar o conflito:

Comece com um arquivo contendo:

```text
linguagem favorita: indefinida
```

Na primeira branch:

```bash
git switch -c escolha/javascript
```

Altere para:

```text
linguagem favorita: JavaScript
```

Faça commit:

```bash
git add .
git commit -m "docs: escolhe javascript"
```

Volte à `main` e crie outra branch a partir do estado anterior:

```bash
git switch main
git switch -c escolha/python
```

Altere a mesma linha para:

```text
linguagem favorita: Python
```

Faça commit:

```bash
git add .
git commit -m "docs: escolhe python"
```

Integre uma das branches na `main`:

```bash
git switch main
git merge escolha/javascript
```

Depois tente integrar a outra:

```bash
git merge escolha/python
```

O arquivo deverá conter marcadores semelhantes a:

```text
<<<<<<< HEAD
linguagem favorita: JavaScript
=======
linguagem favorita: Python
>>>>>>> escolha/python
```

Escolha uma versão final, por exemplo:

```text
linguagens estudadas: JavaScript e Python
```

Remova os marcadores e conclua:

```bash
git add arquivo.txt
git commit
```

Confira:

```bash
git status
git log --oneline --graph --all
```

## O aprendizado principal

Git não "quebrou". Ele parou porque **não tinha informação suficiente para decidir por você**.

---

# Desafio 05 — Recuperação

## A) `git restore`

Altere um arquivo rastreado e confira:

```bash
git diff
```

Descarte a alteração não staged:

```bash
git restore arquivo.txt
```

Use apenas quando realmente quiser perder essa modificação local.

---

## B) `git restore --staged`

Faça uma alteração:

```bash
git add arquivo.txt
```

Agora remova apenas da staging:

```bash
git restore --staged arquivo.txt
```

A alteração continua no arquivo.

```text
staged
  ↓ restore --staged
modified
```

---

## C) `git stash`

Faça alterações sem commit e guarde temporariamente:

```bash
git stash
```

Confira:

```bash
git status
git stash list
```

Recupere:

```bash
git stash pop
```

---

## D) `git revert`

Crie um commit de teste:

```bash
git add .
git commit -m "test: cria alteracao temporaria"
```

Veja o hash:

```bash
git log --oneline
```

Desfaça preservando o histórico:

```bash
git revert HASH
```

O histórico passa a conter tanto o commit original quanto o commit que registra sua reversão.

---

# 🧠 Como saber se você realmente aprendeu?

Não se limite a confirmar que os comandos funcionaram. Tente responder:

- Por que `git add` não cria um commit?
- Por que uma branch permite trabalhar sem alterar a `main`?
- Por que um conflito exige uma decisão humana?
- Por que `restore --staged` não é igual a `restore`?
- Por que `revert` é adequado para histórico já compartilhado?

Se você consegue explicar o **estado anterior**, o **comando usado** e o **estado resultante**, você está entendendo Git em vez de apenas decorar comandos.