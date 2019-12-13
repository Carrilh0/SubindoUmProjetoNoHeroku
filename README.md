# SubindoUmProjetoNoHeroku
Informações necessaria para subir um projeto na plataforma do heroku

* Baixar o CLI do heroku

* Entrar na pasta do projeto e criar um repositorio (caso não haja um)

* Fazer o login no heroku com o comando ```heroku login```

* Criar uma aplicação heroku baseado no repositorio da pasta atual  ```heroku create```

* Configurar as variaveis de ambiente caso seja necessario  ```heroku config:set NAME=Example```

* Fazer um push para o heroku, com isso, acontecerá o build, e aplicação estará no ar | ```push origin heroku master ```

> No caso do laravel, é preciso adicionar o root para a pasta public. Para isso tem o arquivo do heroku chamado ProcfileEle tem o papel de escolher o servidor (que no caso será o apache2) e a pasta que iniciará o sistema, com o comando ```web: vender/bin/heroku-php-apache2 /public```.

> Caso o css não funcione no laravel, o problema pode ser no certificado https do heroku, uma vez em que a aplicação foi definida como production ela pode dar conflito com o http. Para isso deve-se colocar no AppServiceProvider, na função boot, o comando: 

~~~php 
if(config('app.env') === 'production') {
    \URL::forceScheme('https');
}
~~~

> Para executar comando no servidor do heroku é necessario adicionar no composer.json, no objeto scripts, ```"post-install-cmd" ["comando","comando2"] ``` todos os comandos que estiverem dentro do array, serão executados após o build do projeto. 

**OBS: O usuário não tem acesso direto ao terminal do heroku.**
