# 08 — Do zero ao primeiro repositório

> Se você nunca usou Git, esta é a aula para começar. O objetivo é sair de uma pasta comum no computador e terminar com um repositório publicado no GitHub.

## 1. O que você precisa instalar?

Você precisa do **Git** no computador e de uma conta no **GitHub**.

- Git: https://git-scm.com/downloads
- GitHub: https://github.com/

Depois da instalação, abra um terminal e confirme:

```bash
git --version
```

Se aparecer algo como `git version 2.x.x`, o Git está disponível.

> No Windows, o instalador do Git também oferece o **Git Bash**, um terminal bastante usado em cursos e tutoriais de Git.

---

## 2. Configure sua identidade

O Git registra quem criou cada commit. Configure seu nome e e-mail uma vez:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
```

Confira:

```bash
git config --global --list
```

### Modelo mental

```text
Você altera arquivos
       ↓
Git registra um commit
       ↓
o commit guarda autor + data + mensagem + alterações
```

---

## 3. Crie sua primeira pasta de projeto

```bash
mkdir meu-primeiro-repositorio
cd meu-primeiro-repositorio
```

Confira onde você está:

```bash
pwd
```

No PowerShell ou Prompt de Comando, `cd` também mostra/navega pelo caminho atual, dependendo do shell.

---

## 4. Transforme a pasta em um repositório Git

```bash
git init
```

Agora a pasta possui um diretório oculto `.git`, onde o Git guarda o histórico e as configurações locais do repositório.

```text
pasta comum
    ↓ git init
repositório Git
```

Confira:

```bash
git status
```

Você deverá ver que está em uma branch e ainda não existem commits.

---

## 5. Crie o primeiro arquivo

Crie um `README.md` pelo editor de texto ou terminal.

Exemplo de conteúdo:

```markdown
# Meu primeiro repositório

Estou aprendendo Git e GitHub.
```

Agora:

```bash
git status
```

O README deverá aparecer como **untracked**.

### O que significa untracked?

```text
arquivo criado
     ↓
Git percebe que ele existe
     ↓
mas ainda não está sendo acompanhado pelo histórico
```

---

## 6. Prepare o arquivo para o commit

```bash
git add README.md
```

Confira novamente:

```bash
git status
```

Agora ele está na **staging area**.

```text
Working Directory
       ↓ git add
   Staging Area
       ↓ git commit
Repository History
```

A staging area funciona como uma seleção do que entrará no próximo commit.

---

## 7. Crie seu primeiro commit

```bash
git commit -m "docs: adiciona README inicial"
```

Consulte o histórico:

```bash
git log --oneline
```

Você deverá ver algo semelhante a:

```text
8f20a31 docs: adiciona README inicial
```

O código no início é a identificação abreviada do commit.

---

## 8. Crie um repositório no GitHub

No GitHub:

1. clique em **New repository**;
2. escolha um nome;
3. defina como público ou privado;
4. se o projeto local já possui README, evite criar outro README pelo GitHub nesse momento;
5. crie o repositório.

O GitHub mostrará uma URL semelhante a:

```text
https://github.com/seu-usuario/meu-primeiro-repositorio.git
```

---

## 9. Conecte o repositório local ao GitHub

Adicione o remoto chamado `origin`:

```bash
git remote add origin https://github.com/seu-usuario/meu-primeiro-repositorio.git
```

Confira:

```bash
git remote -v
```

### O que é `origin`?

`origin` é apenas um **apelido convencional** para o repositório remoto principal.

```text
seu computador          GitHub
      │                    │
repositório local ─────► origin
```

---

## 10. Garanta que a branch principal se chama `main`

```bash
git branch -M main
```

Agora envie o histórico:

```bash
git push -u origin main
```

O `-u` registra que sua `main` local acompanha `origin/main`.

Depois disso, nos próximos envios normalmente basta:

```bash
git push
```

---

## 11. O ciclo que você acabou de executar

```text
criar arquivo
     ↓
git status
     ↓
git add
     ↓
git commit
     ↓
git push
     ↓
GitHub
```

Esse é o ciclo fundamental que aparecerá repetidamente durante todo o estudo de Git.

---

## 12. Faça uma segunda alteração sozinho

Altere o README e acrescente uma linha:

```markdown
Meu próximo objetivo é aprender branches.
```

Tente completar sem olhar a resposta:

1. descubra o que mudou;
2. prepare o arquivo;
3. crie outro commit;
4. envie ao GitHub.

<details>
<summary>Ver uma possível solução</summary>

```bash
git status
git diff
git add README.md
git commit -m "docs: adiciona proximo objetivo"
git push
```

</details>

---

## ✅ Checklist da aula

Ao terminar, você deve conseguir responder:

- [ ] Qual a diferença entre uma pasta comum e um repositório Git?
- [ ] Para que serve `git init`?
- [ ] O que é a staging area?
- [ ] Qual a diferença entre `git add`, `git commit` e `git push`?
- [ ] O que é `origin`?
- [ ] Onde fica o histórico: no computador, no GitHub ou nos dois?

> **Resposta da última pergunta:** depois do `push`, existe uma cópia do histórico localmente e outra no repositório remoto.