# PHP + Banco de Dados

Integrar PHP com um banco de dados é essencial para criar sistemas web. Bancos de dados permitem armazenar, gerenciar e recuperar dados de maneira mais eficiente do que outras formas. Funcionalidades como sistemas de login, gerenciamento de conteúdo, e-commerce, entre outras, são sempre necessário o uso de um banco de dados.

No nosso caso, iremos usar o Banco de Dados MySQL para integrar em nossos códigos.

## PDO

Para integrarmos o banco de dados a nosso código, precisamos usar uma extensão do PHP chamada PDO (PHP Data Objects) que define uma interface leve e consistente para acessar bases de dados. O PDO tem como caracteristicas:

- **Suporte a Diversos Bancos de Dados:** PDO suporta vários sistemas de banco de dados como MySQL, PostgreSQL, SQLite, entre outros.
- **Segurança:** PDO oferece suporte a prepared statements, que protegem contra SQL Injection.
- **Flexibilidade:** Permite trocar de banco de dados com mínimas alterações no código.

## Conexão com o banco

```php
<?php
try {
    $dsn = 'mysql:host=localhost;dbname=meu_banco';
    $username = 'root';
    $password = '';
    $options = array(
        PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION
    );

    $pdo = new PDO($dsn, $username, $password, $options);
    echo "Conexão estabelecida com sucesso!";
} catch (PDOException $e) {
    echo "Erro ao conectar ao banco de dados: " . $e->getMessage();
}
?>

```

### Explicação do Código

 **Bloco try-catch**
 ```php
try {     
   // Código que pode gerar uma exceção    
   } catch (PDOException $e) {     
   // Código que será executado em caso de uma exceção 
   }
```

- **try:** Contém o código que tenta estabelecer a conexão com o banco de dados.
- **catch (PDOException $e):** Captura qualquer exceção (erro) gerada pela tentativa de conexão. `PDOException` é uma classe específica para tratar erros relacionados ao PDO.

**Definição da DSN (Data Source Name)**

```php
    $dsn = 'mysql:host=localhost;dbname=meu_banco';
```

- **`mysql:`** Indica que estamos usando o banco MySQL.
- **`host=localhost;`** Define o endereço do servidor de banco de dados, que neste caso é `localhost` pois se trata do endereço local do computador.
- **`dbname=meu_banco;`** Define o nome do banco de dados ao qual estamos tentando nos conectar (`meu_banco`).

**Definição de Credenciais**

 ```php
 $username = 'root';    
 $password = ''; 
```

- **`$username`** e **`$password`:** Contêm o nome de usuário e a senha para autenticação no banco de dados. Neste exemplo, o usuário é `root` e a senha está vazia (`''`).

**Opções do PDO**

 ```php
 $options = [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION];
```

- **`PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION`:** Define o modo de erro do PDO para lançar exceções. Isso facilita o tratamento de erros, pois qualquer problema na conexão ou consulta será tratado como uma exceção.

 **Instanciando o Objeto PDO**

 ```php
$pdo = new PDO($dsn, $username, $password, $options);
```

 - **`new PDO($dsn, $username, $password, $options)`:** Cria uma nova instância da classe PDO usando a DSN, credenciais e opções fornecidas. Se a conexão for bem-sucedida, a variável `$pdo` conterá o objeto PDO, que pode ser usado para executar consultas no banco de dados.
 
**Tratamento de Exceções**

```php
catch (PDOException $e) {    
	echo "Erro ao conectar ao banco de dados: " . $e->getMessage(); 
}
```

- Se ocorrer um erro durante a tentativa de conexão, a exceção será capturada e a mensagem de erro será exibida. **`$e->getMessage()`** retorna uma descrição detalhada do erro.

## Revisão de Banco de Dados

Antes de continuar, é importante revisar alguns conceitos vistos antes, que são as consultas ao banco. As consultas SQL permitem realizar diversas operações em um banco de dados, desde a criação e modificação de tabelas até a inserção, atualização, exclusão e consulta de dados. 

### Tipos de consultas

**Consultas DDL (Data Definition Language)**

As consultas DDL são usadas para definir e gerenciar a estrutura dos objetos do banco de dados, como tabelas, índices e esquemas.

**Consultas DML (Data Manipulation Language)**

As consultas DML são usadas para manipular os dados dentro do banco de dados. Isso inclui inserir, atualizar, deletar e selecionar dados.

**Consultas DCL (Data Control Language)

As consultas DCL são usadas para controlar o acesso aos dados no banco de dados.


**Consultas TCL (Transaction Control Language)**

As consultas TCL são usadas para gerenciar transações no banco de dados, garantindo que as operações sejam executadas de maneira segura e consistente.


**No nosso caso, vamos focar nas consultas de manipulação de dados.**


> [!NOTE] Observação
> As consultas requer que o banco esteja criado. Nas aulas, criaremos o banco usando o painel 'phpMyAdmin' do Aplicativo 'Xampp'.

### Consulta INSERT (Inserir Dados)

A instrução `INSERT` é usada para adicionar novos registros a uma tabela do banco.

**Estrutura Básica:**

```sql
INSERT INTO nome_da_tabela (coluna1, coluna2, coluna3, ...)
VALUES (valor1, valor2, valor3, ...);
```

**Exemplo:**

```sql
INSERT INTO usuarios (nome, email) VALUES ('Gabriel', 'gabriel@gmail.com');
```

- **`INSERT INTO usuarios`**: Especifica a tabela `usuarios` onde os dados serão inseridos.

- **`(nome, email)`**: Lista as colunas que receberão os valores. As colunas especificam os campos da tabela onde os dados serão armazenados. Se no caso, você queira preencher somete o nome, basta passar somente a coluna nome e seu valor.

- **`VALUES ('Gabriel', 'gabriel@gmail.com')`**: Define os valores que serão inseridos nas colunas correspondentes. Cada valor corresponde a uma coluna listada.

>[!NOTE] Observação
> Quase nunca atribuimos valor à coluna `id` do banco pois ela é preenchida automaticamente (mediante configuração, lógico).


### Consulta SELECT (Selecionar Dados)

A instrução `SELECT` é usada para consultar dados de uma ou mais tabelas.

**Estrutura Básica:**

```sql
SELECT coluna1, coluna2, coluna3, ... *
FROM nome_da_tabela
WHERE condição
ORDER BY coluna [ASC|DESC]
LIMIT número;
```

**Exemplos:**

```sql
SELECT nome, email FROM usuarios WHERE id = 1;

SELECT * FROM usuarios WHERE id = 1; // seleciona tudo do usuário com id 1

SELECT nome, email FROM usuarios; // seleciona nome e email de todos os usuarios

SELECT * FROM usuarios ORDER BY nome DESC // seleciona usuarios por ordem decrescente
```

- **`SELECT nome, email`**: Indica as colunas `nome` e `email` que serão retornadas. As colunas especificam os campos da tabela cujos dados queremos visualizar. Você pode usar `*` para trazer todos os dados do registro da tabela caso não queira especificar as colunas.

- **`FROM usuarios`**: Especifica a tabela `usuarios` de onde os dados serão selecionados.

- **`WHERE id = 1`**: Filtra os registros para retornar apenas aqueles com `id` igual a 1.
- ``**ORDER BY**``: Indica como vai ser ordenados os registros selecionados.
### Consulta UPDATE (Atualizar Dados)

A instrução `UPDATE` é usada para modificar dados existentes em uma tabela.

**Estrutura Básica**:

```sql
UPDATE nome_da_tabela
SET coluna1 = valor1, coluna2 = valor2, ...
WHERE condição;
```

**Exemplos:**

```sql
UPDATE usuarios SET email = 'novoemail@gamail.com' WHERE id = 1;
UPDATE usuarios SET email = 'novoemail@gmail.com', nome = "Gabriel Novo" WHERE id = 1;
```

- **`UPDATE usuarios`**: Especifica a tabela `usuarios` onde os dados serão atualizados.
- **`SET email = 'novoemail@gmail.com'`**: Define a nova valor para a coluna `email`. As colunas especificam quais campos serão atualizados e os valores correspondem aos novos dados que serão armazenados.
- **`WHERE id = 1`**: Filtra os registros para atualizar apenas aquele com `id` igual a 1.

>[!NOTE] **ATENÇÃO**
>Caso não use a cláusula `WHERE` vai alterar todos os registros do banco para os valores indicados.

### Consulta DELETE (Excluir Dados)

A instrução `DELETE` é usada para remover registros de uma tabela.

**Estrutura Básica:**

```sql
DELETE FROM nome_da_tabela WHERE condição;
```

**Exemplo**:

```sql
DELETE FROM usuarios WHERE id = 1;
```

- **`DELETE FROM usuarios`**: Especifica a tabela `usuarios` de onde os dados serão excluídos.
- **`WHERE id = 1`**: Filtra os registros para excluir apenas aquele com `id` igual a 1.


>[!NOTE] **ATENÇÃO**
>Caso não use a cláusula `WHERE` vai apagar todos os registros do banco.

### **Cláusulas:**

**Cláusula WHERE:**

A cláusula `WHERE` é usada para filtrar registros com base em condições específicas.

**Exemplos:**

```sql
SELECT * FROM usuarios WHERE nome = 'Gabriel';

// condição composta

SELECT * FROM usuarios WHERE nome = 'Gabriel' AND email = 'gabriel@gmail.com';

```

**Cláusula ORDER BY:**

A cláusula `ORDER BY` é usada para ordenar os resultados.

**Exemplos:**

```sql
SELECT * FROM usuarios ORDER BY nome ASC; // ordem ASCENDENTE (crescente)

SELECT * FROM usuarios ORDER BY nome DESC; // ordem DESCENDENTE (decrescente)

```

**Cláusula LIMIT:**

A cláusula `LIMIT` é usada para restringir o número de registros retornados na consulta.

**Exemplo:**

```sql
SELECT * FROM usuarios LIMIT 10;
```

## Resgatar dados usando PDO QUERY

`query` é um método da classe PDO usado para executar instruções SQL . Ele é ideal para consultas que não exigem a preparação prévia de instruções ou a vinculação de valores para prevenir ataques ao banco.

A primeira coisa que precisamos fazer para executar o método é ter um **objeto** `PDO` criado, como nos exemplos acima.

Leve em consideração que a conexão abaixo deu certo:

```php
<?php
	$dsn = 'mysql:host=localhost;dbname=meu_banco'; 
	$username = 'root'; 
	$password = ''; 
	$options = [
			PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION
	];
	
	$pdo = new PDO($dsn, $username, $password, $options);
```

Agora, por meio da variável `$pdo` podemos usar o método ``query`` .

```php
<?php
//código acima

$consulta = $pdo->query('SELECT * FROM usuarios');
```

### **Iterando Sobre os Resultados com `foreach`**

Ao usar o método `query`, você pode recuperar um registro, o número de linhas retornadas, ou todos os registros.


#### Recuperando Todos os Registros

Para recuperar todos os registros de uma consulta, você pode usar o método `fetchAll` e iterar sobre os resultados com `foreach` ou qualquer outra estrutura de repetição veja mais nessa nota caso não lembre [[8 - Laços de repetição]].

```php
<?php

// Código de conexão já estabelecido acima 
	$consulta = $pdo->query('SELECT * FROM usuarios'); 
	$resultados = $consulta->fetchAll();
	 
	foreach ($resultados as $linha){ 
		echo "Nome: " . $linha['nome'] . " - Email: " . $linha['email'] . "<br>"; 
	}
```

#### Recuperando um Único Registro

Para recuperar um único registro, você pode usar o método `fetch`.

```php
<?php

	$consulta = $pdo->query('SELECT * FROM usuarios WHERE id = 1');
	$registro = $consulta->fetch(PDO::FETCH_ASSOC);
	
	if ($registro) {
	    echo "Nome: " . $registro['nome'] . " - Email: " . $registro['email'] . "<br>";
	} else {
	    echo "Nenhum registro encontrado.";
	}
?>

```

#### Recuperando o Número de Linhas Retornadas

Para recuperar o número de linhas retornadas por uma consulta, você pode usar o método `rowCount`.

```php
<?php
	$consulta = $pdo->query('SELECT * FROM usuarios');
	$numeroLinhas = $consulta->rowCount();
	
	echo "Número de registros: " . $numeroLinhas . "<br>";

```


Embora o método `query` seja bem mais simples de usar e direto, em alguns casos é melhor evitar pois precisamos tratar dados antes de fazer a consulta e evitar invasão no banco de dados. No caso de consultas do tipo `INSERT`, `UPDATE`, e `DELETE` vamos usar outro método.


## Preparar consultas (PDO PREPARE)

Enquanto o método `query` é útil para consultas SQL simples, `prepare` é para consultas que necessitam de parâmetros dinâmicos e proteção contra [ataques de injeção de SQL](https://gitbook.ganeshicmc.com/web/semana-2/14_sql_injection).

**veja como se faz o uso:**

```php
<?php
// Preparar a consulta
$stmt = $pdo->prepare('SELECT * FROM usuarios WHERE id = :id');

?>
```

Os "dois pontos" (`:`) são usados para definir parâmetros nomeados na consulta SQL. Neste caso, `:id` é um parâmetro nomeado que será substituído por um valor real durante a execução da consulta. Esse valor por qual vai ser trocado deve ser tratado antes, como por exemplo, verificar se o `id` é numérico.

Após preparar a consulta, precisamos vincular valores aos parâmetros nomeados. Usamos o método `bindValue` para isso.

```php

<?php
	$id = $_POST['id'];
	
	$stmt = $pdo->prepare('SELECT * FROM usuarios WHERE id = :id');
	$stmt->bindValue(':id', $id, PDO::PARAM_INT);
?>

```

**Explicação:**

- `:id`: O nome do parâmetro na consulta SQL.
- `$id`: O valor dessa variável a ser vinculado ao parâmetro `:id`.
- `PDO::PARAM_INT`: O tipo de dado do parâmetro (neste caso, um inteiro).

Com a consulta preparada e os valores vinculados, podemos executar a instrução SQL usando o método `execute`.

```php

<?php
	$id = $_POST['id'];
	
	$stmt = $pdo->prepare('SELECT * FROM usuarios WHERE id = :id');
	$stmt->bindValue(':id', $id, PDO::PARAM_INT);
	$stmt->execute();
?>

```

Após executar a consulta, podemos recuperar os resultados da mesma forma ([[#Resgatar dados usando PDO QUERY]] ) que fizemos com o método `query`.

**Exemplo completo:**

```php
<?php

	$stmt = $pdo->prepare('SELECT * FROM usuarios WHERE id = :id');
    
    // Vincular o valor ao parâmetro :id
    $stmt->bindValue(':id', 1, PDO::PARAM_INT);
    
    // Executar a consulta
    $stmt->execute();
    
    // Recuperar os resultados
    $resultados = $stmt->fetchAll();
    
    foreach ($resultados como $linha) {
        echo "Nome: " . $linha['nome'] . " - Email: " . $linha['email'] . "<br>";
    }
```

