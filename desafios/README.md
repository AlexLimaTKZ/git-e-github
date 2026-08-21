# 🧪 Desafios práticos

Use estes exercícios para transformar os conceitos estudados em prática.

> **Regra sugerida:** tente resolver sozinho primeiro. Se travar, volte à aula relacionada. Consulte as [soluções comentadas](solucoes/README.md) somente depois de formular sua própria tentativa.

## Como praticar melhor

Para cada desafio, tente registrar mentalmente:

```text
estado inicial
     ↓
comando escolhido
     ↓
estado resultante
```

Isso ajuda a aprender Git como um sistema de estados, em vez de decorar sequências.

---

## Desafio 01 — Primeiro repositório

**Objetivo:** praticar `init → status → add → commit → log`.

1. Crie uma pasta e inicialize um repositório Git.
2. Crie um `README.md`.
3. Consulte o estado com `git status`.
4. Adicione o README à staging area.
5. Antes do commit, consulte o que está staged.
6. Faça um commit com uma mensagem clara.
7. Consulte o histórico com `git log --oneline`.

### Você concluiu se consegue explicar

- o que significa `untracked`;
- o que muda depois de `git add`;
- por que `commit` não é a mesma coisa que `push`.

---

## Desafio 02 — Trabalhando com branch

**Objetivo:** entender isolamento de trabalho e integração.

1. Crie `feat/profile` a partir da `main`.
2. Altere o README.
3. Faça um commit na feature.
4. Visualize o histórico com `git log --oneline --graph --all`.
5. Volte para `main`.
6. Integre a feature com `git merge`.
7. Exclua a branch depois do merge.

### Você concluiu se consegue explicar

- onde o commit da feature existia antes do merge;
- por que a `main` não mudou enquanto você trabalhava na feature;
- o que o merge fez com o histórico.

---

## Desafio 03 — Repositório remoto e Pull Request

**Objetivo:** praticar o caminho local → remoto → revisão.

1. Publique um repositório no GitHub.
2. Crie uma branch local.
3. Faça uma alteração e um commit.
4. Execute `git push -u origin <branch>`.
5. Abra um Pull Request.
6. Leia a descrição do PR como se fosse outra pessoa do time.
7. Revise a aba **Files changed** antes de fazer merge.
8. Faça uma segunda alteração na mesma branch, commit e push, observando o PR ser atualizado.

### Você concluiu se consegue explicar

```text
push ≠ Pull Request ≠ merge
```

---

## Desafio 04 — Conflito controlado

**Objetivo:** perder o medo de conflitos.

1. Crie duas branches a partir do mesmo ponto.
2. Altere a mesma linha de um arquivo de maneiras diferentes.
3. Faça commits separados.
4. Integre a primeira branch.
5. Tente integrar a segunda.
6. Leia os marcadores de conflito.
7. Use `git status` para descobrir o que ainda precisa de atenção.
8. Resolva manualmente.
9. Finalize o merge.
10. Visualize o histórico com `--graph`.

### Você concluiu se consegue explicar

- por que o Git interrompeu o merge;
- o significado de `<<<<<<<`, `=======` e `>>>>>>>`;
- por que resolver conflito é uma decisão sobre o conteúdo, não apenas executar outro comando.

---

## Desafio 05 — Recuperação

**Objetivo:** aprender a corrigir erros sem usar comandos destrutivos no impulso.

Pratique em um repositório descartável:

- `git restore`;
- `git restore --staged`;
- `git revert`;
- `git stash` e `git stash pop`.

Para cada comando, anote:

```text
O que existia antes?
O que o comando alterou?
O trabalho continua recuperável?
O histórico foi reescrito?
```

> Faça experimentos destrutivos apenas em repositórios de treino. Errar de propósito em ambiente controlado é uma ótima forma de entender o Git.

---

# ✅ Soluções

Depois de tentar os desafios, compare sua abordagem com as [soluções comentadas](solucoes/README.md).

As soluções explicam o raciocínio por trás dos comandos e mostram que nem sempre existe uma única sequência correta.

---

# 🎓 Próximo passo: projeto final

Se você concluiu os cinco desafios, avance para o [Projeto final — Do zero ao fluxo de equipe](../projeto-final/README.md).

Ele reúne em uma única prática:

```text
Fork
 ↓
Clone
 ↓
Issue
 ↓
Branch
 ↓
Commits
 ↓
Ahead / Behind
 ↓
Conflito
 ↓
Pull Request
 ↓
Review
 ↓
Merge
 ↓
Revert
```

O projeto final foi pensado para verificar se você consegue usar os conceitos em conjunto, como aconteceria em um fluxo real de desenvolvimento.