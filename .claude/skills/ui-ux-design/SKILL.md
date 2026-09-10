---
name: ui-ux-design
description: >-
  Princípios de design de interface para o AutoShare (Controle de Veículo
  Compartilhado). Use ANTES de criar ou alterar qualquer UI no index.html —
  layout, cor, tipografia, componentes, telas, modais, fluxos. Traz a
  linguagem visual do projeto, regras anti-clichê e o portão do DESIGN.md.
  Não use para lógica de negócio ou cálculo de rateio.
---

# UI/UX Design — AutoShare

> App real: **um único `index.html`** (~3.300 linhas), JavaScript vanilla, **Tailwind via CDN (v3)**,
> FontAwesome 6, tema **dark**, **mobile-first**, interface em **pt-BR**, 5 usuários fixos
> (Cinthia, Arnaldo, Henri, Hector, Heric). Sem build, sem npm, sem React.

## 0. Portão obrigatório: leia o `DESIGN.md`

Antes de escrever/editar UI:

1. Leia `DESIGN.md` na raiz do projeto. Ele é a fonte da verdade dos tokens (cores, tipografia, raio, componentes).
2. Construa **contra os tokens** de lá. Nomes descritivos na conversa mapeiam para nomes de token.
3. Se a linguagem visual mudar, **atualize o `DESIGN.md` junto** — nunca deixe desatualizado.
4. Tweak trivial em UI existente (uma cor de botão, um respiro de espaçamento) pode seguir direto. UI nova sempre passa pelo portão.

Formato do `DESIGN.md`: ver `.agents/skills/design-spec/SKILL.md`.

## 1. Ler o pedido antes de mexer nos botões

Antes de qualquer código, diga em uma linha o **"Design Read"**: que tela é, para quem, com que intenção.
Exemplo: *"Lendo como: modal de fechamento financeiro para 5 amigos não-técnicos, linguagem utilitária e confiável, densidade média, tudo em pt-BR."*

Se o pedido for genuinamente ambíguo, faça **uma** pergunta. Se dá pra inferir, não pergunte.

## 2. Três dials (calibração)

- `DESIGN_VARIANCE: 4` — 1 simetria perfeita … 10 caos artístico. App utilitário → baixo.
- `MOTION_INTENSITY: 3` — transições curtas (`transition`, 150–200ms), nada cinemático. Respeitar `prefers-reduced-motion`.
- `VISUAL_DENSITY: 5` — é um app de dados (viagens, litros, R$). Compacto, mas com hierarquia clara.

Só mude os dials se o pedido pedir explicitamente.

## 3. Linguagem visual do projeto (não reinventar)

| Elemento | Padrão atual |
|---|---|
| Fundo | `bg-slate-950` (página), `bg-slate-900` (header/inputs) |
| Card | `.glass-card` → `rgba(30,41,59,.85)` + `backdrop-blur(16px)` + borda `white/8` |
| Cor de ação / marca | Emerald: `emerald-500` (`#10b981`) primário, `emerald-400` texto/ícone, `emerald-600→teal-400` no gradiente do logo |
| Texto | `text-slate-100` corpo, `text-white` títulos, `text-slate-400` secundário, `text-[10px]/[11px]` labels uppercase |
| Raio | `rounded-xl` (botões/inputs), `rounded-2xl`/`rounded-3xl` (cards/modais) |
| Fonte | Plus Jakarta Sans (Google Fonts), pesos 400–800 |
| Ícones | FontAwesome 6 (`fa-solid`). Emoji é aceito aqui (o app já usa 🚗⛽📅) — é o "vibe" escolhido, mantenha com moderação |
| Nav | Abas no topo (desktop) + bottom-nav fixa (mobile). Estado ativo = `emerald-500` |

**Anti-clichê:** não introduza roxo/violeta, não troque a fonte, não jogue glassmorphism em tudo (o `.glass-card` já é o recurso), não adicione animação em loop infinito.

## 4. Regras rígidas desta base

- **iOS zoom:** todo `input/select/textarea/button` precisa de `font-size: 16px` (já forçado no `<style>`). Não crie campo com fonte menor.
- **Impressão:** o app gera PDF via `@media print`. Qualquer tela nova que entre no relatório precisa de regras de print (fundo branco, texto preto, `.no-print` no que não deve sair).
- **Mobile-first:** classes base = mobile; use `sm:` / `md:` para telas maiores. `pb-24 md:pb-12` no body existe por causa da bottom-nav — não remova.
- **Grid, não cálculo de flex:** `grid grid-cols-1 md:grid-cols-3 gap-4`, nunca `w-[calc(33%-1rem)]`.
- **Altura de viewport:** `min-h-[100dvh]`, nunca `h-screen`.
- **Sem dependência nova sem avisar:** tudo é CDN. Antes de adicionar uma lib, diga qual `<script>`/`<link>` e por quê.
- **Consistência de handlers:** botões usam `onclick="window.app && window.app.metodo()"`. Siga o padrão.

## 5. Acessibilidade (mínimo)

- Contraste WCAG AA: 4.5:1 texto normal. `text-slate-400` sobre `slate-950` passa; `text-slate-500` não — evite para texto informativo.
- Todo controle interativo: alvo de toque ≥ 44px, `:focus` visível, `aria-label` quando o rótulo é só ícone.
- Modais: fechar no `Esc` e no clique fora; devolver foco ao abrir/fechar.
- Estados: todo botão que dispara rede (OSRM, Firebase) precisa de estado de loading e de erro (toast).

## 6. Fluxo de trabalho

```
1. DESIGN READ  → uma linha declarando o que é
2. DESIGN.md    → ler / criar / sincronizar tokens
3. CODIFICAR    → contra os tokens, seguindo a seção 3 e 4
4. AUDITAR      → skill `ui-ux-review`
5. CORRIGIR     → aplicar achados
```

## Aprofundamento (ler sob demanda)

- Princípios gerais de design web: `.agents/skills/frontend-design/SKILL.md`
- Padrões Tailwind: skill `tailwind-cdn-patterns` (adaptada) ou `.agents/skills/tailwind-patterns/SKILL.md` (v4, referência)
- Pensamento mobile / toque: `.agents/skills/mobile-design/SKILL.md`
- Auditoria de UI: skill `ui-ux-review`
- Agente especialista completo: `.agents/agent/frontend-specialist.md`
