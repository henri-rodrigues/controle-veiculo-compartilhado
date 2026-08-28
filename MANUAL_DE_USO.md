# 🚗 Manual de Uso Completo - AutoShare (7 km/L)
> **Controle de Veículo Compartilhado & Divisão de Consumo por Litros**  
> *Link de Acesso ao Sistema:* [https://henri-rodrigues.github.io/controle-veiculo-compartilhado/](https://henri-rodrigues.github.io/controle-veiculo-compartilhado/)

---

## 📌 1. Visão Geral do Sistema

O **AutoShare** é uma plataforma web desenvolvida para gerenciar o uso compartilhado de veículos entre múltiplos integrantes (**Cinthia, Arnaldo, Henri, Hector e Heric**), operando sob uma constante de consumo de **7,0 km/L** (`1 Litro a cada 7 km rodados`).

### Principais Recursos:
- 📅 **Relatório por Intervalo de Datas**: O usuário define livremente a **Data de Início** e a **Data de Emissão/Fim** (sendo a data máxima permitida o dia atual) para apurar os gastos do período exato.
- 📄 **Extrato Completo para PDF/Impressão**: O relatório exportável em PDF inclui resumo executivo, tabela de rateio por pessoa e a relação detalhada de **todas as viagens, rotas, paradas e passageiros**.
- 🛣️ **Histórico com Fluxo de Passageiros**: Visualização das corridas com linha do tempo de paradas e indicador de quem entrou (`🟢 Entrou`), permaneceu (`👤 Permanece`) e desceu (`🔴 Desceu`) em cada trecho.
- 🛣️ **Rotas Pré-definidas (Modelos Salvos)**: Carregamento instantâneo de trajetos frequentes com paradas e ocupantes pré-configurados.
- 👥 **Divisão Justa por Trecho**: Seleção de quem estava no carro em cada trecho da viagem, dividindo tanto o KM quanto os Litros.
- ⛽ **Abastecimento Extra & Créditos em Litros (L)**: Quando um participante abastece com recursos próprios, a quantidade de **Litros** abastecida vira crédito acumulado para abatimento.
- ☁️ **Sincronização em Nuvem (Firebase)**: Dados sincronizados em tempo real entre celulares e computadores com suporte offline.

---

## 🛣️ 2. Módulo 1: Registrar Viagem & Rotas Pré-definidas

Utilizado para registrar cada corrida realizada com o veículo no dia a dia.

### ⚡ Como Registrar uma Viagem:
1. Informe a **Data da Viagem**.
2. Defina a **Origem**, adicione **Paradas Intermediárias** (se houver) e o **Destino Final**.
3. Em cada trecho gerado, marque os integrantes que estavam dentro do carro.
4. O sistema calcula a distância real via OSRM, a conversão para Litros (7 km/L) e o rateio proporcional.
5. Clique em **`Salvar Viagem`**.

### 💾 Modelos de Rotas Pré-definidas:
- Para usar: abra o menu **`⚡ Carregar Rota Modelo...`**.
- Para salvar uma rota nova: monte o trajeto e clique em **`Salvar este Trajeto com Paradas e Ocupantes como Modelo`**.
- Para gerenciar ou excluir modelos: clique no botão com ícone de rota no cabeçalho.

---

## ⛽ 3. Módulo 2: Abastecimento Extra (Crédito em Litros)

Quando um integrante abastece o veículo pagando do próprio bolso, a quantidade de combustível entra como **Crédito em Litros (L)**.

1. Acesse a aba **`Abastecimento Extra (Crédito em L)`**.
2. Selecione quem abasteceu, a data e os **Litros Abastecidos (L)**.
3. Clique em **`Registrar Abastecimento Extra & Adicionar Crédito (L)`**.
4. O saldo de créditos é atualizado e abaterá automaticamente nos relatórios de consumo.

---

## 📊 4. Módulo 3: Relatório de Consumo por Período & PDF

Gera o fechamento e a prestação de contas de qualquer período desejado.

### Como Gerar o Relatório:
1. Acesse a aba **`Relatório por Período`**.
2. Selecione a **Data de Início** e a **Data de Emissão/Fim** (a data máxima disponível é o dia de hoje).
3. O sistema filtra as viagens do período e exibe o consumo total em KM e Litros.
4. Opcionalmente, informe o **Preço do Litro (R$/L)** ou o **Custo Total no Posto (R$)** para conversão financeira automática.
5. Clique em **`Gerar Relatório em PDF / Imprimir`**.
6. Um modal completo será exibido contendo:
   - Resumo geral de métricas.
   - Tabela de rateio e consumo por participante.
   - Extrato detalhado com todas as viagens, paradas e ocupantes daquele período.
7. Clique em **`Imprimir / Salvar em PDF`** para exportar o arquivo oficial.

---

## 📄 5. Módulo 4 & 5: Log de Relatórios & Histórico Visual de Viagens

- **Log de Relatórios**: Consulta histórica de todos os relatórios emitidos anteriormente para reimpressão rápida.
- **Histórico & Fluxo de Paradas**: Cada viagem exibe uma linha do tempo com:
  - Distância e litros de cada perna do trajeto.
  - Ocupantes no carro.
  - Indicador de quem subiu e quem desceu em cada parada.
  - Rateio individual detalhado daquela corrida.
