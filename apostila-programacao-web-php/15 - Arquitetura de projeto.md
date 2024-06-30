# Arquitetura de Pastas em um Projeto PHP

Organizar as pastas e arquivos de um projeto PHP de forma clara é fundamental para manter o código limpo e fácil de manter. No nosso contexto, a estrutura a seguir é recomendada para manter os arquivos separados por função.

![[arquitetura.png]](imgs/arquitetura.png)

## Descrição das Pastas

### Config

- **Função:** Armazena arquivos de configuração essenciais para o projeto.
- **Conteúdo Típico:** Arquivos com constantes, funções gerais, manipulação de sessões, e scripts de inicialização.
- **Exemplos de Arquivos:** `config.php`, `constants.php`, `init.php`

### Database

- **Função:** Gerencia a conexão e a interação com o banco de dados.
- **Conteúdo Típico:** Arquivos para configurar a conexão com o banco de dados e scripts para manipulação de dados específicos de cada tabela.
- **Exemplos de Arquivos:** `conexao.php`, `usuario.php`, `produto.php`

### Forms

- **Função:** Processa e valida dados de formulários.
- **Conteúdo Típico:** Arquivos separados para cada ação de formulário, como cadastro, login, e atualização de perfil.
- **Exemplos de Arquivos:** `form_criar_usuario.php`, `form_login.php`, `form_registro.php`

### Pages

- **Função:** Contém as páginas principais do site.
- **Conteúdo Típico:** Arquivos PHP que geram as páginas da aplicação.
- **Exemplos de Arquivos:** `page_inicio.php`, `page_sobre.php`, `page_contato.php`

##### Template

- **Função:** Armazena partes comuns das páginas, como cabeçalhos, rodapés e menus.
- **Conteúdo Típico:** Arquivos que são incluídos em várias páginas para manter a consistência do layout.
- **Exemplos de Arquivos:** `header.php`, `footer.php`, `navbar.php`

### Raiz do Projeto

- **Função:** Contém os arquivos acessados diretamente pelo usuário.
- **Conteúdo Típico:** Arquivos principais da aplicação, como a página inicial e a página de login.
- **Exemplos de Arquivos:** `index.php`, `login.php`, `lista_usuarios.php`, etc.