---
name: ui-ux-review
description: >-
  Auditoria de UI/UX do AutoShare (index.html) — acessibilidade, usabilidade,
  consistência visual, responsividade mobile, estados de carregamento/erro e
  regras de impressão. Use quando o pedido for "revisar a interface",
  "auditar o design", "checar acessibilidade", "revisar UX" ou depois de
  qualquer alteração visual no index.html.
---

# UI/UX Review — AutoShare

Auditar UI **depois** de construída. Reportar no formato terso `arquivo:linha — problema → correção`.

## Como rodar

1. Se houver acesso à internet, buscar as diretrizes atuais e aplicar também:
   `https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md` (via WebFetch)
2. Ler `index.html` (e `DESIGN.md` para conferir aderência aos tokens).
3. Percorrer os checklists abaixo.
4. Listar achados ordenados por severidade (bloqueia uso > acessibilidade > consistência > polimento).

## Checklist — Acessibilidade

- [ ] Contraste AA (4.5:1 texto, 3:1 UI). Suspeitos: `text-slate-500`/`text-slate-600` para texto informativo sobre fundo escuro.
- [ ] Todo controle só-ícone tem `aria-label` (botões FontAwesome no header, lixeiras, editar).
- [ ] Alvo de toque ≥ 44×44px (botões pequenos de "excluir rota", pills de filtro).
- [ ] `:focus-visible` perceptível em todos os interativos (o reset do Tailwind remove outline).
- [ ] Modais (`#modal-*`): fecham no `Esc`, clique no backdrop fecha, foco é movido para dentro ao abrir e devolvido ao fechar, `role="dialog"` + `aria-modal="true"`.
- [ ] Inputs com `<label>` associado (`for`/`id`) — não só placeholder.
- [ ] `<html lang="pt-BR">` mantido; textos novos em pt-BR.
- [ ] Ordem de tabulação segue a ordem visual.

## Checklist — Usabilidade / Estados

- [ ] Ações de rede (cálculo OSRM, geocoding Photon, sync Firebase) têm: estado de carregando, sucesso e **erro visível** (toast), não só `console.error`.
- [ ] Botões de ação irreversível (excluir viagem, excluir rota, zerar banco, emitir relatório que zera período) pedem confirmação clara.
- [ ] Formulário de viagem: validação antes de salvar (origem/destino, ao menos 1 ocupante por trecho) com mensagem no campo.
- [ ] Estados vazios (nenhuma viagem no período, sem créditos, sem rotas-modelo) têm texto orientando o próximo passo.
- [ ] Feedback após salvar/excluir (toast) e a lista re-renderiza.
- [ ] Datas: `report-end-date` limitado a hoje; início ≤ fim.

## Checklist — Consistência visual

- [ ] Cores só saem do `DESIGN.md` (emerald para ação, slate para superfícies). Nada de roxo/azul aleatório.
- [ ] Raios coerentes: `rounded-xl` interativos, `rounded-2xl/3xl` contêineres. Não misturar cantos retos e arredondados na mesma tela.
- [ ] Espaçamento na escala de 4px (`gap-2/3/4`, `p-3/4/5`). Sem valores mágicos `p-[13px]`.
- [ ] Labels uppercase `text-[10px]/[11px] font-semibold text-slate-400` reutilizados, não reinventados.
- [ ] Ícone + texto: `flex items-center gap-2`.

## Checklist — Responsividade

- [ ] Sem scroll horizontal em 360px de largura (`overflow-x-hidden` no body ajuda, mas tabelas do relatório podem estourar — envolver em `overflow-x-auto`).
- [ ] `min-h-[100dvh]` em vez de `h-screen`.
- [ ] Bottom-nav não cobre conteúdo (`pb-24 md:pb-12` no body).
- [ ] Grids colapsam para 1 coluna no mobile.
- [ ] Modais: `max-h-[90vh] overflow-y-auto` para não vazar da tela.

## Checklist — Impressão (PDF do relatório)

- [ ] Elementos de tela que não devem sair no PDF têm `.no-print`.
- [ ] Conteúdo novo do relatório aparece legível no `@media print` (fundo branco / texto preto — testar com preview de impressão).
- [ ] Tabela de rateio e extrato de viagens não quebram feio entre páginas.

## Aprofundamento

- Diretrizes Vercel completas: WebFetch da URL acima.
- Skill de referência original: `.agents/skills/web-design-guidelines/SKILL.md`
- Princípios de design (para justificar correções): skill `ui-ux-design`
