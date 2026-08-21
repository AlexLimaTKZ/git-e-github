# 00 — Comece aqui

Se você **nunca usou Git ou GitHub**, comece por esta página.

O objetivo não é ensinar todos os comandos de uma vez. É preparar seu ambiente, explicar como estudar este material e evitar que palavras como *commit*, *branch* e *remote* pareçam pré-requisitos.

---

## O que você vai aprender neste repositório?

Ao terminar a trilha, a meta é que você consiga sair de:

```text
"Nunca usei Git"
```

para:

```text
criar repositório
      ↓
acompanhar alterações
      ↓
criar commits
      ↓
trabalhar com branches
      ↓
publicar no GitHub
      ↓
abrir Pull Requests
      ↓
resolver conflitos
      ↓
trabalhar em equipe
```

---

## 1. Instale o Git

Baixe pelo site oficial:

https://git-scm.com/downloads

Depois da instalação, abra um terminal e execute:

```bash
git --version
```

Se aparecer algo semelhante a:

```text
git version 2.x.x
```

o Git está disponível.

> No Windows, o instalador também oferece o Git Bash, bastante usado para praticar os comandos desta trilha.

---

## 2. Crie uma conta no GitHub

Acesse:

https://github.com/

### Git e GitHub não são a mesma coisa

Por enquanto, guarde apenas isto:

```text
Git
│
└── controla versões no seu computador

GitHub
│
└── hospeda repositórios Git e facilita colaboração
```

A [Aula 01](01-introducao-ao-git.md) aprofunda essa diferença.

---

## 3. Configure seu nome e e-mail

O Git registra quem criou cada commit.

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
```

Confira:

```bash
git config --global --list
```

Não é necessário decorar esses comandos. Essa configuração normalmente é feita apenas uma vez por computador.

---

## 4. Você não precisa dominar terminal

Para começar, estes comandos já são suficientes para navegar:

| Comando | Ideia |
|---|---|
| `pwd` | onde estou? |
| `ls` | o que existe nesta pasta? |
| `cd pasta` | entrar em uma pasta |
| `cd ..` | voltar uma pasta |
| `mkdir nome` | criar uma pasta |

> O comando exato pode variar entre Git Bash, PowerShell e Prompt de Comando. O importante é entender que Git e terminal são coisas diferentes: o terminal é apenas uma forma de conversar com o computador.

---

## 5. Vocabulário mínimo

Você encontrará estas palavras muitas vezes:

### Repositório

Uma pasta cujo histórico é acompanhado pelo Git.

### Commit

Um registro de alterações em um ponto do histórico.

### Branch

Uma linha de desenvolvimento que permite trabalhar sem alterar diretamente outra linha, como a `main`.

### Remote

Uma referência para outro repositório Git, normalmente hospedado em um serviço como GitHub.

### Pull Request

Uma proposta de integrar alterações de uma branch em outra, permitindo revisão antes do merge.

Não se preocupe se ainda não estiver totalmente claro. Cada conceito será reconstruído com exemplos nas próximas aulas.

---

## 6. Como estudar esta trilha

Siga a ordem:

```text
00 Comece aqui
      ↓
01 Conceitos fundamentais
      ↓
02 Configuração e primeiros passos
      ↓
03 Commits e histórico
      ↓
04 Branches e merge
      ↓
05 GitHub, remotos e Pull Requests
      ↓
06 Conflitos e recuperação
      ↓
07 Stash, rebase e boas práticas
      ↓
08 Prática guiada completa
      ↓
09 Colaboração no GitHub
      ↓
10 Erros comuns e diagnóstico
      ↓
Desafios
      ↓
Projeto final
```

---

## 7. Não copie comandos sem observar o estado

Durante os exercícios, faça frequentemente:

```bash
git status
```

O objetivo é perceber:

```text
antes do comando
      ↓
o que você executou
      ↓
o que mudou depois
```

Esse hábito é mais importante do que decorar dezenas de comandos.

---

## 8. Crie um repositório de laboratório

Durante o curso, é útil ter uma pasta descartável para testar sem medo:

```bash
mkdir laboratorio-git
cd laboratorio-git
git init
```

Use esse laboratório para provocar erros, conflitos e testar recuperação.

> Não pratique comandos destrutivos em projetos importantes enquanto ainda estiver entendendo seus efeitos.

---

## 9. Quando eu estiver perdido, o que faço?

Comece por:

```bash
git status
```

Depois procure entender a mensagem antes de executar outra coisa.

Mais tarde, a [Aula 10 — Erros comuns e diagnóstico](10-erros-comuns-e-diagnostico.md) ensina um processo sistemático de investigação.

---

## ✅ Pronto para começar?

Se o Git está instalado e você consegue executar:

```bash
git --version
```

avance para a [Aula 01 — Introdução ao Git](01-introducao-ao-git.md).

Você não precisa saber Git para começar este repositório. **A trilha existe justamente para construir esse conhecimento do zero.**