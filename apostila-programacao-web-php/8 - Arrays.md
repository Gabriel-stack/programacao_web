# Arrays

 No PHP, os arrays são usados para armazenar vários valores em uma única variável. Existem dois tipos de arrays no PHP: os arrays indexados e os arrays associativos.

Para criar um array, podemos usar a função ```array()``` ou a sintaxe de colchetes ```[]```. Exemplo:

```php
<?php
    $filhos = array();
    // ou
    $filhos = [];

?>

```

## Arrays indexados

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
## Arrays associativos

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

Para acessar um elemento de um array associativo, basta usar o índice do elemento que deseja acessar. Exemplo:

```php

<?php

    echo $pessoa["nome"]; // João

    echo $pessoa["idade"]; // 20

    echo $pessoa["altura"]; // 1.80

?>
```
## Adicionar elementos no array

Em ambos os casos, caso queira adicionar valores manualmente, ou seja, atribuir valores, você pode fazer da seguinte forma:

```php
// Indexado
$nomes[0] = "Gabriel";

// Associativo

$pessoa['nome'] = "Gabriel";

// Associativo + indexado

$pessoas[0]['nome'] = "João";
```

Esse último caso você vai ver no tópico a seguir.

## Arrays associativos multidimensionais

Assim como os tipos de arrays anteriores, o array multidimensional vai guardar vários valores, mas o valor que ele guardar pode ser um array que está dentro do array raiz.  Veja o exemplo a seguir:

```php
<?php

$familia = [
	[
		'nome' => "João",
		'tipo_membro' => "pai",
		'idade' => 45
	],
	[
		'nome' => "Maria",
		'tipo_membro' => "mãe",
		'idade' => 40
	],
	[
		'nome' => "Guilerme",
		'tipo_membro' => "filho",
		'idade' => 10
	]
]
```

O exemplo acima mostra exatamente como um array multidimensional funciona: guarda vários arrays dentro de um array. No caso se eu quisesse acessar o ``tipo_membro`` do segundo membro da família, basta acessar o segundo subarray que está dentro, e em seguida acessar a chave ``tipo_membro``.

```php
echo $familia[1]['tipo_membro'];
```

## Visualizando as estruturas

Quando você estiver desenvolvendo, você precisará checar se os dados estão de acordo com o que você espera, e para fazer isso, basta usar umas das funções a seguir:

```php
$nomes = ["maria", "joaquim"];
// var_dump
var_dump($nomes);
// print_r
print_r($nomes);

```
	