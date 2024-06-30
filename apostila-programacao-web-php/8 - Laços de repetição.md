# Laços de repetição
Laços ou loops, servem para executar o mesmo bloco de código repetidamente, desde que uma determinada condição seja atendida. A ideia básica por trás de um loop é automatizar as tarefas repetitivas dentro de um programa para economizar tempo e esforço.

## FOR

Percorre um bloco de código até que o contador atinja um número especificado.

O `for` repete um bloco de código desde que uma determinada condição seja atendida. Normalmente é usado para executar um bloco de código por um determinado número de vezes.

```php
for (inicialização; condição; incremento){  
    // Código a ser executado  
}
```
Os parâmetros do `for` têm os seguintes significados:

- `inicialização`— é usado para inicializar as variáveis ​​do contador e avaliado uma vez incondicionalmente antes da primeira execução do corpo do loop.
- `condição`— no início de cada iteração, a condição é avaliada. Se for avaliado como `true`, o loop continua e as instruções aninhadas são executadas. Se for avaliado como `false`, a execução do loop termina.
- `incremento`— atualiza o contador de loop com um novo valor. É avaliado ao final de cada iteração.

Exemplo:

```php
<?php

for($i = 1; $i <= 10; $i++){
	echo "<h1>titulo nº:$i</h1>";
}

?>
```

O laço repete 10 vezes imprimindo 10 títulos.

## WHILE

A  instrução `while` percorrerá um bloco de código enquanto a condição especificada no `while` for avaliada como verdadeira.
```php
while (condição){  
    // Código a ser executado  
}
```

Exemplo:

```php
<?php 
	$i = 20;
	while($i <= 100){
		$i++; 
		echo "Imprimindo nº$i <br>";
	} 
?>
```

## DO-WHILE

O `do-while` é uma variante do loop while, que avalia a condição no final de cada iteração do loop. Com um `do-while`, o bloco de código é executado uma vez e, em seguida, a condição é avaliada; se a condição for verdadeira, a instrução é repetida enquanto a condição especificada avaliada for verdadeira.

```php
do {  
    // Código a ser executado  
}  
while (condição);
```


```php
<?php

	$x = 1;
	do {  
		$x++;
			echo "Nº $i";
	}while ($x < 10);
?>
```

## FOREACH

O ```foreach``` é uma estrutura de repetição usada para percorrer arrays. veja a sintaxe do ```foreach``` com o exemplo abaixo.

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

Ao percorrer o array `$filhos`, cada `$filho` será um item de dentro do array, nesse caso, um nome. Mas e se fosse um array multidimensional onde há subarrays no array principal? É simples, basta tratar a variável depois do `as` como se fosse um array comum. Veja o exemplo:

```php

<?php

    $familia = [
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

  

    foreach ($familia as $membro) {

        echo $membro["nome"];

    }

?>
```

O laço foreach em questão está imprimindo o nome de cada membro do array principal.



