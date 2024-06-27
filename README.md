Sistema de Gestão de Cursos
Este é um sistema simples de gestão de cursos desenvolvido com Flask e SQLAlchemy, usando PostgreSQL como banco de dados.

Funcionalidades
Gerenciamento de Clientes
Gerenciamento de Cursos
Gerenciamento de Vendedores
Gerenciamento de Vendas
Estrutura do Projeto
plaintext
Copiar código
sistema_cursos/
├── templates/
│   ├── base.html
│   ├── cliente_form.html
│   ├── curso_form.html
│   ├── vendedor_form.html
│   ├── venda_form.html
│   └── index.html
├── app.py
├── requirements.txt
└── README.md
Configuração do Ambiente
Clone o repositório:

bash
Copiar código
git clone https://github.com/seu-usuario/sistema_cursos.git
cd sistema_cursos
Crie e ative um ambiente virtual:

bash
Copiar código
python3 -m venv venv
source venv/bin/activate  # No Windows use `venv\Scripts\activate`
Instale as dependências:

bash
Copiar código
pip install -r requirements.txt
Configuração do Banco de Dados:

Certifique-se de ter o PostgreSQL instalado e em execução.
Crie um banco de dados chamado postgres.
Atualize a string de conexão no arquivo app.py com as credenciais corretas do banco de dados.
Estrutura do Banco de Dados
O banco de dados é composto pelos seguintes esquemas e tabelas:

sql
Copiar código
CREATE SCHEMA sistema_cursos;

CREATE TABLE sistema_cursos.clientes (
    cliente_id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    telefone VARCHAR(15)
);

CREATE TABLE sistema_cursos.cursos (
    curso_id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    descricao TEXT,
    preco NUMERIC(10, 2) NOT NULL
);

CREATE TABLE sistema_cursos.vendedores (
    vendedor_id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);

CREATE TABLE sistema_cursos.vendas (
    venda_id SERIAL PRIMARY KEY,
    cliente_id INT NOT NULL REFERENCES sistema_cursos.clientes(cliente_id),
    curso_id INT NOT NULL REFERENCES sistema_cursos.cursos(curso_id),
    vendedor_id INT NOT NULL REFERENCES sistema_cursos.vendedores(vendedor_id),
    data_venda DATE NOT NULL
);
Executando o Projeto
Inicialize o banco de dados e crie as tabelas:

bash
Copiar código
python app.py
Acesse a aplicação:

Abra o navegador e acesse http://localhost:5000.

Estrutura de Arquivos
app.py: Arquivo principal do aplicativo Flask.
templates/: Diretório que contém os arquivos HTML dos templates.
Arquivos HTML (Templates)
base.html: Template base que é estendido pelos outros templates.
cliente_form.html: Formulário para adicionar um novo cliente.
curso_form.html: Formulário para adicionar um novo curso.
vendedor_form.html: Formulário para adicionar um novo vendedor.
venda_form.html: Formulário para adicionar uma nova venda.
index.html: Página inicial da aplicação.
Contribuição
Sinta-se à vontade para contribuir com o projeto. Para isso:

Fork o projeto
Crie uma branch para sua feature (git checkout -b feature/fooBar)
Commit suas alterações (git commit -am 'Add some fooBar')
Push para a branch (git push origin feature/fooBar)
Crie um novo Pull Request
Licença
Este projeto está licenciado sob a MIT License.
