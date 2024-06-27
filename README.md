# Sistema de Gestão de Cursos

Este é um sistema simples de gestão de cursos desenvolvido com Flask e SQLAlchemy, usando PostgreSQL como banco de dados.

## Funcionalidades

- Gerenciamento de Clientes
- Gerenciamento de Cursos
- Gerenciamento de Vendedores
- Gerenciamento de Vendas

## Estrutura do Projeto

```
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
```

## Configuração do Ambiente

Clone o repositório:

```bash
git clone https://github.com/seu-usuario/sistema_cursos.git
cd sistema_cursos
```

Crie e ative um ambiente virtual:

```bash
python3 -m venv venv
source venv/bin/activate  # No Windows use `venv\Scripts\activate`
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Configuração do Banco de Dados:

Assegure-se de que você tem uma instância do PostgreSQL rodando e crie um banco de dados chamado `postgres`. Altere a string de conexão em `app.py` se necessário:

```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://postgres:senha@localhost:5432/postgres'
```

Inicialize o banco de dados:

```bash
python3 app.py
```

## Uso

Inicie o servidor Flask:

```bash
python3 app.py
```

Acesse o aplicativo no navegador:

Abra seu navegador e vá para [http://127.0.0.1:5000](http://127.0.0.1:5000).

## Estrutura do Banco de Dados

O banco de dados PostgreSQL contém as seguintes tabelas:

### Clientes

| Campo      | Tipo         | Descrição           |
|------------|--------------|---------------------|
| cliente_id | SERIAL (PK)  | Identificador único |
| nome       | VARCHAR(100) | Nome do cliente     |
| email      | VARCHAR(100) | Email do cliente    |
| telefone   | VARCHAR(15)  | Telefone do cliente |

### Cursos

| Campo      | Tipo         | Descrição          |
|------------|--------------|--------------------|
| curso_id   | SERIAL (PK)  | Identificador único|
| nome       | VARCHAR(100) | Nome do curso      |
| descricao  | TEXT         | Descrição do curso |
| preco      | NUMERIC(10, 2)| Preço do curso    |

### Vendedores

| Campo        | Tipo        | Descrição            |
|--------------|-------------|----------------------|
| vendedor_id  | SERIAL (PK) | Identificador único  |
| nome         | VARCHAR(100)| Nome do vendedor     |
| email        | VARCHAR(100)| Email do vendedor    |

### Vendas

| Campo       | Tipo         | Descrição               |
|-------------|--------------|-------------------------|
| venda_id    | SERIAL (PK)  | Identificador único     |
| cliente_id  | INTEGER (FK) | Referência para o cliente|
| curso_id    | INTEGER (FK) | Referência para o curso  |
| vendedor_id | INTEGER (FK) | Referência para o vendedor|
| data_venda  | DATE         | Data da venda           |

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

## Licença

Este projeto está licenciado sob a MIT License.

## Contato

Para mais informações, entre em contato com seu-nome.
