# 11 — Coautoria e pair programming no GitHub

Em um trabalho colaborativo, nem sempre um commit é resultado do trabalho de apenas uma pessoa. Duas pessoas podem discutir a solução, escrever juntas, revisar cada decisão em tempo real e produzir uma única alteração.

O Git permite registrar essa colaboração usando **coautoria**.

---

## 1. O que é pair programming?

**Pair programming** é uma prática em que duas pessoas trabalham juntas na mesma tarefa.

Um modelo clássico divide os papéis em:

- **driver**: controla teclado/editor e escreve a alteração;
- **navigator**: acompanha a solução, identifica problemas, sugere caminhos e ajuda a tomar decisões.

Os papéis podem ser trocados durante a sessão.

```text
Pessoa A ── escreve / executa
     ↕
Pessoa B ── analisa / orienta
     ↓
solução construída em conjunto
```

A ideia principal não é simplesmente "uma pessoa escrever e outra assistir". As duas participam da construção da solução.

---

## 2. Por que registrar coautoria?

Quando um commit foi realmente construído por mais de uma pessoa, registrar coautoria ajuda o histórico a responder uma pergunta importante:

> Quem participou da criação desta mudança?

Sem coautoria:

```text
commit
└── autor: Pessoa A
```

Com coautoria:

```text
commit
├── autor: Pessoa A
└── coautor: Pessoa B
```

Isso torna o histórico mais fiel ao trabalho realizado.

---

## 3. Como funciona `Co-authored-by`

A coautoria é registrada na mensagem do commit usando um trailer:

```text
Co-authored-by: Nome <email-associado-ao-github>
```

Exemplo:

```bash
git commit -m "docs: melhora explicacao de pull requests

Co-authored-by: usuario-parceiro <usuario@users.noreply.github.com>"
```

O e-mail usado precisa estar associado à conta GitHub da pessoa para que a plataforma consiga relacionar a coautoria ao perfil correto.

---

## 4. Usando o e-mail `noreply` do GitHub

O GitHub permite que uma pessoa mantenha seu e-mail pessoal privado usando um endereço `noreply`.

Ele normalmente possui um formato semelhante a:

```text
ID+usuario@users.noreply.github.com
```

Esse endereço pode ser usado no trailer `Co-authored-by`.

> Não tente adivinhar o endereço de outra pessoa. Use somente o e-mail que ela disponibilizou ou confirmou para a colaboração.

---

## 5. Exemplo completo

Imagine que duas pessoas trabalharam juntas para melhorar a documentação de branches.

Depois de revisar o diff:

```bash
git status
git diff
git add aulas/04-branches-e-merge.md
git diff --staged
```

O commit pode ser criado assim:

```bash
git commit -m "docs: melhora modelo visual de branches

Co-authored-by: parceiro <email-do-parceiro>"
```

Depois:

```bash
git push -u origin docs/melhora-branches
```

E o fluxo continua normalmente:

```text
trabalho em dupla
      ↓
commit com Co-authored-by
      ↓
push
      ↓
Pull Request
      ↓
review
      ↓
merge
```

---

## 6. Coautor não é a mesma coisa que reviewer

Esses papéis representam contribuições diferentes.

| Papel | Participação |
|---|---|
| Autor | cria o commit |
| Coautor | participa da construção daquela mudança |
| Reviewer | revisa a mudança antes do merge |

Uma pessoa que apenas revisou um Pull Request não deve ser marcada automaticamente como coautora do commit.

---

## 7. Coautoria não deve ser usada apenas como decoração

O trailer `Co-authored-by` deve representar colaboração real.

Use quando duas ou mais pessoas participaram efetivamente da construção da alteração, por exemplo:

- pair programming;
- escrita conjunta de documentação;
- solução técnica construída em conjunto;
- implementação feita durante uma sessão colaborativa.

Evite adicionar nomes apenas para aumentar estatísticas ou preencher o histórico.

---

## 8. A conquista Pair Extraordinaire

O GitHub possui a conquista **Pair Extraordinaire**, relacionada a commits com coautoria que fazem parte de Pull Requests integrados.

O aprendizado importante não é apenas a conquista, mas entender o fluxo que ela representa:

```text
colaboração real
      ↓
coautoria registrada
      ↓
Pull Request
      ↓
merge
      ↓
histórico reconhece o trabalho em dupla
```

---

## 9. Como verificar a coautoria

Depois de criar o commit, confira a mensagem:

```bash
git log -1 --format=full
```

Você deve encontrar o trailer:

```text
Co-authored-by: Nome <email>
```

No GitHub, depois do push, abra o commit e verifique se os perfis envolvidos aparecem associados à contribuição.

---

## 10. Mais de um coautor

Um mesmo commit pode ter vários trailers:

```text
Co-authored-by: Pessoa B <email-b>
Co-authored-by: Pessoa C <email-c>
```

Cada trailer deve ficar em sua própria linha.

---

## 🧠 Modelo mental

```text
Quem digitou o commit?
        ↓
autor principal

Quem também construiu aquela mudança?
        ↓
Co-authored-by

Quem analisou depois?
        ↓
reviewer
```

São papéis diferentes e todos podem ser importantes em uma equipe.

---

## ✅ Exercício

Em um repositório de laboratório:

1. trabalhe em uma pequena alteração com outra pessoa;
2. revise o diff em conjunto;
3. crie um commit com `Co-authored-by`;
4. faça push para uma branch;
5. abra um Pull Request;
6. confira a autoria do commit no GitHub;
7. faça o merge depois da revisão.

Ao terminar, tente explicar com suas próprias palavras:

- por que coautor é diferente de reviewer;
- por que o e-mail precisa estar associado à conta GitHub;
- por que `Co-authored-by` fica na mensagem do commit;
- como a coautoria melhora a fidelidade do histórico.
