# PROJETO PARTE - 2 - Criando a página de cadastro e entendendo funcionamento dos métodos  ```GET``` e ```POST```


## Criando a página de cadastro

No arquivo [parte1.md](parte1.md) criamos a página de login, agora vamos criar a página de cadastro.

Na pasta ```pages``` crie um arquivo chamado ```page_cadastro.php``` e adicione o seguinte código:

```php
<?php require_once 'template/head.php'; ?>
// aqui vai o conteúdo da página
<?php require_once 'template/footer.php'; ?>
```

Isso vai fazer com que a página de cadastro tenha o mesmo cabeçalho e rodapé que as outras páginas (template).

Agora onde tem o comentário ```// aqui vai o conteúdo da página``` substitua pelo seguinte código:

```php
<body class="vh-100 bg-light">
	<div class="container h-100 d-flex justify-content-center align-items-center flex-column">
		<h3 class="text-center">Cadastro</h3>
		<form class="d-flex flex-column gap-2 p-4" style="min-width:360px" action="" method="POST">
			<input class="form-control" name="nome" type="text" placeholder="Nome">
			<input class="form-control" name="email" type="email" placeholder="Email">
			<input class="form-control" name="senha" type="password" placeholder="Senha">
			<button class="btn btn-success" type="submit">Cadastrar</button>
			<p class="text-center">já tem uma conta? <a href="login.php">Logar</a></p>
		</form>
	</div>
</body>
```
Essa é uma estrutura HTML básica de um formulário de cadastro, com campos de nome, email e senha que foi feita usando bootstrap 5.3.


## Criando arquivo para chamar a página de cadastro

Como foi falado, na raiz do projeto sempre vai existir um arquivo que vai ficar responsável por pegar os dados do banco, por definir o título da página e chamar a página referente. Vamos criar o arquivo ```cadastro.php``` na raiz do projeto e adicionar o seguinte código:

```php

<?php 

require_once 'configs/init.php';

$title = "Cadastro";

require_once 'pages/page_cadastro.php';

```

## Entendendo funcionamento das variáveis Globais ```$_GET``` e ```$_POST```

A gente criou dois formulários: um de login e outro de cadastro. Esses formulários têm um propósito: enviar dados para o servidor, lá ele processa esses dados e retorna uma resposta.

Para enviar esses dados para o servidor, a gente pode usar basicamente dois métodos: GET e POST.
O método GET envia os dados pela URL, enquanto o método POST envia os dados pelo corpo da requisição.
No nosso caso, como esses dois formulários trata-se de dados sensíveis, sempre usamos o método POST.

No formulário de cadastro, na tag ```<form>``` temos o atributo ```method```, é nele que definimos o método que queremos usar para enviar os dados. No caso do formulário de cadastro vá até o arquivo ```page_cadastro.php``` e veja que o atributo ```method``` está definido como ```POST```, se não estiver, defina.

Outro atributo que temos que definir é o ```action```, que é o arquivo que vai receber os dados do formulário. No caso do formulário de cadastro, o atributo ```action``` está vazio. Vamos mudar para ```forms/form_cadastro.php```.

Na nossa estrutura de projeto, a pasta `forms` fica responsável por armazenar os arquivos que vão receber os dados dos formulários. Vamos criar o arquivo `form_cadastro.php` na pasta `forms` e vamos importar o arquivo `configs/init.php` e vamos fazer um teste para ver se está tudo funcionando.

```php
<?php

require_once '../configs/init.php';
```

### $_POST

A variável global ```$_POST``` é um array associativo que armazena os dados enviados pelo método POST. Para acessar os dados enviados pelo formulário de cadastro, basta acessar a variável ```$_POST``` e passar o nome do campo que você quer acessar, mas tem que ser um campo que você definiu no formulário.

### $_GET

A variável global ```$_GET``` também é um array associativo que armazena os dados só que enviados pelo método GET. Para acessar os dados enviados pelo método GET, basta acessar a variável ```$_GET``` e passar o nome do campo que você quer acessar, mas tem que ser um campo que você definiu na URL.

### Usando a variável global para verificar os dados

Ao receber os dados, a primeira coisa que a gente tem que fazer é verificar se os dados foram enviados e se estão preenchidos. Para fazer isso, vamos usar condições IF-ELSE junto com uma função chamada `empty()`.

```php

if(empty($_POST['nome']) || empty($_POST['email']) || empty($_POST['senha'])){
	echo "Preencha todos os campos";
}else{
	$nome = $_POST['nome'];
	$email = $_POST['email'];
	$senha = $_POST['senha'];

	echo "$nome foi cadastrado com sucesso!";
}

```