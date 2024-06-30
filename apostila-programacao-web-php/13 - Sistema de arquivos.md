# Sistema de arquivos

Imagine que você tem dois arquivos: `index.php` e `config.php`. No arquivo `config.php`, você define todas as constantes do sistema. Quando precisa acessar essas constantes no arquivo `index.php`, você deve incluir o `config.php` usando `require_once` ou `include_once`.

 Arquivo `config.php`

```php
<?php 
	define("USUARIO", "root");
?>
```

Arquivo `index.php`

```php
<?php 
echo USUARIO; // Isso causará um erro, pois a constante não está definida aqui ?>
```

Se tentarmos acessar a constante `USUARIO` diretamente no `index.php`, o PHP retornará um erro, pois a constante não está definida nesse arquivo. Para resolver isso, precisamos incluir o `config.php` no `index.php`.

## Incluir arquivos em outros

No PHP temos algumas funções que importam arquivos para dentro de outro, no nosso caso, usamos `require_once` ou `include_once` para incluir o arquivo `config.php`:


```php
<?php 	
	require_once "config.php"; // ou include_once "config.php"; 	
	echo USUARIO; 
?>
```

Agora, o arquivo `config.php` é incluído no `index.php`, e a constante `USUARIO` pode ser acessada.

## Diferença entre `require_once` e `include_once`

- **`require_once`**: Para a execução do script se o arquivo não for encontrado.
- **`include_once`**: Continua a execução do script mesmo que o arquivo não seja encontrado.

## Atenção aos Caminhos dos Arquivos

Quando trabalha com PHP, é importante informar corretamente os caminhos dos arquivos que você está incluindo, especialmente em projetos com várias pastas e subpastas.

### Exemplo de Inclusão em Diretórios Diferentes

Se `index.php` está na raiz do projeto e `config.php` está na pasta `config`:


```php
<?php 
	require_once "config/config.php"; 
?>
```


Se você precisar "voltar" pastas para incluir um arquivo de outro diretório:


```php
<?php
	require_once "../config.php"; 
?>
```

O `../` é usado para voltar uma pasta no sistema de arquivos.