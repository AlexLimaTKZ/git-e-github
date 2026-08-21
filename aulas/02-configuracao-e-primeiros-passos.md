# 02 — Configuração e primeiros passos

## Identidade do Git

Antes dos primeiros commits, configure nome e e-mail:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "voce@exemplo.com"
```

Confira a configuração:

```bash
git config --list
```

## Criando um repositório

```bash
mkdir meu-projeto
cd meu-projeto
git init
```

Ou clone um repositório existente:

```bash
git clone https://github.com/usuario/repositorio.git
```

## Comandos de navegação úteis

| Comando | Função |
|---|---|
| `pwd` | mostra o diretório atual |
| `ls` | lista arquivos e diretórios |
| `cd pasta` | entra em um diretório |
| `cd ..` | volta um nível |
| `mkdir pasta` | cria um diretório |

> Alguns comandos variam entre Bash, PowerShell e Prompt de Comando. O Git funciona da mesma forma; o que muda é o shell usado para navegar pelos arquivos.