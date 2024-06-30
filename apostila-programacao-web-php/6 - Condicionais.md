# Estruturas de Controle de Fluxo - IF

Todas as linguagens de programação possuem estruturas de controle de fluxo, que são usadas para controlar o fluxo de execução de um programa.

## IF
A instrução _if_ é usada para executar um bloco de código somente se a condição especificada for avaliada como verdadeira.
```php

<?php
    if (condição) {
        // código a ser executado
    }
?>

```

## IF...ELSE

Você pode aprimorar o processo de tomada de decisão fornecendo uma escolha alternativa adicionando uma instrução _else_ à instrução _if_ . A instrução _if...else_ permite executar um bloco de código se a condição especificada for avaliada como verdadeira e outro bloco de código se for avaliada como falsa.

```php

<?php

    if (condição) {
        // código a ser executado
    } else {

        // código a ser executado  
    }
?>

```

## IF...ELSEIF...IF

A instrução if...elseif..else permite adicionar mais de uma condição para verificação:

```php
if (condição1){  
    // Código a ser executado se a condição1 for verdadeira_  
} elseif (condição2){  
    // Código a ser executado se a condição1 for falsa e a condição2 for verdadeira_  
} else {  
    // Código a ser executado se a condição1 e a condição2 são falsos_  
}
```

## SWITCH

A instrução switch-case é uma alternativa à instrução if-elseif-else, que faz quase a mesma coisa.

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

            // código a ser executado se o valor da variável não for nenhum do cases
            break;
    }
?>

```