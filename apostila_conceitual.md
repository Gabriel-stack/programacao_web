# Apostila de Programação Web Focado no PHP

# Conceitos de aplicações Web - Requisições e Respostas

No desenvolvimento de aplicações web, é importante entender o conceito de requisições (request) e respostas (response). Quando um usuário acessa uma página web, ele envia uma requisição para o servidor, isto é, uma solicitação de algo. O servidor, por sua vez, processa essa requisição e envia uma resposta ao usuário, essa resposta pode ser uma página HTML, um arquivo CSS, um arquivo JavaScript, uma imagem, um arquivo de áudio, um arquivo de vídeo, entre outros.

No caso do processamento das requisições, o servidor pode executar scripts de diversas linguagens de programação, como PHP, Python, Ruby, Java, C#, entre outras. No nosso caso, vamos focar no PHP.

# Introdução 

O PHP é uma linguagem de programação de uso geral, muito utilizada no desenvolvimento de aplicações web. As características do PHP são:
- É gratuito para baixar e usar;
- É um acrônimo para "PHP: Hypertext Preprocessor";
- É uma linguagem de script de código aberto amplamente usada;
- scripts são um conjunto de instruções para que uma função seja executada.
- Os scripts PHP são executados no servidor;
- PHP é adequado para o desenvolvimento web e que pode ser embutida dentro do HTML.
- O seu código é executado no servidor e o navegador recebe os resultados da execução desse script, mas não tem acesso ao código fonte.

## Sintaxe Básica, Variáveis e Operadores

### Sintaxe
Para criar um script PHP, basta abrir e fechar as tags PHP ```<?php``` e ```?>```. Dentro dessas tags, você pode escrever o código PHP. 

```php
<?php
	echo "Olá, Mundo!";
?>
```

Todavia, como escrevi anteriormente, o PHP é uma linguagem de script embutida no HTML. Portanto, você pode escrever o código PHP dentro de uma página HTML. 

```html
<!DOCTYPE html>
<html>
<head>
	<title>Título</title>
</head>
<body>
	<?php
		echo "Olá, Mundo!";
	?>
</body>
</html>
```
Isso vai acontecer bastante quando estivermos criando páginas web dinâmicas, onde o conteúdo da página é gerado a partir de um script PHP.

Outra sintaxe do PHP é a que é usada para somente imprimir valores na tela, não necessitando usar o ```echo```.  

```php
<?php
	$nome = "Fulano";
?>

<!DOCTYPE html>
<html>
<head>
	<title>Título</title>
</head>
<body>
	<p>Olá, <?= $nome; ?>!</p>
</body>
</html>
```
Dessa forma, o PHP vai imprimir o valor da variável ```$nome``` na tela.
***Não é recomendado usar a segunda forma caso você precise de mais coisas do que somente imprimir o valor de uma variável.***


### Variáveis

Variáveis em todas as linguagens de programação são usadas para armazenar valores. No PHP, as variáveis são declaradas com o símbolo de cifrão ```$```. Diferentemente de outras linguagens, o PHP é uma linguagem que não é necessário declarar o tipo da variável (int, string, float, etc). O tipo da variável é definido a partir do valor que é atribuído a ela. Exemplo:

```php
<?php
	$nome = "Fulano";
	$idade = 20;
	$altura = 1.80;
	$casado = false;
	$filhos = [
		"João",
		"Maria",
		"José"
	];
?>
```

#### Tipos de Dados

- String: é uma sequência de caracteres, como "Olá, Mundo!";
- Int: é um número inteiro, como 20;
- Float: é um número decimal, como 1.80;
- Boolean: é um valor lógico, verdadeiro ou falso;
- Array: é uma coleção de valores, como o exemplo acima.
#### Regras de nomenclatura de variáveis

- Deve começar com ```$```;
- Não pode começar com números;
- Não pode conter espaços;
- Não pode conter caracteres especiais, exceto o ```_```;

#### Arrays
Os arrays merecem um tópico mais aprofundado. No PHP, os arrays são usados para armazenar vários valores em uma única variável. Existem dois tipos de arrays no PHP: os arrays indexados e os arrays associativos.
Para criar um array, podemos usar a função ```array()``` ou a sintaxe de colchetes ```[]```. Exemplo:

```php
<?php
	$filhos = array();
	ou
	$filhos = [];
?>
```
No nosso caso, vamos sempre usar a sintaxe de colchetes ```[]```.
##### Arrays indexados

Os arrays indexados são arrays que têm um índice numérico. O índice começa em 0, assim como na linguagem C que vocês viram no 1º Ano. Exemplo:

```php
<?php
	$filhos = [
		"João",
		"Maria",
		"José"
	];
?>
```
Acima, o array ```$filhos``` tem três elementos e cada elemento tem um índice numérico: 0, 1 e 2, respectivamente.

Para acessar um elemento de um array indexado, basta usar o índice do elemento que deseja acessar. Exemplo:

```php
<?php
	echo $filhos[0]; // João
	echo $filhos[1]; // Maria
	echo $filhos[2]; // José
?>
```

##### Arrays associativos

Os arrays associativos são arrays que têm um índice associado a um valor. Em outras palavras, o índice você dá o identificador do valor. Exemplo:

```php
<?php
	$pessoa = [
		"nome" => "Fulano",
		"idade" => 20,
		"altura" => 1.80
	];
?>
```
Acima, o array ```$pessoa``` tem três elementos e cada elemento tem um índice associado a um valor: "nome", "idade" e "altura".
A sintaxe de um array associativo é ```"índice" => "valor"```.


### Operadores

#### Aritméticos

- Adição: ```+```, exemplo: ```$soma = 2 + 2;```
- Subtração: ```-```, exemplo: ```$subtracao = 2 - 2;```
- Multiplicação: ```*```, exemplo: ```$multiplicacao = 2 * 2;```
- Divisão: ```/```, exemplo: ```$divisao = 2 / 2;```
- Módulo: ```%```, exemplo: ```$modulo = 2 % 2;```

#### Lógicos

- Igual: ```==```, exemplo: ```$igual = 2 == 2;```
- Diferente: ```!=```, exemplo: ```$diferente = 2 != 2;```
- Maior: ```>```, exemplo: ```$maior = 2 > 2;```
- Menor: ```<```, exemplo: ```$menor = 2 < 2;```
- Maior ou igual: ```>=```, exemplo: ```$maior_igual = 2 >= 2;```
- Menor ou igual: ```<=```, exemplo: ```$menor_igual = 2 <= 2;```
- E: ```&&```, exemplo: ```$e = true && false;```
- Ou: ```||```, exemplo: ```$ou = true || false;```

#### De strings

- Concatenação: ```.```, exemplo: ```$concatenacao = "Olá, " . "Mundo!";```
- Concatenação e atribuição: ```.=```, exemplo: ```$concatenacao .= " Como você está?";```

## Estruturas de Controle de Fluxo

Todas as linguagens de programação possuem estruturas de controle de fluxo, que são usadas para controlar o fluxo de execução de um programa. No PHP, as estruturas de controle de fluxo têm a seguinte sintaxe:

### Condicional

#### If

```php
<?php
	if (condição) {
		// código a ser executado
	} else {
		// código a ser executado	
	}
?>
```

#### switch

```php
<?php
	switch (variável) {
		case valor1:
			// código a ser executado
			break;
		case valor2:
			// código a ser executado
			break;
		default:
			// código a ser executado
			break;
	}
?>
```

### Repetição

#### For

```php
<?php
	for ($contador = 0; $condicao_de_parada; $contador++) {
		// código a ser executado
	}
?>
```

#### While

```php
<?php
	while (condição) {
		// código a ser executado
	}
?>
```

#### Foreach
O ```foreach``` é uma estrutura de repetição usada para percorrer arrays. Mais adiante, vamos falar sobre arrays, mas por enquanto, vamos ver a sintaxe do ```foreach``` com o exemplo abaixo. 
```php
<?php
	$filhos = [
		"João",
		"Maria",
		"José"
	];

	foreach ($filhos as $filho) {
		echo $filho;
	}
?>

```
ou
```php
<?php
	$familias = [
		[
			"nome" => "Fulano",
			"idade" => 20
		],
		[
			"nome" => "Ciclano",
			"idade" => 30
		],
		[
			"nome" => "Beltrano",
			"idade" => 40
		]
	];

	foreach ($familias as $familia) {
		echo $familia["nome"];
	}
?>
```

## Require_once, Include_once e Define

### Define

No PHP nós temos as variáveis que podem ser alteradas durante a execução do script, mas também temos as constantes. As constantes são valores que não mudam. Elas são mais usadas para armazenar informações que vão ser usadas em várias partes do script.  Para definir uma constante, usamos a função ```define()``` que recebe dois parâmetros: o nome da constante e o valor da constante. Exemplo:

```php
<?php
	define("URL_LOGIN", "http://localhost/login");
	define("URL_LOGOUT", "http://localhost/logout");
	define("BANCO_SENHA", "123456");
?>
```
Veja que criamos três constantes: ```URL_LOGIN```, ```URL_LOGOUT``` e ```BANCO_SENHA```. A partir de agora, essas constantes vai sempre retornar o valor que foi definido. Para eu acessar o valor de uma constante, basta chamar o nome da constante. Exemplo:

```php
<?php
	echo URL_LOGIN;
	echo URL_LOGOUT;
	echo BANCO_SENHA;
?>
```

**Perceba que não é necessário usar o cifrão ```$``` para acessar o valor de uma constante.**

Obs: Quando trabalhamos com PHP, precisamos separar vários arquivos que fazem coisas diferentes. Nesse sentido, é comum termos um arquivo que contém todas as constantes do sistema. Logo, as constantes criadas só serão acessadas se o arquivo que contém as constantes for incluído no arquivo que está sendo executado. E por isso, usamos o ```require_once``` ou ```include_once```.

### Require_once e Include_once
Imagine o cenário que você tem dois arquivos: ```index.php``` e ```config.php```. No arquivo ```config.php``` você tem todas as constantes do sistema. Você está trabalhando no arquivo ```index.php``` e precisa acessar as constantes do arquivo ```config.php```. Então como você faz isso? Você usa o ```require_once``` ou ```include_once```. 

Arquivo ```config.php```
```php
<?php
	define("USUARIO", "root");
?>
```

Arquivo ```index.php```
```php

<?php
	echo USUARIO;
?>
```

Se tentarmos acessar a constante ```USUARIO``` o PHP vai retornar um erro. Isso porque para  o arquivo ```index.php``` não existe a constante ```USUARIO```. Para resolver,precisamos fazer com que o arquivo ```config.php``` seja incluído no arquivo ```index.php```. para fazer isso, usamos o ```require_once``` ou ```include_once``` da seguinte forma: 
```php
<?php
	require_once "config.php"; // ou include_once "config.php";
	echo USUARIO;
?>
```
Dessa forma, o arquivo ```config.php``` vai ser incluído no arquivo ```index.php``` e a constante ```USUARIO``` vai ser acessada.

### Diferença entre Require_once e Include_once

A diferença entre o ```require_once``` e o ```include_once``` é que o ```require_once``` vai parar a execução do script caso o arquivo que está sendo incluído não exista. Já o ```include_once``` vai continuar a execução do script, mesmo que o arquivo que está sendo incluído não exista.

### Atenção aos caminhos dos arquivos
Todo projeto é dividido em pastas e subpastas. Quando você está trabalhando com o PHP, é importante saber o caminho dos arquivos que você está incluindo. Por exemplo, se você tem um arquivo ```index.php``` na raiz do projeto e um arquivo ```config.php``` na pasta ```config```, você precisa informar o caminho do arquivo que está sendo incluído. Exemplo:

```php
<?php
	require_once "config/config.php";
?>
```

Em outros casos, você precisará "voltar" pastas para incluir um arquivo. Exemplo:

```php
<?php
	require_once "../config.php";
?>
```

O ```../``` é usado para voltar uma pasta em um sistema operacional.

# Aprofundando em PHP

Nessa etapa, vamos aprofundar um pouco mais no PHP. Vamos falar sobre funções, formulários, requisições, variáveis globais, arquitetura de pastas e funções mais utilizadas. Vamos começar pela arquiteura de pastas pois será a que vamos usar para criar nossos projetos em sala.

## Arquitetura de pastas
meu_projeto/
│
├── Config/
│   
│
├── Database/
│   
│
├── Forms/
│   
│
├── Pages/
├────── Template/
│	
│   
│ 
└── index.php


Nessa arquitetura, temos as seguintes pastas:
- Config: Onde vão ficar, por exemplo os arquivos para constantes, funções, manipulação de sessão e inicialização do projeto.
- Database: Onde vão ficar os arquivos para conexão com o banco de dados e arquivos especificos para manipulação de dados de cada tabela.
- Forms: Onde vão ficar os arquivos para validação de formulários (Veremos sobre formulários no próximo tópico). Para cada ação de um formulário, teremos um arquivo específico, por exemplo, um arquivo para cadastro, um arquivo para login, etc.
- Pages: Onde vão ficar os arquivos para as páginas do projeto. Dentro dessa pasta, teremos a pasta Template, onde vão ficar os arquivos para o cabeçalho, rodapé e menu do projeto.
- Arquivos da raiz: Onde vão ficar os arquivos que vão ser acessados diretamente pelo usuário, como o ```index.php``` e ```login.php```.

## Formulários e Requisições

Essa parte é muito importante no desenvolvimento de aplicações web. Os formulários são usados para coletar informações do usuário. No PHP, os formulários são enviados para o servidor e processados. Para criar um formulário, usamos a tag ```<form>``` do HTML. Exemplo:

```html
<form action="" method="" enctype="">
	<label for="nome">Nome:</label>
	<input type="text" name="nome" id="nome">
</form>
```

O formulário possui três atributos importantes:
- action: Para onde vai ser enviado o formulário. Se o valor for vazio, o formulário vai ser enviado para a mesma página (mesmo arquivo PHP). No nosso caso, esse formulários vai estar em algum arquivo PHP da pasta ``pages`` e enviaremos para um arquivo de validação na pasta ``forms``. Fazendo assim, a separação de responsabilidades por arquivo.
- method: Como os dados do formulário vão ser enviados. Pode ser ```GET``` ou ```POST```. O ```GET``` envia os dados do formulário pela URL, enquanto o ```POST``` envia os dados do formulário de forma oculta.
- enctype: Tipo de codificação dos dados do formulário. Pode ser ```application/x-www-form-urlencoded``` ou ```multipart/form-data```. O primeiro é usado para formulários simples, enquanto o segundo é usado para formulários que enviam arquivos. Não é necessário usar esse atributo se o formulário não envia arquivos. Vejamos um exemplo simples de um formulário de login:

```html
<form action="forms/login.php" method="post">
	<label for="email">E-mail:</label>
	<input type="email" name="email" id="email">
	<label for="senha">Senha:</label>
	<input type="password" name="senha" id="senha">
	<button type="submit">Entrar</button>
</form>
```

No exemplo acima, o formulário vai ser enviado para o arquivo ```login.php``` da pasta ```forms``` e os dados do formulário vão ser enviados de forma oculta pois usamos o método ```POST```. É necessário que seja POST pois estamos enviando dados sensíveis, como a senha do usuário, e isto não deve ser enviado pela URL (GET).

### Requisições

Quando um formulário é enviado, o PHP recebe os dados do formulário e processa esses dados. Para acessar os dados do formulário, usamos as variáveis globais ```$_GET``` e ```$_POST```. O ```$_GET``` é usado para acessar os dados do formulário que foram enviados pelo método ```GET```, enquanto o ```$_POST``` é usado para acessar os dados do formulário que foram enviados pelo método ```POST```. Mas para isso precisamos entender o uso dessas variáveis globais.

Quando as requisições forem do tipo ```GET```, os dados do formulário vão ser enviados pela URL. Veja o exemplo de URL abaixo:

```html
http://localhost/index.php?nome=Fulano&idade=20
```
Nesse caso, os dados do formulário são ```nome``` e ```idade```. Para acessar esses dados e o ``&`` é usado para separar os dados do formulário.

## Variáveis globais: ```$_GET, $_POST, $_SESSION e $_REQUEST```

Variáveis globais são variáveis que podem ser acessadas de qualquer parte do script PHP. No PHP, temos várias variáveis globais, mas as mais usadas são ```$_GET```, ```$_POST```, ```$_SESSION``` e ```$_REQUEST```. Vamos falar sobre cada uma delas.

### $_GET

O ```$_GET``` é uma variável global usada para acessar os dados do formulário que foram enviados pelo método ```GET```. Para acessar os dados do formulário, usamos o nome do campo do formulário. Exemplo:

```php
URL: http://localhost/index.php?nome=Fulano&idade=20

<?php
	echo $_GET["nome"]; // Fulano
	echo $_GET["idade"]; // 20
?>
```
No caso, estamos usando echo para imprimir o valor do campo do formulário mas para acessar o valor do campo do formulário, basta usar o nome do campo do formulário entre colchetes da variável global ```$_GET```. Veja um exemplo de outro uso, agora para comparar os valores enviados:

```php
<?php
	if ($_GET["idade"] >= 18) {
		echo "Maior de idade";
	} else {
		echo "Menor de idade";
	}
?>
```

### $_POST

O ```$_POST``` é uma variável global usada para acessar os dados do formulário que foram enviados pelo método ```POST```. O uso é o mesmo do ```$_GET```. Como o ```$_POST``` envia os dados do formulário de forma oculta, os dados do formulário não são enviados pela URL. Exemplo de código para acessar os dados do formulário via ```$_POST```:

```php
<?php
	echo $_POST["email"];
	echo $_POST["senha"];
?>
```
Usando para comparar os valores enviados:
```php
<?php
	if ($_POST["senha"] == "123456") {
		echo "Senha correta";
	} else {
		echo "Senha incorreta";
	}
?>
```

### $_SESSION

A variável global ```$_SESSION``` merece um destaque especial. Ela é usada para armazenar informações do usuário durante a sessão, isto é, enquanto o usuário estiver navegando no site. Para usar a variável global ```$_SESSION```, é necessário iniciar a sessão com a função ```session_start()```. Exemplo:

```php
<?php
	session_start();
	$_SESSION["nome"] = "Fulano";
?>
```
No exemplo acima, estamos armazenando o nome do usuário na variável global ```$_SESSION```. Agora o valor da variável ```$_SESSION["nome"]``` pode ser acessado em quaquer parte do site enquanto o usuário estiver navegando. Exemplo de uso:

```php

<h2>Olá, <?= $_SESSION["nome"]; ?>!</h2>
```

No código acima, o nome do usuário vai ser impresso na tela.

#### Funções de sessão

##### session_start()

Inicia a sessão. Essa função deve ser chamada antes de acessar ou definir qualquer variável de sessão.

##### session_destroy()

Encerra a sessão. Essa função é usada para encerrar a sessão do usuário.

##### session_unset()

Remove todas as variáveis de sessão. Essa função é usada para remover todas as variáveis de sessão.


## Funções mais utilizadas - isset, empty, header, unset e criação de outras funções
Funções são um conjunto de instruções que são usadas para executar uma tarefa específica que pode ser reutilizada em várias partes do script.

No PHP, temos várias funções que são muito utilizadas no desenvolvimento de aplicações web. Algumas são caracterizadas como funções que sempre estão presentes em um projeto.

### isset

A função ```isset()``` é usada para verificar se uma variável foi definida. Ela retorna ```true``` se a variável foi definida e ```false``` se a variável não foi definida.  Resumindo, verifica se a variável existe. Exemplo de uso com a variável global ```$_GET```:
Alguém acessou a URL: ``http://localhost/index.php?nome=Fulano``
no arquivo index.php queremos saber se a variável nome foi definida:

```php
<?php
	if (isset($_GET["nome"])) {
		echo "A variável nome foi definida";
	} else {
		echo "A variável nome não foi definida";
	}
?>
```
Ela verifica não somente uma variável, mas várias variáveis. Exemplo:

```php
<?php
	if (isset($_GET["nome"], $_GET["idade"])) {
		echo "As variáveis nome e idade foram definidas";
	} else {
		echo "As variáveis nome e idade não foram definidas";
	}
?>
```

### empty

A função ```empty()``` é usada para verificar se uma variável está vazia. Ela retorna ```true``` se a variável estiver vazia e ```false``` se a variável não estiver vazia. VEja que diferente do ```isset()```, o ```empty()``` não verifica se a variável foi definida, mas sim se ela está vazia contém algum valor. Exemplo:

```php
<?php
	$nome = "";
	if (empty($nome)) {
		echo "A variável nome está vazia";
	} else {
		echo "A variável nome não está vazia";
	}
?>
```

### header

A função ```header()``` serve para, na maioria dos casos, redirecionar o usuário para outra página. Por exemplo, quando o usuário faz login, o sistema vai validar os dados do usuário e, se os dados estiverem corretos, o sistema vai redirecionar o usuário para a página inicial.  Atrelado a ela, sempre é bom usar o ```exit()``` ou ```die()``` para parar a execução do script. Exemplo de uso:

```php
<?php
	if($email == "usuario@email.com" && $senha == "123456") {
		header("Location: index.php");
		die();
	} else {
		header("Location: login.php");
		die();
	}
?>
```

### unset

A função ```unset()``` serve para remover/apagar uma variável. Exemplo:

```php
<?php
	$nome = "Fulano";
	unset($nome);
	echo $nome; // Vai retornar um erro
------------------------------------------------
						ou
------------------------------------------------
	$dados = [
		"nome" => "Fulano",
		"idade" => 20
	];
	unset($dados["nome"]);
	echo $dados["nome"]; // Vai retornar um erro
	echo $dados["idade"]; // Vai retornar 20
?>
```

