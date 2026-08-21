# 05 — Repositórios remotos, GitHub e Pull Requests

## Verificando remotes

```bash
git remote -v
```

Adicione um remote quando necessário:

```bash
git remote add origin https://github.com/usuario/repositorio.git
```

## Atualizando referências remotas

```bash
git fetch origin
```

`git fetch` baixa referências remotas sem integrar automaticamente as alterações na branch atual.

Para buscar e integrar alterações:

```bash
git pull
```

## Publicando uma branch

```bash
git push -u origin feat/minha-feature
```

O `-u` associa a branch local à branch remota correspondente.

## Pull Request

Um Pull Request (PR) propõe a integração de uma branch em outra. Em um fluxo comum:

```text
feat/minha-feature
       ↓ push
GitHub
       ↓ Pull Request
review / ajustes
       ↓ merge
main
```

Um bom PR deve explicar:

- o que mudou;
- por que a mudança foi necessária;
- como validar;
- riscos ou pontos de atenção, quando existirem.

Pull Requests tornam a colaboração mais segura porque permitem revisão antes da integração.