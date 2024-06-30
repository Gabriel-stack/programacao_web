# Variáveis

Variáveis em todas as linguagens de programação são usadas para armazenar valores. No PHP, as variáveis são declaradas com o símbolo de cifrão ```$```. Diferentemente de outras linguagens, o PHP é uma linguagem que não é necessário declarar o tipo da variável (int, string, float, etc). O PHP converte automaticamente a variável para o tipo de dados correto, dependendo do seu valor.

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

> [!NOTE] Observação
> - Depois de declarar uma variável ela pode ser reutilizada em todo o código.
> - O operador de atribuição ( `=`) usado para atribuir valor a uma variável.

## Regra de nomenclatura de variáveis

- Deve começar com ```$```;
- Não pode começar com números;
- Não pode conter espaços;
- Não pode conter caracteres especiais, exceto o ```_```;


## Constantes

Uma constante é um nome ou identificador para um valor fixo. Constantes são como variáveis, exceto que, uma vez definidas, não podem ser indefinidas ou alteradas.

Constantes são muito úteis para armazenar dados que não mudam enquanto o script está em execução. Exemplos como nome de usuário e senha do banco de dados, URL do site, nome da empresa, etc.

As constantes são definidas usando a função do PHP `define()`, que aceita dois argumentos: o nome da constante e seu valor. Uma vez definido o valor da constante pode ser acessado a qualquer momento apenas referindo-se ao seu nome.  Exemplo:

```php
<?php
	define("URL", "https://www.auladeprogramacaoweb.com");
	define("URL_LOGIN", "https://www.auladeprogramacaoweb.com/login");
	define("URL_LOGOUT", "https://www.auladeprogramacaoweb.com/logout");
    define("BANCO_SENHA", "123456");
?>
 

echo 'Url do site: ' . SITE_URL;
?>
```


> [!NOTE] Observação
> Para usar a constante não precisa usar cifrão.