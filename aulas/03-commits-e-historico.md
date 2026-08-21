# 03 — Commits e histórico

## Preparando alterações

Use `git status` para entender o estado do repositório:

```bash
git status
```

Veja o que mudou:

```bash
git diff
```

Adicione apenas os arquivos que devem entrar no próximo commit:

```bash
git add README.md
git add src/app.js
```

Confira o conteúdo preparado:

```bash
git diff --staged
```

## Criando commits

```bash
git commit -m "docs: adiciona guia de commits"
```

Prefira mensagens que expliquem a intenção da mudança. Exemplos:

```text
feat: adiciona formulário de login
fix: corrige validação do e-mail
docs: documenta fluxo de branches
refactor: simplifica função de busca
```

## Consultando o histórico

```bash
git log
git log --oneline
git log --oneline --graph --all
```

O último formato é especialmente útil para visualizar branches e merges.