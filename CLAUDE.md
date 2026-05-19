# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install          # install dependencies
npm run dev          # run in development (ts-node, no build needed)
npm run build        # compile TypeScript to dist/
npm start            # run compiled output from dist/
npm test             # run tests
```

## Architecture

```
src/
  index.ts           # entry point and agent main loop
dist/                # compiled output — gitignored
.env                 # secrets (ANTHROPIC_API_KEY) — never committed
```

## Key Dependencies

- `@anthropic-ai/sdk` — Anthropic client for calling Claude
- `typescript` + `ts-node` — TypeScript toolchain (run src/ directly in dev)

## Environment

Copy `.env.example` to `.env` and set `ANTHROPIC_API_KEY` before running. The key is never committed.

## GitHub Sync

Repositório: https://github.com/ggdf00/meu-primeiro-agente

O projeto sincroniza automaticamente com o GitHub ao final de cada resposta do Claude Code. O hook `Stop` em `.claude/settings.json` executa:
1. `git add -A` — adiciona todas as alterações
2. Verifica se há mudanças a commitar
3. `git commit -m "auto: update from Claude Code"` — cria o commit
4. `git push` — envia para o GitHub

Para push manual: `git add -A && git commit -m "mensagem" && git push`
