# Squad 22 - Rede Social - Unit

## Descrição
Neste repositório se encontram todos os códigos produzidos pelo Squad 22 durante a Residência de Software 2024.1 do Porto Digital pela UNIT-SE, assim como links e guias para utilização daquilo foi produzido pelo squad.
Especificamente, nesse repositório se encontram submodulos para os repositórios que hospedam o código das aplicações de backend e frontend produzidos pelo squad, e ainda neste readme, serão indexados links para acesso a aplicação e ao repositório do docker onde se encontram images para a execução local dos contêiners do banco de dados e da aplicação Spring Boot utilizada em nosso servidor.

## Index
1. Acesso ao MVP
   - Guia de Uso da Interface do MVP
   - Guia de Uso do Servidor do MVP
3. Acesso aos Contêineres
4. Utilização dos Contêineres
5. Utilização dos Repositórios

## Acesso ao MVP
A aplicação, em 20/05/2024, encontra-se online na nuvem, seu servidor e banco dados estão na Azure, enquanto que um MVP do seu frontend está hospedada na [Netlify](https://transcendent-genie-292011.netlify.app/). esse frontend fornece uma interface não tão rebuscada que permite a utilização de alguns dos recursos do servidor para dar ao usuário uma experiência de utilização da rede social.
### Guia de Uso do Frontend do MVP
Para utilizar o MVP através do link da Netlify, primeiro clique em **Create Account** e vá para a tela de registro, crie uma conta com uma das três modalidades estudante, professor ou comercial, forneça as informações especificas de cada conta e clique em **Register**, em seguida, clique na seta no canto superior esquerdo e retorne para a tela de login, na tela de login insira o nome de usuário (**username**) e a senha (**password**) da conta criada, assim você será direcionado para sua página de usuário. 
Dentro da página de usuário é possível criar posts e comunidades através do menu na parte direita da tela, os posts e comunidades podem ser vistos clicando em **Posts** e **Comunidades**, botões localizados abaixo das informações do usuário. Na página de usuário, também é possível pesquisar pelo nome de um usuário na barra de pesquisa no canto superior direito, para pesquisar, digite um nome de usuário (ex. yuri) e clique no icone de lupa.
### Guia de Uso do Servidor do MVP
Assim como a interface hospedada no Netlify, nosso servidor também foi implementado na nuvem e pode ser utilizado através de aplicações de teste de API, como o Postman, Insomnia ou [ReqBin](https://reqbin.com/). Para utilizar o servidor desta forma, utilize a url https://squad22-web-app-container.azurewebsites.net em uma dessas aplicações. Após, adicione /auth/register para acessar o endpoint de registro de conta, esse endpoint não precisa de autenticação e recebe o seguinte tipo de objeto para criar a conta:
```
{
  "username": "",
  "name": "",
  "password": "",
  "registration": 0,
  "accountType": "",
  "activityStatus": "",
  "course": "",
  "classes": [],
  "courses": [],
  "degrees": [],
  "stores": [],
  "services": [],
  "opening": "",
  "closing": ""
}
```
Os campos de *username* até *activityStatus* são obrigatórios, enquanto os campos *course* e *classes* são campos do *accountType* ESTUDANTE, *classes*, *courses* e *degrees* são campos de PROFESSOR, e os últimos campos são para o *accountType* COMERCIAL.

Depois de criar a conta, retire o /auth/register da url e use /auth/login para utilizar o endpoint de login, esse endpoint precisa apenas do seguinte objeto:
```
{
  "username": "",
  "password": ""
}
```
Quando chamado corretamente ele deverar retornar o Bearer token que será utilizado para as próximas requisições ao servidor. Para exemplo de uma requisição utilizando o token, retire o /auth/login do final da url e acrescente /api/posts/usuario/:username (adicione um nome de usuário no lugar de :username), em seguida procure alguma opção de adicionar autorização na sua aplicação de teste de API e selecione Bearer e coloque o token retornado da requisição de login onde pedir. Essa requisição não precisa de corpo, apenas do parâmetro :username e do token, ela deverá retornar um objeto contendo todos os dados dos posts do usuário utilizado como parâmetro.

# Continua...
