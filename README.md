# 🚗 Controle de Veículo Compartilhado (AutoShare - 7 km/L)

Aplicação web single-page (SPA) responsiva, intuitiva e moderna para gestão de uso, cálculo de consumo por **Litros (L)** com constante fixa de **7,0 km/L**, controle de créditos individuais em Litros e apuração financeira transparente entre integrantes (Cinthia, Arnaldo, Henri, Hector e Heric).

🌐 **Acesse a Aplicação Online (GitHub Pages)**:
👉 **[https://henri-rodrigues.github.io/controle-veiculo-compartilhado/](https://henri-rodrigues.github.io/controle-veiculo-compartilhado/)**

---

## ⚡ Funcionalidades

- **🛣️ Rotas Pré-definidas com Paradas & Ocupantes**: Salve e carregue instantaneamente trajetos frequentes com 1 clique. O sistema preenche a origem, paradas, destino final e os integrantes de cada perna do percurso automaticamente!
- **⛽ Consumo Real por Litros (7 km/L)**: Cada quilômetro percorrido é automaticamente convertido para Litros consumidos (`Litros = KM / 7`). O KM percorrido continua visível e registrado.
- **📍 Locais Pré-definidos & Rota Real OSRM**: Cálculo automático de rota com suporte a múltiplas paradas intermediárias e link direto para navegação no Google Maps.
- **👥 Divisão Justa por Trecho**: Seleção de ocupantes em cada perna do trajeto com cálculo proporcional imediato de KM e Litros atribuídos.
- **⛽ Abastecimento Extra & Saldo de Créditos em Litros (L)**: Quando um integrante abastece o carro com recursos próprios, os litros entram como crédito acumulado para abatimento automático no fechamento.
- **📊 Relatório & Fechamento de Período**: Apuração proporcional ao consumo do carro (% de uso e Litros a pagar) com conversão automática para valor em R$ conforme o preço do combustível ou valor total do posto.
- **🖨️ Relatório Oficial Imprimível (A4 / PDF)**: Modal pronto para impressão e salvamento em PDF com tabela completa de auditoria.
- **🔥 Firebase Cloud Database & LocalStorage**: Sincronização em tempo real na nuvem via Firebase Firestore com suporte offline completo via LocalStorage.
- **📦 Backup & Restauração**: Exportação e importação de dados em JSON.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5 & Vanilla JavaScript**: Sem dependências pesadas, carregamento instantâneo.
- **Tailwind CSS (CDN)**: Design moderno escuro e responsivo (Desktop & Mobile).
- **FontAwesome 6**: Ícones vetoriais.
- **OSRM API & OpenStreetMap**: Roteirização e cálculo de distâncias reais.
- **Firebase Firestore**: Armazenamento e sincronização em nuvem em tempo real.

---

## 🔥 Como Conectar o Firebase Cloud Database

1. Acesse o [Firebase Console](https://console.firebase.google.com) e crie um projeto gratuito.
2. Adicione um **Web App** para copiar o objeto de configuração (`apiKey`, `projectId`, etc.).
3. Vá em **Firestore Database** -> **Criar banco de dados** e inicie em **Modo de teste**.
4. Na aplicação web, clique no botão **Firebase Cloud** (ícone de fogo) no cabeçalho e cole o JSON com suas chaves!
