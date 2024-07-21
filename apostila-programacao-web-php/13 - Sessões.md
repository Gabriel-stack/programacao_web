# Sessões

Sessões no PHP permitem armazenar dados de usuário entre diferentes páginas de um site. Elas são úteis para manter informações persistentes, como dados de login ou preferências do usuário e tem seus dados guardados na variável global `$_SESSION`.

## Variável global `$_SESSION`

A variável global ```$_SESSION``` é usada para armazenar informações do usuário durante a sessão, isto é, enquanto o usuário estiver navegando no site. Para usar a variável global ```$_SESSION```, é necessário iniciar a sessão com a função ```session_start()```. Você pode armazenar todos os dados da sua sessão como pares de valores-chave na `$_SESSION[]`matriz superglobal. Os dados armazenados podem ser acessados ​​durante a vida de uma sessão. Exemplo:


```php

<?php

    session_start();

    $_SESSION["nome"] = "Fulano";

?>

```

No exemplo acima, estamos armazenando o nome do usuário na variável global ```$_SESSION```. Agora o valor da variável ```$_SESSION["nome"]``` pode ser acessado em qualquer parte do site enquanto o usuário estiver navegando. Exemplo de uso:


```php

session_start();

<h2>Olá, <?= $_SESSION["nome"]; ?>!</h2>

```

No código acima, o nome do usuário vai ser impresso na tela.

## Funções de sessão

### session_start()

Inicia a sessão. Essa função deve ser chamada antes de acessar ou definir qualquer variável de sessão.
```php
session_start();
```
### session_destroy()

  ```php
session_destroy();
```

Encerra a sessão. Essa função é usada para encerrar a sessão do usuário.
### session_unset();

```php
session_unset();
```  

Remove todas as variáveis de sessão. Essa função é usada para remover todas as variáveis de sessão.
### session_status();

```php
session_status();
```  

Retorna o valor do estado atual da sessão.

## Constantes de Estado da Sessão

**`PHP_SESSION_DISABLED`**
	- **Valor:** `0`
	- **Descrição:** Indica que as sessões estão desabilitadas.
**`PHP_SESSION_NONE`**
    - **Valor:** `1`
    - **Descrição:** Indica que as sessões estão habilitadas, mas nenhuma sessão existe.
**`PHP_SESSION_ACTIVE`**
    - **Valor:** `2`
    - **Descrição:** Indica que uma sessão está ativa.

> [!NOTE] Importante
> É importante sempre verificar se a sessão está iniciada para não tentar iniciar ela já estando em uso, veja abaixo um exemplo de função que verifica se a sessão está ativa e se não estiver, inicia.

```php
<?php

function iniciaSessao(){
	if(session_status() == PHP_SESSION_DISABLED){
		session_start();
	}
}

iniciaSessao();
```
