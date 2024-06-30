# Sintaxe

Para criar um script PHP, basta abrir e fechar as tags PHP ```<?php``` e ```?>```. Dentro dessas tags, você pode escrever o código PHP.
```php

<?php
    echo "Olá, Mundo!";
?>

```

Todavia, como escrevi anteriormente, o PHP é uma linguagem de script embutida no HTML. Portanto, você pode escrever o código PHP dentro de uma página HTML.

```php

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

## Comentários

Um comentário é simplesmente um texto ignorado pelo mecanismo PHP. O objetivo dos comentários é tornar o código mais legível. Isso pode ajudar outro desenvolvedor (ou você no futuro, ao editar o código-fonte) a entender o que você estava tentando fazer com o PHP.

PHP oferece suporte a comentários de linha única e também de várias linhas. Para escrever um comentário de linha única, inicie a linha com duas barras ( ``//``) ou um símbolo de hash ( ``#``). Por exemplo

```php
<?php

// esse código imprime um texto
echo "olá mundo";
?>
```

No entanto, para escrever comentários multilinhas, comece o comentário com uma barra seguida de um asterisco ( `/*`) e termine o comentário com um asterisco seguido de uma barra ( `*/`), assim:

```php
<?php

/* 
esse código imprime um texto e
tem muitas linhas de comentários
*/
echo "olá mundo";
?>
```


## Instrução ECHO

A instrução ``echo`` como é mostrado acima em alguns exemplos, serve para imprimir/exibir textos no navegador, tanto texto simples como **HTML**.
```php
// exibindo texto normal
echo "oi pessoal";


// exibindo html
echo "<h1>olá pessoal<h1>";
```

O navegador interpretará o conteúdo e mostrará na tela.
