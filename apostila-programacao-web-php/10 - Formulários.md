# Formulários

Essa parte é muito importante no desenvolvimento de aplicações web. Os formulários são usados para coletar informações do usuário. No PHP, os formulários são enviados para o servidor e processados. Para criar um formulário, usamos a tag ```<form>``` do HTML. Exemplo:

```html

<form action="" method="" enctype="">

    <label for="nome">Nome:</label>

    <input type="text" name="nome" id="nome">

</form>

```

O formulário possui três atributos importantes:

- **action**: Para onde vai ser enviado o formulário. Se o valor for vazio, o formulário vai ser enviado para a mesma página (mesmo arquivo PHP). No nosso caso, esse formulários vai estar em algum arquivo PHP da pasta ``pages`` e enviaremos para um arquivo de validação na pasta ``forms``. Fazendo assim, a separação de responsabilidades por arquivo.

- **method**: Como os dados do formulário vão ser enviados. Pode ser ```GET``` ou ```POST```. O ```GET``` envia os dados do formulário pela URL, enquanto o ```POST``` envia os dados do formulário de forma oculta.

- **enctype**: Tipo de codificação dos dados do formulário. Pode ser ```application/x-www-form-urlencoded``` ou ```multipart/form-data```. O primeiro é usado para formulários simples, enquanto o segundo é usado para formulários que enviam arquivos. Não é necessário usar esse atributo se o formulário não envia arquivos. Vejamos um exemplo simples de um formulário de login:

  

```html

<form action="forms/login.php" method="post">

    <label for="email">E-mail:</label>

    <input type="email" name="email" id="email">

    <label for="senha">Senha:</label>

    <input type="password" name="senha" id="senha">

    <button type="submit">Entrar</button>

</form>

```

No exemplo acima, o formulário vai ser enviado para o arquivo ```login.php``` da pasta ```forms``` e os dados do formulário vão ser enviados de forma oculta pois usamos o método ```POST```.

## Métodos de envio de informações ao servidor

Um navegador da web se comunica com o servidor normalmente usando um dos dois métodos HTTP (Hypertext Transfer Protocol) – GET e POST. Ambos os métodos passam as informações de maneira diferente e apresentam vantagens e desvantagens diferentes, conforme descrito a seguir.
### O método GET

No método GET, os dados são enviados como parâmetros na URL, separados por "&". Exemplo:

`http://www.example.com/action.php?nome=joão&idade=24`

- **Parâmetros GET:** `nome=joão` e `idade=24`
- **Valores:** `joão` e `24`

Você pode enviar múltiplos parâmetros usando "&". Apenas dados de texto simples podem ser enviados.

> [!NOTE] **Vantagens:** 
> - Parâmetros na URL permitem marcar páginas com valores específicos.

> [!NOTE]  **Desvantagens:**
> - Não é seguro para informações confidenciais (ex.: senhas) porque os dados são visíveis na URL.
> - O comprimento da URL é limitado, restringindo a quantidade de dados enviados.

PHP usa a variável superglobal `$_GET` para acessar dados enviados pela URL ou por um formulário HTML com `method="get"`.

### O método POST

No método POST, os dados são enviados ao servidor em uma comunicação separada e não são visíveis na URL.

> [!NOTE] **Vantagens:**
> - Mais seguro que GET, pois os dados não aparecem na URL.
> - Pode transmitir grandes quantidades de dados e suportar tanto texto quanto arquivos.

> [!NOTE] **Desvantagens:**
> - Não é possível marcar a página com dados específicos na URL.

Da mesma forma `$_GET`, o PHP fornece outra variável superglobal `$_POST`para acessar todas as informações enviadas via post ou enviadas através de um formulário HTML usando o `method="post"`.

## Variáveis globais: ```$_GET, $_POST e $_REQUEST```

Variáveis globais são variáveis que podem ser acessadas de qualquer parte do script PHP. Temos várias variáveis globais, mas as mais usadas são ```$_GET```, ```$_POST```, ```$_SESSION``` e ```$_REQUEST```.
### $\__GET

  
O ```$_GET``` é uma variável global usada para acessar os dados do formulário que foram enviados pelo método ```GET```. Para acessar os dados do formulário, usamos o nome do campo do formulário. Exemplo:

```php
URL: http://localhost/index.php?nome=Fulano&idade=20
<?php
    echo $_GET["nome"]; // Fulano
    echo $_GET["idade"]; // 20
?>
```

No caso, estamos usando ``echo`` para imprimir o valor do campo do formulário mas para acessar o valor do campo do formulário, basta usar o nome do campo do formulário entre colchetes da variável global ```$_GET```. Veja um exemplo de outro uso, agora para comparar os valores enviados:


```php
<?php
    if ($_GET["idade"] >= 18) {
        echo "Maior de idade";
    } else {
        echo "Menor de idade";
    }
?>
```
### $\_POST

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

## $\_REQUEST

A variável superglobal `$_REQUEST` em PHP é usada para coletar dados de formulários enviados com os métodos GET, POST, e também dados gerais da requisição que está sendo feita pelo usuário ao navegador.

> [!NOTE] Detalhes
> - **Acesso a Dados**: `$_REQUEST` permite acessar dados enviados via GET (`$_GET`), POST (`$_POST`), e cookies (`$_COOKIE`) de forma unificada.
> - **Facilidade de Uso**: Simplifica o código ao permitir acessar todos os tipos de dados de entrada através de uma única variável


## Variável $\_SERVER

A variável superglobal `$_SERVER` em PHP contém informações sobre o servidor e o ambiente de execução, além de detalhes sobre a solicitação do usuário.

### Uso em Formulários e Requisições

`$_SERVER` é útil para obter informações sobre a requisição e o ambiente, como o método de envio de um formulário, a URL de referência, etc.

### Exemplos Comuns

1. **Verificar o Método de Envio do Formulário:**

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST') { 
// Processar dados enviados via POST
}
```


2. **Obter a URL de Referência:**
```php
$url = $_SERVER['HTTP_REFERER']; 
echo "Página de referência: $referer";
```

``$_GET``