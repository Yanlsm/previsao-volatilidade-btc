# 📈 Previsão de Volatilidade do Bitcoin: TFT vs LSTM vs GARCH

[cite_start]Este repositório contém o código-fonte, os pipelines de pré-processamento e a pesquisa documentada do artigo **"Previsão de Volatilidade do Bitcoin: Um Estudo Comparativo entre Temporal Fusion Transformers, LSTM e GARCH"**[cite: 239]. 

[cite_start]O objetivo central deste projeto é investigar e avaliar arquiteturas de redes neurais do estado-da-arte na previsão de risco financeiro, especificamente a volatilidade diária do Bitcoin com um horizonte de 24 horas à frente[cite: 243, 257].

## 🧠 Visão Geral dos Modelos Investigados

O estudo contrasta três abordagens distintas para lidar com séries temporais financeiras:
* [cite_start]**Temporal Fusion Transformer (TFT):** Arquitetura moderna baseada em atenção, destacando-se pelo uso da *Variable Selection Network* (VSN) para ponderar dinamicamente a relevância de variáveis exógenas heterogêneas[cite: 277, 278, 338].
* [cite_start]**Long Short-Term Memory (LSTM):** Rede neural recorrente profunda (RNN) clássica, capaz de mitigar o desaparecimento do gradiente e capturar dependências não lineares e de longo prazo[cite: 321, 322, 323].
* [cite_start]**GARCH(1,1):** *Baseline* econométrico univariado consolidado, focado em modelar o agrupamento de volatilidade (*volatility clustering*)[cite: 307, 308].

## 📊 Dataset e Pré-processamento

[cite_start]Para refletir a dinâmica atual, o estudo utiliza uma abordagem multivariada com dados de fechamento de granularidade horária abrangendo um histórico de 730 dias, de 2024 a 2026[cite: 245, 258].

* [cite_start]**Ativo Alvo:** Bitcoin (BTC-USD)[cite: 259].
* [cite_start]**Variáveis Exógenas (Contexto de Mercado):** ETH-USD, SOL-USD, e ações do setor de tecnologia tradicionais (NVDA, AAPL, MSFT, GOOGL, QQQ)[cite: 259].
* [cite_start]**Aquisição Reprodutível:** Dados extraídos de forma programática utilizando a API do Yahoo Finance via biblioteca `yfinance` em Python[cite: 289, 290].
* [cite_start]**Alinhamento Temporal:** Aplicação de redimensionamento forçando a marcação de hora cheia e preenchimento de lacunas com o método *forward fill* para sincronizar o mercado de criptomoedas com as restrições de horário do mercado de ações[cite: 295].
* [cite_start]**Engenharia de Atributos:** Transformação de preços originais em retornos logarítmicos, e cálculo de indicadores técnicos como Volatilidade Móvel (24h) e RSI de 14 períodos[cite: 296, 297, 298].
* [cite_start]**Sequenciamento Temporal:** Divisão estrita de 80% para treino e 20% para teste cronológico, com as redes neurais utilizando uma janela de observação (*lookback window*) de 168 horas (uma semana)[cite: 302, 356].

## 🏆 Principais Resultados

[cite_start]Os testes empíricos demonstraram que a transição de modelos estatísticos univariados para arquiteturas profundas multivariadas traz ganhos significativos[cite: 458]:

* [cite_start]**TFT (Estado-da-Arte):** Registrou o menor erro global com um **RMSE de 0.0100**[cite: 421]. [cite_start]Conseguiu minimizar os erros preditivos ao filtrar o ruído das ações de tecnologia e ponderar a influência de choques passados[cite: 422, 423].
* [cite_start]**LSTM:** Alcançou um **RMSE de 0.0108**, validando a capacidade de aprendizado não linear, mas sofreu com atraso na atualização de pesos durante picos extremos[cite: 419, 420].
* [cite_start]**GARCH(1,1):** Obteve o maior erro com um **RMSE de 0.0263**, demonstrando dificuldade em reagir a quebras estruturais e em incorporar sinais multivariados complexos[cite: 319, 417, 418].

## 🚀 Trabalhos Futuros

[cite_start]Como próximos passos indicados na pesquisa, sugere-se a expansão do *dataset* com processamento de linguagem natural (análise de sentimento) sobre notícias e redes sociais, além da exploração de *Quantile Loss* para o modelo TFT, visando a geração de intervalos de confiança[cite: 468, 469].

## 👥 Autores

[cite_start]Trabalho desenvolvido no curso de Bacharelado em Ciência da Computação - Universidade Federal de Uberlândia (UFU)[cite: 242]:
* [cite_start]João Pedro Costa Baroni [cite: 240]
* [cite_start]Leonardo Henrique Carvalho Oliveira [cite: 240]
* [cite_start]Matheus Henrique Barbosa Ribeiro [cite: 240, 241]
* [cite_start]Rodrigo Otávio Fernandes Rodrigues [cite: 240]
* [cite_start]Yan Lucas Santos Marra [cite: 240, 241]

---
*Para mais detalhes matemáticos e estruturais sobre a pesquisa, consulte o artigo completo (`sbc_template.pdf`) disponibilizado neste repositório.*
