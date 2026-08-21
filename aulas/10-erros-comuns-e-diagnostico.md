# 10 — Erros comuns e como diagnosticar sozinho

Quem aprende Git não precisa decorar todos os erros. Precisa aprender a **investigar o estado do repositório antes de executar comandos no impulso**.

## Regra de ouro

Quando algo der errado, comece por:

```bash
git status
```

Depois pergunte:

```text
1. Em qual branch estou?
2. Tenho alterações locais?
3. Há algo na staging area?
4. Minha branch possui upstream?
5. O remoto está configurado corretamente?
6. A main avançou no remoto?
7. Estou no meio de merge ou rebase?
```

Comandos de diagnóstico úteis:

```bash
git status
git branch -vv
git remote -v
git log --oneline --graph --decorate --all
git diff
git diff --staged
```

---

## 1. `fatal: not a git repository`

### O que significa?

Você executou um comando Git em uma pasta que não pertence a um repositório.

```text
pasta atual
   │
   └── não existe .git aqui nem nos diretórios acima
```

### Investigue

```bash
pwd
ls
```

### Possíveis soluções

Entre na pasta correta:

```bash
cd caminho/do/projeto
```

ou, se realmente quiser iniciar um novo repositório:

```bash
git init
```

> Não use `git init` apenas para fazer o erro desaparecer. Primeiro confirme se você está na pasta certa.

---

## 2. `Author identity unknown`

### O que significa?

O Git ainda não sabe qual nome/e-mail registrar no commit.

### Resolva

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
```

Confira:

```bash
git config --global --list
```

---

## 3. `pathspec ... did not match any file(s) known to git`

Esse erro aparece, por exemplo, ao tentar trocar para uma branch que não existe ou informar um caminho incorreto.

```bash
git switch nome-que-nao-existe
```

### Investigue branches

```bash
git branch
git branch -a
```

Se a branch existe apenas no remoto:

```bash
git fetch origin
git switch nome-da-branch
```

---

## 4. `fatal: The current branch ... has no upstream branch`

### O que significa?

Sua branch existe localmente, mas ainda não está associada a uma branch remota.

```text
branch local ✅
branch remota ❌
upstream ❌
```

### Resolva no primeiro push

```bash
git push -u origin nome-da-branch
```

Depois disso, normalmente:

```bash
git push
```

já é suficiente.

---

## 5. `remote origin already exists`

### O que significa?

Já existe um remote chamado `origin`.

### Investigue antes de alterar

```bash
git remote -v
```

Se a URL estiver correta, não há nada para corrigir.

Se estiver errada:

```bash
git remote set-url origin NOVA_URL
```

Confira novamente:

```bash
git remote -v
```

---

## 6. `rejected` / `non-fast-forward` ao fazer push

Exemplo:

```text
! [rejected] main -> main (non-fast-forward)
```

### O que geralmente significa?

O remoto possui commits que sua branch local ainda não possui.

```text
local     A────B

remote    A────B────C
```

Enviar `B` como se `C` não existisse poderia sobrescrever a linha de histórico remota.

### Investigue

```bash
git fetch origin
git status
git log --oneline --graph --decorate --all
```

### Caminho comum

Integre as mudanças remotas conforme o fluxo do projeto:

```bash
git pull
```

ou faça explicitamente:

```bash
git fetch origin
git merge origin/main
```

Depois resolva eventuais conflitos e tente novamente:

```bash
git push
```

> Evite responder automaticamente com `git push --force`. Force push reescreve referências e pode apagar trabalho compartilhado.

---

## 7. `CONFLICT (content)`

### O que significa?

Git encontrou alterações incompatíveis na mesma região de um arquivo e não conseguiu decidir sozinho qual versão deve permanecer.

Exemplo:

```text
<<<<<<< HEAD
Título da versão atual
=======
Título da outra branch
>>>>>>> feature
```

### Processo de resolução

```text
1. git status
       ↓
2. abrir arquivos em conflito
       ↓
3. escolher/combinar o conteúdo correto
       ↓
4. remover marcadores <<<< ==== >>>>
       ↓
5. git add arquivo
       ↓
6. concluir merge/rebase
```

Em um merge:

```bash
git add arquivo.md
git commit
```

Se quiser abandonar o merge antes de concluí-lo:

```bash
git merge --abort
```

---

## 8. `Your local changes ... would be overwritten by checkout/switch`

### O que significa?

Você possui alterações locais que poderiam ser sobrescritas ao trocar de branch.

### Investigue

```bash
git status
git diff
```

Você possui três escolhas principais:

### A) As alterações estão prontas

```bash
git add .
git commit -m "..."
```

### B) Precisa guardar temporariamente

```bash
git stash
git switch outra-branch
```

Depois:

```bash
git stash pop
```

### C) Quer descartar

Somente se tiver certeza:

```bash
git restore arquivo
```

---

## 9. Estou em `detached HEAD`

Você pode ver algo parecido com:

```text
HEAD detached at a1b2c3d
```

### O que significa?

Você não está atualmente apontando para uma branch; está olhando diretamente para um commit.

```text
branch main ───► C

HEAD ─────────► A   (detached)
```

Isso é útil para inspeção, mas commits feitos ali podem ficar sem uma branch fácil de encontrar depois.

### Voltar para uma branch

```bash
git switch main
```

### Quero preservar um trabalho criado no detached HEAD

Crie uma branch apontando para o estado atual:

```bash
git switch -c rescue/meu-trabalho
```

---

## 10. `Permission denied (publickey)`

Esse erro normalmente aparece ao usar uma URL SSH sem que a autenticação SSH esteja configurada corretamente.

### Primeiro descubra qual URL está usando

```bash
git remote -v
```

URL SSH costuma parecer com:

```text
git@github.com:usuario/projeto.git
```

URL HTTPS:

```text
https://github.com/usuario/projeto.git
```

Se você ainda não configurou SSH, pode usar HTTPS ou seguir a documentação oficial do GitHub para configurar uma chave SSH.

> Não copie chaves privadas, tokens ou credenciais para Issues, chats públicos ou commits.

---

## 11. Fiz `git add` em um arquivo por engano

Se ainda não criou o commit:

```bash
git restore --staged arquivo
```

Isso remove o arquivo da staging area, mas mantém suas alterações locais.

```text
staged
  ↓ git restore --staged
modified
```

---

## 12. Fiz commit, mas quero desfazer com segurança

Se o commit já foi compartilhado, uma opção segura costuma ser:

```bash
git revert HASH_DO_COMMIT
```

Isso cria um **novo commit** que desfaz o anterior.

```text
A────B────C
          ↓ revert B
A────B────C────D
              D desfaz B
```

Assim o histórico compartilhado não é reescrito.

---

## 13. Tenho arquivos modificados e não sei o que alterei

Não comece apagando nada.

Use:

```bash
git status
git diff
```

Se o arquivo já está na staging:

```bash
git diff --staged
```

Isso responde **o que mudou** antes de você decidir **o que fazer**.

---

## 🧭 Árvore de diagnóstico rápido

```text
Algo deu errado
      │
      ├── git status
      │
      ├── problema de branch?
      │      └── git branch -vv
      │
      ├── problema de remoto?
      │      └── git remote -v
      │
      ├── histórico divergiu?
      │      ├── git fetch origin
      │      └── git log --oneline --graph --all
      │
      └── alteração desconhecida?
             ├── git diff
             └── git diff --staged
```

---

## 🚫 Comandos que merecem atenção extra

Alguns comandos podem reescrever ou descartar trabalho:

```text
git reset --hard
git clean -fd
git push --force
git branch -D
```

Eles não são "comandos proibidos", mas exigem que você saiba exatamente quais dados serão afetados.

Antes de executar algo destrutivo, pergunte:

```text
O trabalho existe em algum commit?
Existe cópia no remoto?
Estou mexendo apenas na minha branch?
Outra pessoa depende desse histórico?
```

---

## ✅ Método para aprender com erros

Quando encontrar um erro novo, registre quatro coisas:

```text
Erro
  ↓
O que significa
  ↓
Qual era o estado do repositório
  ↓
Como foi resolvido
```

Com o tempo, você deixa de decorar receitas e passa a reconhecer estados do Git.

---

## ✅ Checklist da aula

- [ ] Começo uma investigação com `git status`.
- [ ] Sei verificar branches com `git branch -vv`.
- [ ] Sei verificar remotes com `git remote -v`.
- [ ] Sei visualizar divergências com `git log --graph --all`.
- [ ] Entendo por que `push --force` não deve ser uma resposta automática.
- [ ] Sei diferenciar desfazer staging, alteração local e commit compartilhado.
- [ ] Consigo ler uma mensagem de erro antes de procurar uma solução.