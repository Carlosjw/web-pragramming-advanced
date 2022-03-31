## Adicionando scripts ao package.json

```json

{
    "scripts": {
        "dev": "next",
        "start": "next start",
        "build": "next build"
    }
}

```
### Entendendo

    * "dev": "next" => para ambiente de desenvolvimento. Ele vai gerar a build de nosso projeto todas as vezes em que editarmos um código JavaScript e vai mostrar essa alteração na tela automaticamente.
    * "build": "next build" => vai gerar a build com código totalemente em JavaScript que vai ser envidad para o servidor, de forma que ele (servidor) não vai precisar ficar fazendo esse papel de transpilação e carregamento de build todas as vezes.

    * "start": "next start": roda o Next a partir da build gerada.