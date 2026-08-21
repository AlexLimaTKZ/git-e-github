# 🤝 Como contribuir

Este repositório também pode ser usado para praticar um fluxo de colaboração real no GitHub.

Antes de contribuir, leia este guia inteiro.

## 1. Antes de começar

Confira se já existe uma Issue ou Pull Request sobre a mesma mudança.

Uma boa contribuição deve ter um objetivo claro, por exemplo:

- corrigir um erro técnico;
- melhorar uma explicação;
- adicionar um exemplo útil;
- corrigir ortografia;
- criar um exercício que ajude no aprendizado.

Evite mudanças grandes sem contexto ou alterações que não estejam relacionadas ao objetivo do repositório.

---

## 2. Faça um fork

Crie um fork do repositório para sua conta e clone:

```bash
git clone https://github.com/SEU-USUARIO/git-e-github.git
cd git-e-github
```

Adicione o original como `upstream`:

```bash
git remote add upstream https://github.com/AlexLimaTKZ/git-e-github.git
```

Confira:

```bash
git remote -v
```

---

## 3. Atualize a `main`

```bash
git switch main
git fetch upstream
git merge upstream/main
```

Sincronize seu fork:

```bash
git push origin main
```

---

## 4. Crie uma branch

Use um nome que descreva o tipo de alteração:

```text
docs/melhora-explicacao-branches
fix/corrige-comando
docs/adiciona-exercicio
```

Exemplo:

```bash
git switch -c docs/melhora-explicacao-branches
```

---

## 5. Faça mudanças focadas

Antes do commit:

```bash
git status
git diff
```

Prepare apenas o que pertence à tarefa:

```bash
git add caminho/do/arquivo.md
```

Confira:

```bash
git diff --staged
```

---

## 6. Use mensagens de commit claras

Exemplos:

```text
docs: explica diferenca entre fetch e pull
fix: corrige exemplo de git restore
docs: adiciona exercicio sobre conflitos
```

Evite mensagens como:

```text
update
mudancas
arrumei
final
```

---

## 7. Envie sua branch

```bash
git push -u origin nome-da-branch
```

---

## 8. Abra um Pull Request

No PR, explique:

- o que mudou;
- por que a alteração ajuda;
- como você verificou o resultado.

Use o template disponibilizado pelo repositório.

---

## 9. Revise seu próprio diff

Antes de pedir revisão, confira a aba **Files changed** e verifique:

- [ ] apenas arquivos relacionados à tarefa foram alterados;
- [ ] não existem tokens, senhas ou dados pessoais;
- [ ] os comandos estão corretos;
- [ ] links funcionam;
- [ ] não existem marcadores de conflito;
- [ ] o texto está compreensível para iniciantes;
- [ ] exemplos perigosos possuem contexto e aviso.

---

## 10. Recebeu feedback?

Faça os ajustes na **mesma branch**:

```bash
git add .
git commit -m "docs: ajusta explicacao apos review"
git push
```

O mesmo Pull Request será atualizado automaticamente.

---

## 11. Princípios deste material

Ao escrever conteúdo educacional:

1. explique o conceito antes do comando;
2. mostre o estado antes e depois quando possível;
3. use exemplos visuais para histórico e branches;
4. não ensine comandos destrutivos como solução automática;
5. diferencie práticas seguras de atalhos perigosos;
6. prefira exemplos pequenos e reproduzíveis;
7. escreva para alguém que ainda não domina o vocabulário.

---

## 🧠 Fluxo resumido

```text
Issue/objetivo
      ↓
Fork
      ↓
Branch
      ↓
Alteração
      ↓
status + diff
      ↓
Commit
      ↓
Push
      ↓
Pull Request
      ↓
Review
      ↓
Ajustes
      ↓
Merge
```

Obrigado por ajudar a tornar este material mais útil para quem está aprendendo Git e GitHub.