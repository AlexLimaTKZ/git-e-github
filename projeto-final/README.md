# 🎓 Projeto final — Do zero ao fluxo de equipe

Este projeto reúne os principais conceitos estudados no repositório em uma única jornada prática.

A proposta é simular o trabalho de uma pessoa desenvolvedora entrando em um projeto colaborativo.

> Faça este projeto em um **fork seu** deste repositório. Assim você pode criar branches, commits e Pull Requests sem alterar o projeto original.

---

# Cenário

Você entrou em um projeto fictício chamado **DevNotes**.

Sua primeira tarefa é documentar um pequeno guia de boas práticas para pessoas novas no time.

Durante a tarefa, você deverá:

```text
Fork
 ↓
Clone
 ↓
Configurar remotes
 ↓
Issue
 ↓
Branch
 ↓
Commits
 ↓
Atualizar branch
 ↓
Resolver conflito
 ↓
Push
 ↓
Pull Request
 ↓
Revisar diff
 ↓
Merge
 ↓
Limpeza
```

---

## Etapa 1 — Faça um fork

No GitHub, faça um fork deste repositório para sua própria conta.

Depois clone **o seu fork**:

```bash
git clone https://github.com/SEU-USUARIO/git-e-github.git
cd git-e-github
```

Confira:

```bash
git remote -v
```

Neste momento, `origin` deve apontar para seu fork.

---

## Etapa 2 — Configure o `upstream`

Adicione o projeto original como `upstream`:

```bash
git remote add upstream https://github.com/AlexLimaTKZ/git-e-github.git
```

Confira:

```bash
git remote -v
```

Modelo mental:

```text
upstream → projeto original
origin   → seu fork
```

---

## Etapa 3 — Crie uma Issue no seu fork

Abra uma Issue no **seu fork** com o título:

```text
Adicionar guia de boas práticas para novos devs
```

Use uma descrição semelhante a:

```markdown
## Objetivo
Criar um pequeno guia de onboarding para novos membros do time.

## Critérios de aceite
- criar arquivo `projeto-final/entrega.md`;
- incluir pelo menos 5 boas práticas;
- usar Markdown;
- trabalhar em uma branch separada;
- abrir Pull Request antes de integrar na main.
```

A Issue representa a tarefa antes da implementação.

---

## Etapa 4 — Atualize sua `main`

Antes de começar:

```bash
git switch main
git fetch upstream
git merge upstream/main
```

Depois envie a atualização ao seu fork, se necessário:

```bash
git push origin main
```

---

## Etapa 5 — Crie a branch da tarefa

```bash
git switch -c docs/onboarding-devs
```

Confira:

```bash
git branch
```

---

## Etapa 6 — Crie sua entrega

Crie:

```text
projeto-final/entrega.md
```

Sugestão de estrutura:

```markdown
# Guia de onboarding

## 1. Atualize sua branch antes de começar
...

## 2. Evite commits gigantes
...

## 3. Revise o diff antes do commit
...

## 4. Não envie segredos para o Git
...

## 5. Abra Pull Requests pequenos
...
```

Não copie exatamente o exemplo. Escreva com suas próprias palavras.

---

## Etapa 7 — Inspecione antes de commitar

```bash
git status
git diff
```

Depois:

```bash
git add projeto-final/entrega.md
git diff --staged
```

Se estiver correto:

```bash
git commit -m "docs: adiciona guia de onboarding"
```

---

## Etapa 8 — Faça um segundo commit

Adicione ao arquivo uma seção chamada:

```markdown
## Checklist antes de abrir um Pull Request
```

Inclua pelo menos 4 itens.

Depois:

```bash
git diff
git add projeto-final/entrega.md
git commit -m "docs: adiciona checklist de pull request"
```

Confira o histórico:

```bash
git log --oneline --graph --decorate --all
```

Sua branch deve estar pelo menos **2 commits ahead** da `main`.

---

# Etapa 9 — Simule a `main` avançando

Agora vamos provocar uma situação comum de equipe.

Abra outro terminal ou use temporariamente a `main`:

```bash
git switch main
```

Crie um arquivo:

```text
projeto-final/aviso.md
```

Conteúdo:

```markdown
# Aviso

Antes de iniciar uma tarefa, consulte as regras do projeto.
```

Faça commit:

```bash
git add projeto-final/aviso.md
git commit -m "docs: adiciona aviso do projeto final"
git push origin main
```

Agora volte para sua feature:

```bash
git switch docs/onboarding-devs
```

Visualmente:

```text
main                 A────M
                      \
feature                B────C
```

Sua feature está:

```text
ahead  → possui B e C
behind → não possui M
```

---

## Etapa 10 — Atualize sua branch

```bash
git fetch origin
git merge origin/main
```

Confira:

```bash
git log --oneline --graph --decorate --all
```

Sua branch agora deve conter também o commit da `main`.

---

# Etapa 11 — Crie e resolva um conflito controlado

Esta etapa é propositalmente mais avançada.

## 11.1 Na feature

Ainda em `docs/onboarding-devs`, acrescente ao final de `projeto-final/aviso.md`:

```markdown
Priorize branches pequenas e fáceis de revisar.
```

Faça commit:

```bash
git add projeto-final/aviso.md
git commit -m "docs: complementa aviso na feature"
```

## 11.2 Na main

Troque para `main`:

```bash
git switch main
```

Altere **a mesma linha** do arquivo para:

```markdown
Priorize Pull Requests pequenos e fáceis de revisar.
```

Faça commit:

```bash
git add projeto-final/aviso.md
git commit -m "docs: complementa aviso na main"
```

## 11.3 Volte para a feature e tente atualizar

```bash
git switch docs/onboarding-devs
git merge main
```

O Git deverá indicar conflito.

Use:

```bash
git status
```

Abra `projeto-final/aviso.md` e procure:

```text
<<<<<<< HEAD
...
=======
...
>>>>>>> main
```

Escolha uma versão final coerente, por exemplo:

```markdown
Priorize branches e Pull Requests pequenos e fáceis de revisar.
```

Remova os marcadores e conclua:

```bash
git add projeto-final/aviso.md
git commit
```

Confira novamente:

```bash
git status
git log --oneline --graph --decorate --all
```

---

## Etapa 12 — Envie sua branch

```bash
git push -u origin docs/onboarding-devs
```

---

## Etapa 13 — Abra o Pull Request

No **seu fork**, abra:

```text
docs/onboarding-devs → main
```

Use uma descrição parecida com:

```markdown
## O que mudou
- adiciona guia de onboarding;
- adiciona checklist para Pull Requests;
- complementa aviso do projeto final.

## Como revisei
- conferi `git diff`;
- revisei os commits;
- resolvi conflito com a main;
- confirmei que a branch está atualizada.
```

---

## Etapa 14 — Revise o próprio diff

Antes do merge, abra a aba **Files changed**.

Procure por:

```text
arquivos inesperados?
segredos?
texto duplicado?
marcadores de conflito?
nomes ruins?
alterações que não pertencem à tarefa?
```

Se encontrar algo errado, **não abra outro PR**.

Corrija na mesma branch:

```bash
git add .
git commit -m "docs: corrige revisao final"
git push
```

O PR será atualizado.

---

## Etapa 15 — Faça o merge

Depois da revisão, faça o merge no seu fork.

Em seguida:

```bash
git switch main
git pull origin main
```

Exclua a branch local:

```bash
git branch -d docs/onboarding-devs
```

---

# Etapa bônus — Desfaça um commit com `revert`

Crie propositalmente um commit simples na `main` do seu fork:

```bash
echo "linha temporaria" >> projeto-final/aviso.md
git add projeto-final/aviso.md
git commit -m "docs: adiciona linha temporaria"
```

Veja o hash:

```bash
git log --oneline
```

Desfaça sem reescrever o histórico:

```bash
git revert HASH_DO_COMMIT
```

Compare:

```text
commit errado continua no histórico
             ↓
novo commit registra a reversão
```

---

# ✅ Critérios de conclusão

Você concluiu o projeto se conseguiu:

- [ ] fazer fork e clone;
- [ ] diferenciar `origin` e `upstream`;
- [ ] criar uma Issue;
- [ ] criar branch a partir da `main`;
- [ ] fazer pelo menos dois commits claros;
- [ ] usar `status`, `diff` e `diff --staged`;
- [ ] identificar branch ahead/behind;
- [ ] atualizar uma branch que ficou behind;
- [ ] resolver um conflito manualmente;
- [ ] fazer push de uma branch;
- [ ] abrir e revisar um Pull Request;
- [ ] atualizar o mesmo PR com novos commits;
- [ ] fazer merge;
- [ ] excluir uma branch concluída;
- [ ] usar `revert` para desfazer um commit.

---

# 🧠 Perguntas finais

Tente responder sem consultar as aulas:

1. Qual a diferença entre Git e GitHub?
2. Qual a diferença entre `add`, `commit` e `push`?
3. Por que trabalhar em branch em vez de diretamente na `main`?
4. O que significa uma branch estar `2 ahead / 1 behind`?
5. Qual a diferença entre `fetch` e `pull`?
6. O que um Pull Request adiciona ao fluxo que um simples `push` não adiciona?
7. Como você investigaria um `non-fast-forward`?
8. Quando `revert` costuma ser mais seguro do que reescrever o histórico?

Se você consegue explicar essas respostas com suas próprias palavras e concluir o projeto sem copiar comandos mecanicamente, já formou uma base sólida para trabalhar com Git e GitHub em projetos reais.