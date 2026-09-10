---
name: AutoShare
description: Controle de veículo compartilhado e rateio de combustível por litros (7 km/L). App utilitário, dark, mobile-first, pt-BR.
colors:
  primary: "#6366F1"        # índigo suave (emerald-500 remapeado) — cor de ação / marca
  primary-hover: "#5457DA"  # emerald-600
  primary-soft: "#8C8FF2"   # emerald-400 — texto/ícone sobre escuro
  secondary: "#4ADE80"      # leaf-500 — verde folha: litros / consumo / sucesso
  secondary-soft: "#6EE7A0" # leaf-400
  bg: "#121214"             # slate-950 — fundo principal (cinza chumbo)
  surface: "#171719"        # slate-900 — header, inputs, wells
  surface-raised: "#1F1F24" # slate-800 — cards (base do .glass-card ≈ #1A1A1E)
  border: "#1F1F24"         # slate-800 — bordas de input
  border-strong: "#33333A"  # slate-700 — bordas de card
  on-bg: "#E1E1E6"          # slate-100 — corpo (off-white suave)
  on-bg-strong: "#ffffff"   # títulos
  on-bg-muted: "#A8A8B3"    # slate-400 — labels e texto secundário
  error: "#f59e0b"          # amber-500 — status offline/erro
  danger: "#f87171"         # red-400 — ações destrutivas
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

> **Como o tema é aplicado:** o app não usa cores próprias espalhadas — ele **remapeia a escala do Tailwind**
> no `tailwind.config` inline (`slate` → neutros chumbo/grafite, `emerald` → índigo, `leaf` → verde).
> Então `bg-slate-950`, `text-emerald-400` etc. continuam no código, mas rendem os valores abaixo.
> Mexeu em cor? Mexa no `tailwind.config` **e** aqui.

- **Primary `#6366F1` (índigo suave, = `emerald-500`):** única cor de **ação e navegação**. Botões primários, aba ativa, foco de input, links, ícones de seção.
- **Primary-soft `#8C8FF2` (= `emerald-400`):** texto/ícone de destaque sobre fundo escuro (melhor contraste que o 500).
- **Secondary `#4ADE80` (verde folha, = `leaf-500`):** **litros / consumo / sucesso**. Números grandes de litros, traçado da rota no mapa, pino de origem, toast de sucesso. **Não usar para botão nem navegação.**
- **Fundos:** `#121214` (página) → `#171719` (header, inputs) → `#1A1A1E`/`#1F1F24` (cards). Sempre nessa ordem de profundidade.
- **Texto:** `#E1E1E6` corpo, `#ffffff` títulos, `#A8A8B3` labels/secundário. **Não usar slate-500/600 para texto informativo** (contraste no limite).
- **Error/Offline `#f59e0b` (amber-500):** status do Firebase offline, avisos. **Danger `#f87171` (red-400):** ações que apagam dados.
- **Print:** fundo `#ffffff`, texto `#000000`; realces viram tons escuros legíveis (índigo `#3730a3`, verde `#166534`) — imposto pelo `@media print`.

Tema **exclusivamente escuro** (menos vibrante, cinza chumbo). Não há alternância claro/escuro. A única exceção é a impressão do relatório.

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

- **Card:** `.glass-card rounded-3xl p-5 border border-slate-700` (fundo ≈ `rgba(26,26,30,.88)` + blur).
- **Input:** fundo `slate-900`, borda `slate-800`, `rounded-xl`, `px-3 py-3`, `text-white`, `focus:border-emerald-500`, sempre com `<label>` associado.
- **Campo calculado (output):** valor derivado pelo sistema (ex.: distância da rota) usa `readonly tabindex="-1"`, fundo `slate-950` (mais fundo), número em `text-leaf-400`, ícone à esquerda e legenda "calculada automaticamente". O usuário nunca digita.
- **Botão primário:** `bg-emerald-500 hover:bg-emerald-600 text-white font-bold rounded-xl px-4 py-3 transition` (índigo com texto branco).
- **Botão secundário / neutro:** `bg-slate-900 text-slate-300 border border-slate-800 hover:bg-slate-800`.
- **Botão destrutivo:** texto/borda em amber ou red-400; **sempre com `confirm()`** antes de agir.
- **Aba / nav item:** inativo `text-slate-400`; ativo índigo + sombra (classe `.active`).
- **Badge de litros/valor:** `bg-leaf-500/15 text-leaf-300 rounded-full px-2 py-0.5 font-extrabold`.
- **Ícone só-decorativo:** FontAwesome `fa-solid`. **Ícone-como-botão:** precisa de `aria-label`.
- **Toast:** feedback obrigatório após salvar/excluir e após qualquer chamada de rede (OSRM, Photon, Firebase).
- **Modal:** `max-w-3xl max-h-[90vh] overflow-y-auto`, backdrop `bg-slate-950/80 backdrop-blur-sm`, `.no-print`, fecha no `Esc` e no clique fora.

## Do's and Don'ts

- **Do** usar índigo (`emerald-*` remapeado) como a única cor de ação; verde (`leaf-*`) só para litros/consumo/sucesso.
- **Do** manter tudo em pt-BR.
- **Do** dar estado de loading + erro visível para OSRM/Photon/Firebase.
- **Do** adicionar regras `@media print` para qualquer conteúdo que entre no relatório PDF.
- **Do** espelhar as classes da seção vizinha ao editar.
- **Don't** introduzir uma terceira cor de destaque (só índigo + verde), ciano/teal, ou uma segunda fonte.
- **Don't** usar `h-screen`, `text-slate-500` para texto, ou `w-[calc(...)]` para colunas.
- **Don't** criar campo de formulário com `font-size` < 16px.
- **Don't** adicionar biblioteca via npm — tudo é CDN; declare o `<script>`/`<link>` e o motivo.
- **Don't** jogar `backdrop-blur` em elementos novos aleatórios; o `.glass-card` já é o recurso.
- **Don't** adicionar animação em loop infinito; transições ≤ 200ms e respeitar `prefers-reduced-motion`.
