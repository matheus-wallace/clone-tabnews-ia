# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Projeto

Clone do [TabNews](https://www.tabnews.com.br) construído com agentes de IA (ver `README.md`).

Responda e escreva mensagens de commit e documentação em **português**.

## Antes de começar

Este arquivo descreve convenções e decisões, não o estado atual do código. Leia
`package.json` para saber quais dependências e scripts existem de fato, e `app/` para
as rotas que já existem. Não confie na memória nem neste arquivo para versões e
inventário.

## Comandos

Os scripts disponíveis estão em `package.json`. Hoje são apenas `dev` (sobe em
`localhost:3000`), `build` e `start`.

Não há suíte de testes, linter ou formatador configurados. Confira os scripts em
`package.json` antes de afirmar que rodou verificação — não invente `npm test` ou
`npm run lint`. Para validar uma alteração, rode `npm run build` e/ou suba o
`npm run dev` e faça uma requisição à rota afetada.

## Arquitetura e convenções

- **Stack:** Next.js + React, em JavaScript puro. Sem TypeScript — para adotá-lo, basta
  criar um arquivo `.ts`/`.tsx` e o Next gera o `tsconfig.json` sozinho no próximo build.
- **App Router** (diretório `app/`). Não há Pages Router; não crie `pages/`.
- `app/layout.js` é o root layout (define o `lang` do `<html>` e o `metadata`).
  Cada rota é um diretório sob `app/` com seu próprio `page.js`.
- Componentes são Server Components por padrão; só marque `"use client"` onde houver
  estado, efeito ou handler de evento.
- Idioma da interface: português (`lang="pt-BR"`).

## Minimalismo é um requisito, não um descuido

O projeto foi iniciado com a instrução explícita de usar o mínimo de código necessário.
A ausência de arquivos de configuração e ferramental (config do Next, TypeScript,
ESLint, Prettier, Tailwind) é **deliberada** — nada disso é necessário para o projeto
rodar.

Não adicione configuração, dependência ou ferramenta por iniciativa própria, nem trate
a falta delas como lacuna a corrigir. Proponha e espere confirmação.

## Dependências são fixadas em versão exata

O `package.json` declara versões exatas, sem `^` ou `~`. Isso é intencional: mantenha o
formato ao adicionar dependências.

Alertas do `npm audit` nas versões fixadas são conhecidos e aceitos pelo autor. **Não
rode `npm audit fix --force` e não suba versão para silenciar alerta** — mudar um pin
é decisão do autor. Se um alerta parecer relevante, relate e pergunte.

## Git

Remote `origin`: `github.com/matheus-wallace/clone-tabnews-ia`. Repositório individual,
sem fluxo de PR — os commits vão direto para `main`. Commite ou faça push apenas quando
pedido.
