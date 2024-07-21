# Funções

Uma função é um bloco de código independente que executa uma tarefa específica.

O PHP tem uma enorme coleção de funções internas que você pode chamar diretamente em seus códigos para executar uma tarefa específica, como `echo`,  `var_dump`, `die`, funções para manipulação de strings e arrays, etc.

## Funções criadas

Como toda linguagem de programação, você também pode definir uma função para o que você quer fazer. A sintaxe para criar uma função personalizada pode ser fornecida com:

```php
function nomeDaFuncao(){  
    // Código que a função vai executar quando for chamada.
}
```

A declaração de uma função definida pelo usuário começa com a palavra `function`, seguida do nome da função que você deseja criar seguida de parênteses, ou seja, `()`e finalmente coloque o código da sua função entre chaves `{}`.

exemplo:

```php
<?php

function imprimeTitulo(){
	echo "<h1>Olá mundo</h1>";
}

imprimeTitulo(); //chamando a função criada

?>
```

##  Funções com parâmetros

Você pode definir sua função para aceitar valores quando ela é executada. Esses valores, chamados de parâmetros, são como espaços reservados que serão preenchidos na hora da execução pelos argumentos que você fornecer.

```php
<?php

function imprimeTitulo($cor,$texto){
	echo "<h1 style='background-color: $cor;'>$texto</h1>";
}

imprimeTitulo('red', 'Olá mundo'); //chamando a função criada

?>
```

Este código PHP define uma função chamada `imprimeTitulo` que recebe duas informações: uma cor e um texto. Quando a função é chamada, ela cria um título HTML (`<h1>`) com a cor de fundo especificada e o texto fornecido.

Você pode definir quantos parâmetros desejar. No entanto, para cada parâmetro especificado, um argumento correspondente precisa ser passado para a função quando ela for chamada ou passar ele com valor nulo.

## Retorno de funções

Uma função pode retornar um valor usando a palavra-chave `return`. Quando uma função retorna um valor, esse valor pode ser usado em outras partes do código. Veja o exemplo:

```php
<?php 

function somaNumeros($num1, $num2){
	return $num1 + $num2;
}

$n1 = 10;
$n2 = 13;

echo "O valor da soma de $n1 + $n2 é:" .  somaNumeros($n1, $n2);

?>
```

A função pode retornar qualquer tipo de dado.

## Escopo de variáveis

O escopo de uma variável determina onde ela pode ser acessada. Existem dois escopos principais: escopo global e escopo local.

### Escopo Global

Variáveis definidas fora de funções têm escopo global. Elas podem ser acessadas em qualquer lugar no script, exceto dentro de funções, a menos que sejam declaradas explicitamente como globais dentro dessas funções.

### Escopo Local

Variáveis definidas dentro de uma função têm escopo local. Elas só podem ser acessadas dentro da função onde foram definidas.

### Uso da Palavra-chave `global`

A palavra-chave `global` permite acessar variáveis globais dentro de uma função. Aqui está um exemplo:

```php
<?php

$nome = "Gabriel";

function imprimeNome(){
	global $nome;
	echo "O nome da variável global é: $nome";
}

?>
```

