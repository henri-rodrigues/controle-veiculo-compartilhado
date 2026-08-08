# 🚗 Controle de Veículo Compartilhado (AutoShare)

Aplicação web single-page (SPA) responsiva, intuitiva e moderna para gestão de uso, cálculo de distâncias divididas por corrida e apuração financeira transparente entre integrantes fixos (Cíntia, Arnaldo, Henrique e Eric).

🌐 **Acesse a Aplicação Online (GitHub Pages)**:
👉 **[https://henri-rodrigues.github.io/controle-veiculo-compartilhado/](https://henri-rodrigues.github.io/controle-veiculo-compartilhado/)**

---

## ⚡ Funcionalidades

- **📍 Locais Pré-definidos & Distâncias Base**: Cálculo automático de distância entre a "Casa" (0 km) e destinos de trabalho ou locais customizados.
- **🚗 Registro de Corridas**: Seleção múltipla de motoristas/passageiros com cálculo imediato do rateio em KM por pessoa e suporte a percurso de Ida e Volta.
- **⛽ Registro de Abastecimento**: Entrada de odômetro, valor total do posto e contribuição individual com validação visual em tempo real.
- **📊 Relatório & Fechamento de Período**: Apuração proporcional ao uso do carro (% de KM no período) e balanço financeiro transparente (**A RECEBER** / **A PAGAR**).
- **🔥 Firebase Cloud Database & LocalStorage**: Sincronização em tempo real na nuvem via Firebase Firestore com suporte offline completo via LocalStorage.
- **📦 Backup & Restauração**: Exportação e importação de dados em JSON.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5 & Vanilla JavaScript**: Sem frameworks pesados, execução instantânea no navegador.
- **Tailwind CSS (CDN)**: Design moderno com estética automotiva.
- **FontAwesome 6**: Ícones vetoriais.
- **Firebase Firestore**: Armazenamento em nuvem em tempo real (opcional).

---

## 🔥 Como Conectar o Firebase Cloud Database

1. Acesse o [Firebase Console](https://console.firebase.google.com) e crie um projeto gratuito.
2. Adicione um **Web App** para copiar o objeto de configuração (`apiKey`, `projectId`, etc.).
3. Vá em **Firestore Database** -> **Criar banco de dados** e inicie em **Modo de teste**.
4. Na aplicação web, clique no botão **Firebase Cloud** no cabeçalho e cole o JSON com suas chaves!
