# AutoShare — Controle de Veículo Compartilhado

App web de página única para 5 pessoas (Cinthia, Arnaldo, Henri, Hector, Heric)
controlarem o uso de um carro compartilhado e ratearem o combustível por **litros**
(constante fixa **7,0 km/L** → `litros = km / 7`).

## Arquitetura (resumo)

- **`index.html`** — o app inteiro. HTML + JavaScript vanilla (classe `AutoShareApp`, exposta como `window.app`) + Tailwind via **CDN (v3)** + FontAwesome 6. Sem build, sem npm, sem framework.
- **Persistência dupla:** `localStorage` (`autoshare_car_data_v10`, offline) + **Firebase Firestore** (`onSnapshot` no doc `autoshare/main_data_v10`, tempo real). Firestore não aceita array aninhado → `prepareForFirestore` / `parseFromFirestore` serializam sub-arrays como string JSON.
- **APIs externas sem chave:** OSRM (rotas), Photon/Komoot (geocoding). Ambas têm fallback.
- **Rateio:** proporcional aos litros consumidos no período; créditos de abastecimento extra (`memberCredits`) são abatidos no fechamento; emitir relatório zera o período (`lastClosedTimestamp`).
- Tema **dark**, **mobile-first**, interface **pt-BR**. O relatório vira **PDF via `@media print`**.
- `MANUAL_DE_USO.md` — manual do usuário final. `README.md` — visão geral.
- `.agents/` — toolkit "AG Kit" para Gemini CLI / Antigravity (não usado pelo Claude Code; serve como material de referência aprofundada).

## Convenções

- Branch dedicada para mudanças grandes: `feature/[slug]` ou `fix/[slug]`.
- Handlers no HTML seguem o padrão `onclick="window.app && window.app.metodo()"`.
- Ao editar uma seção, espelhe as classes Tailwind vizinhas em vez de introduzir estilo novo.
- Datas de relatório: fim ≤ hoje; início ≤ fim.

## Trabalho de UI/UX — portão obrigatório

Antes de criar ou alterar **qualquer interface** (layout, cor, tipografia, componente, tela, modal, fluxo):

1. **Leia `DESIGN.md`** na raiz — é a fonte da verdade dos tokens visuais. Construa contra ele. Se a linguagem visual mudar, atualize o `DESIGN.md` junto.
2. **Carregue a skill `ui-ux-design`** (`.claude/skills/ui-ux-design/`) e siga o fluxo dela.
3. Depois de codificar, **audite com a skill `ui-ux-review`**.
4. Para classes Tailwind, use a skill `tailwind-cdn-patterns` (o projeto é CDN/v3 — padrões v4 não se aplicam).

Tweak trivial em UI já existente (uma cor, um respiro de espaçamento) pode seguir direto, desde que dentro dos tokens do `DESIGN.md`.

## Skills locais (`.claude/skills/`)

| Skill | Quando |
|---|---|
| `ui-ux-design` | Antes de qualquer UI — princípios, linguagem visual, regras anti-clichê, portão do DESIGN.md |
| `ui-ux-review` | Depois de qualquer alteração visual — acessibilidade, usabilidade, consistência, responsividade, impressão |
| `tailwind-cdn-patterns` | Ao escrever classes Tailwind ou mexer no `tailwind.config` inline |
