# webhook
# Entendendo e Implementando Webhooks com Python

Este repositório é o meu caderno de estudos e projeto prático para entender como funcionam os **Webhooks**.

## 1. O que é um Webhook?

Um Webhook é uma forma de fazer com que um sistema envie informações para outro sistema em **tempo real**, assim que um evento acontece. 

**Analogia simples:**
Imagine que você comprou algo na internet.
* **Sem Webhook:** Você precisa entrar no site da transportadora a cada 5 minutos e perguntar "Meu pacote já chegou?".
* **Com Webhook:** Você cadastra o seu número de celular e a transportadora te manda um SMS (notificação) automaticamente assim que o pacote chega. Você não precisa ficar perguntando.

## 2. Webhook vs. Polling (API Tradicional)

A principal diferença está em **quem toma a iniciativa** da comunicação:

* **Polling (Pull):** É o método tradicional. Nosso servidor faz requisições repetidas para a API de terceiros perguntando se há dados novos. Gasta muitos recursos e gera tráfego desnecessário.
* **Webhook (Push):** A API de terceiros faz uma requisição HTTP (geralmente um `POST`) para o nosso servidor avisando que algo aconteceu e já enviando os dados (o *payload*).



## 3. Ferramentas e Tecnologias

Neste projeto, utilizaremos as seguintes ferramentas:

* **Python:** Linguagem de programação principal.
* **Flask / FastAPI:** Micro-frameworks para criar o nosso servidor web que vai "escutar" a chegada dos webhooks.
* **Ngrok:** Uma ferramenta essencial para testes locais. Ele cria um túnel seguro (uma URL pública) que redireciona as requisições da internet para o nosso `localhost`.
* **Postman / Insomnia:** Para simular o envio de webhooks manualmente antes de conectar com serviços reais (como o GitHub ou Stripe).

## 4. O Fluxo de Funcionamento de um Webhook

1.  **Ocorreu um Evento:** Algo acontece no sistema de origem (ex: alguém fez um *commit* no GitHub, um pagamento foi aprovado, etc.).
2.  **Geração do Payload:** O sistema de origem empacota as informações desse evento, geralmente no formato **JSON**.
3.  **Envio (POST Request):** O sistema de origem envia esses dados via requisição HTTP POST para uma URL específica que nós configuramos (nossa rota do Webhook).
4.  **Recepção e Processamento:** Nosso servidor Python recebe a requisição, lê o JSON e executa a lógica desejada (ex: salvar no banco de dados, enviar um email de aviso).
5.  **Resposta de Confirmação:** Nosso servidor precisa retornar um status de sucesso (geralmente `200 OK`) rápido, apenas para dizer ao sistema de origem: *"Mensagem recebida, obrigado!"*.\

6.  teste 1
