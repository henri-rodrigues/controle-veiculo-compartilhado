---
name: AutoShare
description: Controle de veículo compartilhado e rateio de combustível por litros (7 km/L). App utilitário, dark, mobile-first, pt-BR.
colors:
  primary: "#10b981"        # emerald-500 — cor de ação / marca
  primary-hover: "#059669"  # emerald-600
  primary-soft: "#34d399"   # emerald-400 — texto/ícone sobre escuro
  accent: "#2dd4bf"         # teal-400 — só no gradiente do logo
  bg: "#020617"             # slate-950 — fundo da página
  surface: "#0f172a"        # slate-900 — header, inputs, tracks
  surface-raised: "#1e293b" # slate-800 — cards (base do .glass-card)
  border: "#1e293b"         # slate-800 — bordas de input
  border-strong: "#334155"  # slate-700 — bordas de card
  on-bg: "#f1f5f9"          # slate-100 — corpo
  on-bg-strong: "#ffffff"   # títulos
  on-bg-muted: "#94a3b8"    # slate-400 — labels e texto secundário
  error: "#f59e0b"          # amber-500 — usado para status offline/erro
  print-bg: "#ffffff"
  print-fg: "#000000"
typography:
  font-sans: { fontFamily: "Plus Jakarta Sans", fontWeight: 400, lineHeight: 1.5 }
  headline-lg: { fontFamily: "Plus Jakarta Sans", fontSize: 18px, fontWeight: 800, lineHeight: 1.2 }
  headline-md: { fontFamily: "Plus Jakarta Sans", fontSize: 16px, fontWeight: 700, lineHeight: 1.3 }
  body-md: { fontFamily: "Plus Jakarta Sans", fontSize: 12px, fontWeight: 400, lineHeight: 1.5 }
  label: { fontFamily: "Plus Jakarta Sans", fontSize: 10px, fontWeight: 600, lineHeight: 1.4, letterSpacing: 0.04em }
  input: { fontFamily: "Plus Jakarta Sans", fontSize: 16px, fontWeight: 400 }  # 16px obrigatório (iOS zoom)
rounded:
  sm: 8px      # rounded-lg
  md: 12px     # rounded-xl — botões, inputs, badges quadrados
  lg: 16px     # rounded-2xl — cards internos
  xl: 24px     # rounded-3xl — cards principais, modais
  full: 9999px # pills, avatares
spacing:
  xs: 4px
  sm: 8px
  md: 12px
  lg: 16px
  xl: 20px
  "2xl": 28px
components:
  card:
    backgroundColor: "rgba(30,41,59,0.85)"   # + backdrop-blur(16px)
    borderColor: "rgba(255,255,255,0.08)"
    rounded: "{rounded.xl}"
    padding: 20px
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "#020617"
    rounded: "{rounded.md}"
    padding: 12px
  button-primary-hover:
    backgroundColor: "{colors.primary-hover}"
  button-secondary:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-bg-muted}"
    borderColor: "{colors.border}"
    rounded: "{rounded.md}"
  input:
    backgroundColor: "{colors.surface}"
    borderColor: "{colors.border}"
    textColor: "{colors.on-bg-strong}"
    rounded: "{rounded.md}"
    typography: "{typography.input}"
  tab-active:
    backgroundColor: "{colors.primary}"
    textColor: "#ffffff"
  badge:
    backgroundColor: "rgba(16,185,129,0.20)"
    textColor: "#6ee7b7"
    rounded: "{rounded.full}"
---

# AutoShare — Linguagem Visual

## Overview

Ferramenta interna para 5 pessoas (Cinthia, Arnaldo, Henri, Hector, Heric) controlarem o uso de
um carro compartilhado e ratearem o combustível. A personalidade é **utilitária, confiável e
direta** — não é marketing, é uma planilha viva. O usuário abre no celular, registra uma viagem
em segundos e, no fim do mês, gera um PDF de prestação de contas. Clareza numérica e confiança
importam mais do que sofisticação estética.

## Colors

- **Primary `#10b981` (emerald-500):** única cor de ação. Botões primários, aba ativa, saldos positivos, foco de input.
- **Primary-soft `#34d399` (emerald-400):** texto e ícones de destaque sobre fundo escuro (melhor contraste que o 500 para texto).
- **Accent `#2dd4bf` (teal-400):** aparece só no gradiente do ícone do logo (`from-emerald-600 to-teal-400`). Não usar em mais nada.
- **Fundos:** `#020617` (página) → `#0f172a` (header, inputs) → `#1e293b` (cards). Sempre nessa ordem de profundidade.
- **Texto:** `#f1f5f9` corpo, `#ffffff` títulos, `#94a3b8` labels/secundário. **Não usar slate-500/600 para texto informativo** (falha AA).
- **Error/Offline `#f59e0b` (amber-500):** status do Firebase quando cai para offline, mensagens de erro.
- **Print:** fundo `#ffffff`, texto `#000000` — imposto pelo `@media print` para o PDF do relatório.

Tema **exclusivamente escuro**. Não há alternância claro/escuro. A única exceção é a impressão.

## Typography

Família única: **Plus Jakarta Sans** (Google Fonts, pesos 400–800). Sem serifa, sem segunda família.

- Títulos de seção: 16–18px, peso 700–800.
- Corpo e listas: 12px (`text-xs`) — o app é denso por natureza.
- Labels: 10–11px, uppercase, `font-semibold`, `text-slate-400`.
- **Inputs: 16px obrigatório** (`input,select,textarea,button { font-size:16px !important }` no `<style>`) para impedir o zoom automático do iOS ao focar um campo. Nunca criar campo com fonte menor.

## Layout

- **Mobile-first.** Classe base = mobile; `sm:` (640) e `md:` (768) para telas maiores.
- Contêiner central: `max-w-7xl mx-auto`.
- Navegação dupla: abas no topo (desktop) + **bottom-nav fixa** (mobile). Body tem `pb-24 md:pb-12` para não ser coberto pela bottom-nav.
- Grid sobre flex-math: `grid grid-cols-1 md:grid-cols-3 gap-4`.
- Altura: `min-h-[100dvh]`, nunca `h-screen`.
- Escala de espaçamento em múltiplos de 4px.

## Elevation & Depth

Design quase plano. Profundidade vem de:
- **Camadas tonais:** slate-950 → 900 → 800.
- **`.glass-card`:** `backdrop-filter: blur(16px)` + fundo semi-transparente + borda `white/8`.
- **Sombra colorida** só no que é primário: `shadow-lg shadow-emerald-500/20` / `/35`.
Não empilhar múltiplos níveis de sombra. Não usar sombra preta pesada.

## Shapes

- Interativos (botões, inputs, badges quadrados, ícones em círculo): `rounded-xl` (12px).
- Contêineres internos: `rounded-2xl` (16px).
- Cards principais e modais: `rounded-3xl` (24px).
- Pills, avatares, tags de pessoa: `rounded-full`.
- Não misturar cantos retos e arredondados na mesma tela.

## Components

- **Card:** `.glass-card rounded-3xl p-5 border border-slate-700`.
- **Input:** fundo `slate-900`, borda `slate-800`, `rounded-xl`, `px-3 py-3`, texto branco, `focus:border-emerald-500`, sempre com `<label>` associado.
- **Botão primário:** `bg-emerald-500 hover:bg-emerald-600 text-slate-950 font-bold rounded-xl px-4 py-3 transition`.
- **Botão secundário / neutro:** `bg-slate-900 text-slate-300 border border-slate-800 hover:bg-slate-800`.
- **Botão destrutivo:** texto/borda em amber ou red-400; **sempre com `confirm()`** antes de agir (excluir viagem, excluir rota, estornar crédito, zerar banco).
- **Aba / nav item:** inativo `text-slate-400`; ativo `emerald-500` + sombra (classe `.active`).
- **Badge de litros/valor:** `bg-emerald-500/20 text-emerald-300 rounded-full px-2 py-0.5 font-extrabold`.
- **Ícone só-decorativo:** FontAwesome `fa-solid`. **Ícone-como-botão:** precisa de `aria-label`.
- **Toast:** feedback obrigatório após salvar/excluir e após qualquer chamada de rede (OSRM, Photon, Firebase).
- **Modal:** `max-w-3xl max-h-[90vh] overflow-y-auto`, backdrop `bg-slate-950/80 backdrop-blur-sm`, `.no-print`, fecha no `Esc` e no clique fora.

## Do's and Don'ts

- **Do** usar emerald como a única cor de ação; um destaque por tela.
- **Do** manter tudo em pt-BR.
- **Do** dar estado de loading + erro visível para OSRM/Photon/Firebase.
- **Do** adicionar regras `@media print` para qualquer conteúdo que entre no relatório PDF.
- **Do** espelhar as classes da seção vizinha ao editar.
- **Don't** introduzir roxo/violeta, azul ou uma segunda fonte.
- **Don't** usar `h-screen`, `text-slate-500` para texto, ou `w-[calc(...)]` para colunas.
- **Don't** criar campo de formulário com `font-size` < 16px.
- **Don't** adicionar biblioteca via npm — tudo é CDN; declare o `<script>`/`<link>` e o motivo.
- **Don't** jogar `backdrop-blur` em elementos novos aleatórios; o `.glass-card` já é o recurso.
- **Don't** adicionar animação em loop infinito; transições ≤ 200ms e respeitar `prefers-reduced-motion`.
