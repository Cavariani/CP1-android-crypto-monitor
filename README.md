CryptoMonitor - Documentação do Projeto
Visão Geral
CryptoMonitor é um aplicativo Android que exibe a cotação atual do Bitcoin (BTC) em reais (R$), utilizando a API pública do Mercado Bitcoin. O app apresenta o último preço e a data da consulta, com opção de atualização manual via botão.
Tecnologias Utilizadas

Kotlin: Linguagem de programação principal.  
Retrofit2: Para chamadas HTTP à API.  
Gson: Conversão de JSON para objetos Kotlin.  
Coroutines: Gerenciamento de operações assíncronas.  
Android View System: Interface com Toolbar, TextView e Button.

Estrutura do Projeto
carreiras.com.github.cryptomonitor
├── model
│   ├── TickerResponse.kt
│   └── Ticker.kt
├── service
│   ├── MercadoBitcoinService.kt
│   └── MercadoBitcoinServiceFactory.kt
└── MainActivity.kt

Funcionalidades

Consulta o preço atual do Bitcoin (BTC) via API.  
Formata o preço em reais (R$).  
Exibe a data da cotação no formato dd/MM/yyyy HH:mm:ss.  
Botão "Refresh" para atualização manual.  
Tratamento de erros de rede e respostas da API.

Análise dos Arquivos
Pacote model
TickerResponse.kt

Representa a resposta da API.  
Contém um objeto Ticker com os dados da cotação.

Ticker.kt

Modelo de dados da cotação.  
Atributos:  
high: Preço máximo.  
low: Preço mínimo.  
vol: Volume negociado.  
last: Último preço.  
buy: Preço de compra.  
sell: Preço de venda.  
date: Timestamp da cotação.



Pacote service
MercadoBitcoinService.kt

Interface do Retrofit.  
Define o endpoint HTTP GET /api/BTC/ticker/ para consultar a cotação do Bitcoin.

MercadoBitcoinServiceFactory.kt

Configura e cria uma instância do MercadoBitcoinService.  
Utiliza Retrofit com Gson para conversão de dados.

MainActivity.kt

Classe principal do app.  
Configura a interface:  
Toolbar personalizada com título e cor.  
TextViews para preço e data.  
Botão "Refresh" para atualizar os dados.


Realiza chamada assíncrona à API usando Coroutines.  
Formata e exibe o preço (last) em R$ e a data (date) no formato local.  
Trata erros HTTP (400, 401, 403, 404) e falhas de conexão com mensagens via Toast.

Integração com a API

URL Base: https://www.mercadobitcoin.net/  
Endpoint: /api/BTC/ticker/  
Método: GET  
Resposta (JSON):  {
  "ticker": {
    "high": "152000.00",
    "low": "148000.00",
    "vol": "120.5",
    "last": "150000.00",
    "buy": "149500.00",
    "sell": "150500.00",
    "date": 1618327340
  }
}



Fluxo de Operação

O app inicia e exibe a tela principal.  
Usuário clica no botão "Refresh".  
Uma chamada assíncrona é feita à API do Mercado Bitcoin.  
Se bem-sucedida:  
Preço é formatado em reais e exibido.  
Data é convertida de timestamp para dd/MM/yyyy HH:mm:ss.


Em caso de erro, uma mensagem é exibida via Toast.

Tratamento de Erros

Erros HTTP:  
400: "Bad Request"  
401: "Unauthorized"  
403: "Forbidden"  
404: "Not Found"  
Outros: "Unknown error"


Falhas de Conexão: Capturadas e exibidas via Toast com detalhes do erro.

Evidências de Execução
Adicione as capturas de tela após executar o projeto:  

Tela Inicial: Antes de clicar em "Refresh".  
<img width="1512" alt="Captura de Tela 2025-04-27 às 12 58 46" src="https://github.com/user-attachments/assets/514fd778-8649-4beb-b0a2-9e923ee0c5e6" />



Tela Atualizada: Após clicar em "Refresh".  
<img width="1504" alt="Captura de Tela 2025-04-27 às 12 59 04" src="https://github.com/user-attachments/assets/91e3c23a-f64a-46d1-a26b-af74cbbfa2c7" />




