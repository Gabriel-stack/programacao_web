# Criar projeto a partir do que foi feito em sala de aula

## Estrutura de pastas
1)  **Configs**
Esta pasta é o coração da configuração do sistema. Aqui ficam arquivos essenciais que definem como o sistema funciona e como ele se conecta às diferentes partes:

	- **config.php:** Define informações e parâmetros que o sistema vai usar globalmente, como URLs, constantes, e outras variáveis que precisam ser acessíveis em qualquer parte do código.

	- **funcoes.php:** Armazena funções úteis que podem ser chamadas em várias partes do sistema. Essas funções servem para não repetirmos código. Toda vez que você precisar, por exemplo, redirecionar o usuário para uma nova página, vai usar algo daqui.

	- **sessao.php:** Este arquivo gerencia sessões, que são como espaços temporários onde guardamos informações enquanto o usuário está navegando (como dados de login). Aqui você encontra funções para iniciar, destruir ou verificar sessões ativas.

	- **init.php:** Este arquivo carrega tudo o que o sistema precisa para funcionar corretamente. Ele importa os outros arquivos de configuração (config, funções e sessões) e garante que tudo esteja pronto para ser usado em qualquer parte do sistema.

2) **Database**
Esta pasta é responsável pela conexão e manipulação dos dados no banco de dados. Todo acesso ao banco de dados passa por aqui.

	- **conexao.php:** Responsável por estabelecer a conexão com o banco de dados. Sem ele, nada vai funcionar quando se trata de buscar ou salvar dados.

	- **Arquivos específicos de tabelas:** Para cada tabela que você tiver no banco de dados (usuários, produtos, etc.), você vai criar um arquivo aqui que lida exclusivamente com ela. Cada um desses arquivos contém funções que fazem o CRUD (Criar, Ler, Atualizar, Excluir) da tabela correspondente.

3) **Forms**
Esta pasta recebe os dados enviados pelos formulários do sistema e faz o processamento necessário. Cada vez que um usuário envia um formulário (de login, de cadastro, etc.), um arquivo aqui vai ser chamado para processar esses dados e tomar uma ação.

4) **Pages**
Aqui ficam os arquivos que o usuário realmente vê na tela. Cada página do sistema (como a página de login, de cadastro, ou a página principal) tem um arquivo aqui que contém o HTML e o código PHP para exibir as informações ao usuário.

5) **Arquivos Raiz**
Estes são os controladores principais. São os arquivos que você acessa diretamente pelo navegador (como login.php, index.php, cadastro.php). Cada um deles vai carregar uma página específica e o sistema todo a partir dos arquivos nas outras pastas. Eles chamam a init.php para garantir que tudo esteja configurado corretamente e você possa usar as funções e variáveis definidas nos outros arquivos.

## Casos de Uso e Dúvidas Comuns
Agora, uma lista de dúvidas comuns que podem surgir ao criar um projeto a partir do que foi feito em sala de aula:

**Caso 1: "Eu quero criar uma nova página para o meu sistema. Como eu faço?"**
1) Crie um arquivo na pasta `pages` com o nome da página que você quer criar (por exemplo, `page_sobre.php`).  Esse arquivo vai conter o conteúdo da página que você quer exibir para o usuário. O código principal aqui será o HTML, mas você pode incluir PHP para exibir informações dinâmicas.
<br>
2) Crie um arquivo raiz para essa página  (na raiz do projeto). Por exemplo, se a página se chama "sobre nós", crie sobre.php. Esse arquivo vai:
	- Importar o init.php para carregar todas as configurações.
	- Incluir o arquivo da página que você criou na pasta `pages`.
<br>
3) Atualize o arquivo config.php se necessário. Caso sua página precise de uma URL específica, você pode adicionar isso lá como uma constante.

**Caso 2: "Eu quero exibir informações do banco de dados nessa nova página. Como eu faço?"**

1) Crie ou edite o arquivo na pasta database. Se estiver lidando com uma nova tabela (por exemplo, produtos), crie um arquivo em database com as funções de CRUD necessárias, como ``getProdutos()``.
<br>
2) Crie o arquivo na pasta ``pages``. Esse arquivo vai apenas exibir as informações na tela (HTML), usando as variáveis que guarda os dados resgatados do banco de dados que vão ser criadas no arquivo raiz.
<br>
3) Crie ou edite o arquivo raiz. Na raiz do projeto, crie um arquivo (por exemplo, produtos.php), que:
	- Importa o ``init.php``.
	- Usa as funções do arquivo ``produtos.php`` na pasta database para buscar os dados necessários (como ``getProdutos()``).
	- Depois de resgatar os dados, inclui o arquivo da página correspondente em pages para exibir as informações no HTML.
<br>

**Caso 3: "Como faço para criar uma nova página que tem formulário no sistema e tratar os dados enviados?"**
1) Crie a página do formulário na pasta ``pages``. O HTML do formulário vai estar na pasta ``pages``, mas a lógica de processamento não vai aqui.
<br>
2) Crie o arquivo de processamento na pasta ``forms``. Esse arquivo recebe os dados do formulário e usa funções do arquivo ``database`` correspondente para salvar as informações no banco de dados.
<br>
3) Crie ou edite o arquivo raiz. Na raiz do projeto, crie ou edite o arquivo que vai exibir o formulário para o usuário (por exemplo, ``cadastro_produto.php``):
	- Esse arquivo vai incluir o arquivo do página que tem o formulário (em ``pages``).
	- Quando o formulário for enviado, ele vai redirecionar para um arquivo da pasta ``forms`` que trata os dados e faz o que precisa ser feito no banco.

**Caso 7: "Como faço para criar um CRUD completo de uma tabela (como usuários) com listagem, edição e exclusão?"**

Nesse caso, coloquei como fazer um CRUD completo (Create, Read, Update, Delete) para a tabela de ``usuários`` (mas vale pra qualquer outra que vc quer). O processo envolve a criação de arquivos para listagem, edição e exclusão de registros, além do arquivo de tratamento de formulários e a manipulação dos dados no banco de dados.

1)  **Criar as funções no arquivo ``database/usuario.php``**
Primeiro, você precisa criar as funções que vão manipular os dados da tabela usuarios no banco. Essas funções serão usadas nos arquivos raiz.
	- Função para listar usuários;
	- Função para buscar um usuário específico;
	- Função para inserir um novo usuário;
	- Função para atualizar um usuário;
	- Função para excluir um usuário.
<br>
2) **Criar a página de listagem na pasta ``pages``**
Agora que temos as funções do banco, vamos criar a página de listagem de usuários.
	- ``Arquivo pages/page_lista_usuarios.php``
	Esse arquivo vai exibir a lista de usuários, com botões de "Editar" e "Excluir" para cada registro.
	- A lógica de exibição do HTML estará aqui, mas sem buscar os dados diretamente (os dados serão buscados no arquivo raiz referente).
<br>
3) **Criar o arquivo raiz para listagem**
No arquivo raiz da listagem, você vai buscar os dados e incluir a página de exibição.
	- ``Arquivo lista_usuarios.php:``
	Você precisa fazer 3 coisas no mínimo:
		- Importar o ``init.php`` para carregar as configurações;
		- Buscar os dados dos usuários usando as funções do arquivo ``database/usuario.php`` (como ``getUsuarios()``) e guardar em uma variável (como ``$usuarios``);
		- Incluir o arquivo da página de listagem de usuários (``pages/page_lista_usuarios.php``).
<br>
4) **Criar a página de edição na pasta ``pages``**
	- ``Arquivo pages/page_editar_usuario.php``
	Essa página vai exibir um formulário com os dados do usuário selecionado para edição.
	- Os dados do usuário serão passados pelo arquivo raiz.
<br>
5) **Criar o arquivo raiz para edição**
O arquivo raiz para editar um usuário vai buscar os dados do banco, exibir o formulário com esses dados e redirecionar para o processamento do formulário.
	- ``Arquivo editar_usuario.php``
		- Importar o ``init.php`` para carregar as configurações;
		- Buscar os dados do usuário selecionado usando as funções do arquivo ``database/usuario.php`` (como ``getUsuario()``) e guardar em uma variável (como ``$usuario``);
		- Incluir o arquivo da página de edição de usuário (``pages/page_editar_usuario.php``).
<br>
6)  **Criar o arquivo de processamento de edição**
Na pasta ``forms``, você vai criar o arquivo para processar o formulário de edição e atualizar os dados no banco.
	- Arquivo ``forms/form_editar_usuario.php:``
	Esse arquivo recebe os dados do formulário e chama a função updateUsuario() para atualizar o banco de dados.
<br>

7) **Criar o arquivo de processamento de exclusão**
Na pasta ``forms``, você vai criar o arquivo para processar a exclusão de um usuário.
	- Arquivo ``forms/form_excluir_usuario.php:``
	Este arquivo recebe o ID do usuário a ser excluído e chama a função deleteUsuario() para remover o registro do banco de dados.

## Conclusão

**Resumo do processo:**
1) Crie os arquivos de manipulação do banco de dados para cada tabela do seu sistema.
<br>
2) Crie os arquivos de formulários na pasta ``forms``. Cada ação que o usuário vai fazer por meio de um formulário (como cadastro, edição, exclusão) vai ter um arquivo aqui referente a qualquer tabela do banco.
<br>
3) Crie os arquivos de exibição de páginas na pasta ``pages``.
<br>
4) Crie os arquivos raiz para cada página que o usuário vai acessar. Cada arquivo raiz vai importar uma página da pasta ``pages``.
