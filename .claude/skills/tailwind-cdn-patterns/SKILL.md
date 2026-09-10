---
name: tailwind-cdn-patterns
description: >-
  Padrões de Tailwind CSS para o AutoShare, que usa o Tailwind via CDN
  (play CDN, equivalente v3) configurado inline no index.html. Use ao
  escrever classes utilitárias, ajustar o tema, ou quando tentado a copiar
  padrões de Tailwind v4 (@theme, oklch, CSS-first) que NÃO funcionam aqui.
---

# Tailwind (CDN) — AutoShare

> ⚠️ Este projeto usa `<script src="https://cdn.tailwindcss.com"></script>` — o **play CDN**,
> que é Tailwind **v3**. Padrões de **v4** (`@theme`, `@tailwindcss/postcss`, cores em `oklch`,
> config CSS-first) **não se aplicam**. A skill `.agents/skills/tailwind-patterns` é v4 — use só como leitura conceitual.

## 1. Onde fica a config

Inline no `<head>` do `index.html`:

```js
tailwind.config = {
  theme: { extend: {
    fontFamily: { sans: ['"Plus Jakarta Sans"', 'sans-serif'] },
    colors: { brand: { 50:'#ecfdf5', 100:'#d1fae5', 400:'#34d399', 500:'#10b981',
                       600:'#059669', 700:'#047857', dark:'#0f172a', card:'#1e293b' } }
  } }
}
```

Para adicionar um token: edite esse objeto **e** o `DESIGN.md`. Não crie um segundo lugar de configuração.
Observação: o código hoje usa muito as classes nativas `emerald-*` / `slate-*` em vez de `brand-*`. Mantenha o que já predomina no arquivo que você está editando.

## 2. Limitações do play CDN (importante)

- **Sem purge/tree-shake** — o CDN gera as classes on-the-fly no browser. Não há custo de bundle, mas há um flash inicial. Não é problema para esta escala.
- **Sem plugins** (`@tailwindcss/forms`, `typography`) a menos que carregados via `?plugins=` na URL do script. Hoje: nenhum.
- **`@apply` e `@layer`** só funcionam dentro de `<style type="text/tailwindcss">`. O `<style>` atual é CSS puro — classes como `.glass-card` são CSS normal, não `@apply`. Mantenha assim.
- Classes arbitrárias `[...]` funcionam: `text-[11px]`, `min-h-[100dvh]`, `shadow-emerald-500/35`.

## 3. Padrões recorrentes no arquivo (reutilize)

| Uso | Classe |
|---|---|
| Card | `glass-card rounded-3xl p-5 border border-slate-700` |
| Input | `w-full bg-slate-900 border border-slate-800 rounded-xl px-3 py-3 text-xs text-white focus:outline-none focus:border-emerald-500` |
| Botão primário | `bg-emerald-500 hover:bg-emerald-600 text-slate-950 font-bold rounded-xl px-4 py-3 transition` |
| Botão secundário | `bg-slate-900 text-slate-300 hover:bg-slate-800 border border-slate-800 rounded-xl` |
| Label | `text-[10px] text-slate-400 uppercase font-semibold` |
| Badge/pill | `text-[10px] bg-emerald-500/20 text-emerald-300 px-2 py-0.5 rounded-full font-extrabold` |
| Aba ativa | `.nav-tab.active` (CSS no `<style>`) → `emerald-500` + sombra |
| Ícone em círculo | `w-7 h-7 rounded-xl bg-emerald-500/10 text-emerald-400 flex items-center justify-center border border-emerald-500/20` |

## 4. Regras

- **Mobile-first:** classe base = mobile, prefixe `sm:`/`md:` para telas maiores.
- **Não usar `space-x`/`space-y` em grid** — use `gap-*`.
- **Dark é o único tema.** Não adicione variante `dark:` (o app não alterna; é sempre escuro, exceto `@media print`).
- **Cores com opacidade:** `bg-emerald-500/10`, `border-white/8` — padrão do projeto para camadas sutis.
- Ao mexer numa seção, **espelhe as classes vizinhas** em vez de trazer um estilo novo.

## Referência conceitual (v4, não aplicável direto)

`.agents/skills/tailwind-patterns/SKILL.md`
