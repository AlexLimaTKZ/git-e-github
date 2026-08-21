# 01 — Introdução ao Git

## O que é Git?

Git é um sistema de controle de versão distribuído. Ele registra alterações feitas em arquivos ao longo do tempo e permite comparar versões, restaurar estados anteriores e colaborar com outras pessoas sem sobrescrever trabalho.

## Git x GitHub

- **Git** é a ferramenta de versionamento executada localmente.
- **GitHub** é uma plataforma de hospedagem de repositórios Git e colaboração.

## Modelo mental básico

```text
Working Directory
      ↓ git add
  Staging Area
      ↓ git commit
Local Repository
      ↓ git push
Remote Repository (GitHub)
```

## Termos importantes

- **repositório:** projeto versionado pelo Git;
- **commit:** registro de um estado do projeto;
- **branch:** linha paralela de desenvolvimento;
- **remote:** referência para um repositório remoto;
- **staging area:** área intermediária onde selecionamos o que fará parte do próximo commit.

## Primeiro fluxo

```bash
git init
git status
git add README.md
git commit -m "docs: adiciona README"
```

O objetivo não é decorar comandos, mas entender o fluxo: modificar → selecionar → registrar.