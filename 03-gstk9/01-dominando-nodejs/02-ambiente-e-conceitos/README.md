## Instalar o Node.JS no Linux

**https://github.com/nvm-sh/nvm**

* nvm install node (version)

### Setando como padrão

    * nvm alias default versionNumber (ex: nvm alias default 16.13.2)

## Instalar no Windows

  **https://chocolatey.org/install**

  * Ir no site do Node e clicar em <em>other downloads => Installing Node.js via package mananger => Windows </em>.

## Instalar o yarn: mais rápido e tem um leque de ferramentas mais avançadas para criarmos projetos Node, React, React Native

**https://yarnpkg.com/pt-BR/**

# O que é Node.js?

* JavaScriptt no back-end
  * Cria Regras de negócio;  
  * Não lidamos com eventos do usuario final;
  * Rotas e integrações;
* Plataforma (não linguagem);
* Construída em cima da V8 (motor do Chrome); 
* Comparável a PHP / Ruby / Python / Go ou qualquer outra linguagem que se aplica do lado do back-end;

## O que é o NPM?

  * Instalar bibliotecas de terceiros;
  * Fornecer bibliotecas;
  * Por que utilizaremos o Yarn?
    * Mais rápido e está avançando mais rápido?
  * Comparáveis:
    * Composer do PHP;
    * Gems do Ruby;
    * PIP do Python

## Características do Node

* Arquitetura Event-loop
  * Baseada em eventos (rotas na maioria das vezes);
  * Call Stack (pilha de eventos que o Node processa através de um loop eterno vendo que há alguma nova função para ser executada);
* Node single-thread (executa em apenas um core do processador);
  *  C++ por trás com libuv;
  *  Background threads (multi-threads);
* Non-blocking I/O (input e output não bloqueante);
  *  Quando fazemos uma requisição para o Node, acessando uma página que  retorna uma listage, por exemplo, não precisamos retornar todos os dados dessa listagem de uma só vez, mas podemos retorná-la em partes, pois por dar uma resposta ao cliente, não significa que bloquearemos o resultado daí pra frente.
  *  Isso não acontece em outras linguagens, como por exemplo, o PHP que, a partir do momento que é dada uma respota, por exemplo em html, um texto, um JSON ou um xml, a partir desse momento é perdida a conexão do font-end com o back-end. No Node isso não acontece, isso permite ter aplicação em tempo real. (Ex. chat)

## Frameworks

* ExpressJS como base:
  * Sem opinião (não tem uma estrutura fechada, ou seja, podemos iniciar como quisermos);
  * Ótimo para iniciar;
  * Micro-serviços;
* Frameworks opinados:
  * AdonisJS;
  * NestJS;

# API REST

## O que é API?
  * Application Programming Interface (Interface de Programação de Aplicativos);
  * Conjunto de especificações de possíveis interações entre aplicações
  * Documentação para desenvolvedor;

## O que é REST?
  * Representation State Transfer (Tranferência Representacional de Estado);
  * Modelo de arquitetura
  * 6 regras:
    * 1 - Client-Server: de um lado o servidor e do outro o cliente (um não precisa conhecer o que o outro está fazendo);
    * 2 - Stateless: o cliente pode fazer quantas requisições quiser ao servidor, porém o servidor não armazena nenhuma estado dessas requisições/sessões, ou seja, a cada requisição que fizermos, precisamos fornecer todas as informações para que aquela requisição seja processada;
    * 3 - Cache - nossa palicaçao precisa ser construída de uma forma que o cache possa ser feito, mas isso não significa precisamos iniciar nossa aplicação já com o cache, mas garantir que ela vai ter suporte para o cache no futuro.
    * 4 - Interface Uniforme
      * Identicação dos recursos
        * http://enderecodoservidor.com.br/products
        * http://enderecodoservidor.com.br/clients
      * Representaçao dos recursos
      * Mensagens auto-descritivas
        * (Ex: o que fazer se ocorrer o erro tal em nossa API)
      * HATEOAS (Hypertext As The Engine Of Application State): retornar links dentro da nossa requisição.
        * Ex:
        ```json
        {
          "id": 1,
          "user": "carloslima",
          "created_at": "2020-10-10",
          "commentsLink": "api/users/1/comments"
        }
        ```
    * 5 - Camadas (camadas entre o client e o server)
      * Ex: balanceamento de cargas, segurança, entre outros...
    * 6 - Código Sob Demanda (opcional): permite que as funcionalidades do cliente sejam estendidas na forma de scripts ou mini-aplicativos.


## Métodos de requisições - HTTP Verbs

  * GET - Leitura
    * Ex: quando queremos buscar uma informação, uma lista, um ID, sou seja,  sempre que precisarmos fazer uma leitura.
  * POST - Criação
  * PUT - Atualização
  * DELETE - Deleção
  * PATCH - Atualização parcial

## HTTP Codes

  * 1XX: Informativo - a solicitação foi aceita ou o processo continua em andamento;
  * 2XX: Confirmação
    * 200 - Requisição bem sucedida
    * 201 - Created - Geralmente usado para POST após inserção
  * 3XX: Redirecionamento
    * 301 - Moved Permanently
    * 302 - Moved
  * 4XX: Erro do cliente
    * 400 - Bad Request
    * 401 - Unauthorized
    * 403 - Forbidden
    * 404 - Not Found
    * 422 - Unprocessable Entity
  * 5XX: Erro no servidor - o servidor falhou ao concluir a solicitação.
    * 500 - Internal Server Error
    * 502 - Bad Gateway

## Parâmetros das Requisições
  * Header Params
      ```js
      authority: app.rocketseat.com.br
      method: GET
      path: /api/journey-nodes
      scheme: https
      referer: https://app.rocketseat.com.br/node/
      ```
  * Query Params: parâmetros inseridos no final de uma url
    * http://enderecoservidor.com.br/v1/users?page=2&limit=50
    * Chave(page / limit)
    * Valor (2 / 50)
    * Separação (&)
  
  * Route Params
    * http://enderecoservidor.com.br/v1/user/{id}

  * Body Params: parâmetros no corpo da requisição
    Ex:
    ```json
    {
      "name": "Carlos",
      "username": "TI"
    }
    ```
## Boas práticas API REST

  * A utilização correta dos métodos HTTP;
  * A utilização correta dos status no retorno das respostas
  * Padrão de nomenclatura
    * Busca de usuários - GET
      * https://enderecoservidor.com.br/v1/users
    * Busca de usuário por id - GET
      * https://enderecoservidor.com.br/v1/users/1
    * Busca de endereço do usuário - GET
      * https://enderecoservidor.com.br/v1/users/1/address
    * Deleção de um usuário - DELETE
      * https://enderecoservidor.com.br/v1/users/1
    * Atualização do status do usuário - PATCH
      * https://enderecoservidor.com.br/v1/users/1/status
