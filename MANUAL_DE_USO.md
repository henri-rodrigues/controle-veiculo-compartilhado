# 🚗 Manual de Uso Completo - AutoShare (7 km/L)
> **Controle de Veículo Compartilhado & Divisão de Consumo por Litros**  
> *Link de Acesso ao Sistema:* [https://henri-rodrigues.github.io/controle-veiculo-compartilhado/](https://henri-rodrigues.github.io/controle-veiculo-compartilhado/)

---

## 📌 1. Visão Geral do Sistema

O **AutoShare** é uma plataforma web desenvolvida para gerenciar o uso compartilhado de veículos entre múltiplos integrantes (**Cinthia, Arnaldo, Henri, Hector e Heric**), operando sob uma constante de consumo de **7,0 km/L** (`1 Litro a cada 7 km rodados`).

### Principais Recursos:
- 🛣️ **Rotas Pré-definidas (Modelos com Paradas e Ocupantes)**: Carregamento instantâneo com 1 clique de trajetos com pontos intermediários e passageiros pré-selecionados.
- 🛣️ **Cálculo de Distância (KM) & Consumo (Litros)**: Rotas reais com OSRM/OpenStreetMap. O KM é registrado e convertido automaticamente em Litros (`Litros = KM / 7`).
- 👥 **Divisão Justa por Trecho**: Seleção de quem estava no carro em cada trecho da viagem, dividindo tanto o KM quanto os Litros.
- ⛽ **Abastecimento Extra & Créditos em Litros (L)**: Quando um participante abastece com recursos próprios, a quantidade de **Litros** abastecida vira crédito acumulado.
- 📊 **Fechamento de Período & Rateio por Litro**: Divisão proporcional ao consumo em Litros de cada um, com abatimento automático dos créditos em Litros e cálculo opcional do valor financeiro a pagar em R$.
- ☁️ **Sincronização em Nuvem (Firebase)**: Dados sincronizados em tempo real entre celulares e computadores com suporte offline.

---

## 🛣️ 2. Módulo 1: Registrar Viagem & Rotas Pré-definidas

Utilizado para registrar cada corrida realizada com o veículo no dia a dia.

### ⚡ Como Usar uma Rota Pré-definida:
1. No topo do formulário de registro de viagem, abra o menu **`⚡ Carregar Rota Modelo...`**.
2. Selecione a rota desejada (ex: *Casa ➔ Trab. Cinthia ➔ Facul. Henri/Hector*).
3. O sistema preenche instantaneamente:
   - Origem
   - Todas as paradas intermediárias
   - Destino final
   - Ocupantes marcados em cada perna do trajeto
   - Distância e consumo total em Litros
4. Basta conferir e clicar em **`Salvar Viagem`**!

### 💾 Como Salvar uma Nova Rota Pré-definida:
1. Monte o trajeto com a Origem, Paradas e Destino desejados.
2. Marque os ocupantes de cada trecho.
3. Clique no botão âmbar **`Salvar este Trajeto com Paradas e Ocupantes como Modelo`**.
4. Dê um nome para a rota e clique em OK. Pronto! Ela estará disponível para uso imediato em todos os dispositivos.

---

## ⛽ 3. Módulo 2: Abastecimento Extra (Crédito em Litros)

Quando um integrante abastece o veículo pagando do próprio bolso, a quantidade de combustível entra como **Crédito em Litros (L)**.

### Como Registrar:
1. Acesse a aba **`Abastecimento Extra (Crédito em L)`**.
2. Selecione **Quem Abasteceu** (ex: *Cinthia*).
3. Informe a **Data** e a quantidade de **Litros Abastecidos (L)** (ex: *20,0 L*).
4. Clique em **`Registrar Abastecimento Extra & Adicionar Crédito (L)`**.

### Saldo Atual de Créditos:
- O painel exibe o saldo de crédito acumulado em Litros de cada participante.
- **Abatimento Automático**: No fechamento, os Litros consumidos pelo participante abatem prioritariamente do seu saldo de créditos em Litros!

---

## 📊 4. Módulo 3: Relatório & Fechamento de Período

Ao final de um período, realiza-se o fechamento dos consumos do veículo.

### Como Funciona o Fechamento:
1. Acesse a aba **`Relatório & Fechamento`**.
2. O sistema exibe o **KM Total** e os **Litros Totais Consumidos** no período (`Total KM / 7`).
3. Opcionalmente, preencha:
   - **Preço do Litro (R$/L)** (ex: *R$ 5,89*); OU
   - **Custo Total no Posto (R$)** (ex: *R$ 250,00*).
4. O sistema calcula para cada participante:
   - **KM Rodado** e **Litros Consumidos (L)**.
   - **Porcentagem de Uso (%)**.
   - **Crédito em Litros Abatido (L)**.
   - **Litros a Pagar (L)** (Saldo devedor em combustível).
   - **Valor Final a Pagar (R$)** (se informado preço do combustível).
5. Clique em **`Emitir & Abater Créditos (L)`**. O relatório é salvo no log e um modal de impressão é exibido.

---

## 📄 5. Módulo 4: Log de Relatórios & Histórico

- **Histórico de Viagens**: Tabela completa com data, ocupantes, trajeto, KM total e Litros equivalentes.
- **Log de Relatórios Salvos**: Registro histórico de todos os fechamentos anteriores com opção de visualização e reimpressão.

---

## 💡 6. Exemplo Prático de Divisão (Constante 7 km/L)

Suponha uma viagem de **14,0 km** (equivalente a **2,0 Litros** de combustível):

- **Trecho 1 (7,0 km = 1,0 L)**: Ocupantes **Cinthia** e **Henri**
  - *Atribuição*: 3,5 km (0,5 L) para Cinthia e 3,5 km (0,5 L) para Henri.

- **Trecho 2 (7,0 km = 1,0 L)**: Apenas **Henri** no carro
  - *Atribuição*: 7,0 km (1,0 L) para Henri.

- **Resultado da Viagem**:
  - **Cinthia**: 3,5 km (0,50 L)
  - **Henri**: 10,5 km (1,50 L)

Se Cinthia possuir **2,0 L de crédito prévio**, no fechamento seus **0,5 L** consumidos serão abatidos, resultando em **0,0 L a pagar** e um saldo restante de **1,5 L de crédito**!
