# Funções comuns de uso

Como já foi falado no arquivo [[9 - Funções]]. funções são um conjunto de instruções que são usadas para executar uma tarefa específica que pode ser reutilizada em várias partes do script.

No PHP, temos várias funções que são muito utilizadas no desenvolvimento de aplicações web. Algumas são caracterizadas como funções que sempre estão presentes em um projeto.

---
## Isset

A função ```isset()``` é usada para verificar se uma variável foi definida. Ela retorna ```true``` se a variável foi definida e ```false``` se a variável não foi definida.  Resumindo, verifica se a variável existe. Exemplo de uso com a variável global ```$_GET```:

Alguém acessou a URL: ``http://localhost/index.php?nome=Fulano``

no arquivo index.php queremos saber se a variável nome foi definida como parâmetro ``$_GET``:

  

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

  

## empty

A função ```empty()``` é usada para verificar se uma variável está vazia. Ela retorna ```true``` se a variável estiver vazia e ```false``` se a variável não estiver vazia. Veja que diferente do ```isset()```, o ```empty()``` não verifica se a variável foi definida, mas sim se ela está vazia, contém algum valor. Exemplo:

  

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

## header

A função ```header()``` serve para, na maioria dos casos, redirecionar o usuário para outra página. Por exemplo, quando o usuário faz login, o sistema vai validar os dados do usuário e, se os dados estiverem corretos, o sistema vai redirecionar o usuário para a página inicial.  Atrelado a ela, sempre é bom usar o ```exit()``` ou ```die()``` para parar a execução do script. Exemplo de uso:


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

## unset

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