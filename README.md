# Sistema de Controle de Estoque

Aplicação de controle de estoque desenvolvida em Python, com duas interfaces de utilização: uma aplicação desktop construída com Tkinter e uma aplicação web desenvolvida com Flask.

O projeto utiliza regras de negócio compartilhadas e um banco de dados SQLite, permitindo controlar produtos, categorias, fornecedores e movimentações de entrada e saída de estoque.

---

## Português

### Sobre o projeto

O Sistema de Controle de Estoque foi desenvolvido como projeto acadêmico da disciplina **Development with Python**, do Centro Universitário UniFECAF.

A aplicação foi projetada para demonstrar a utilização de Python em um sistema integrado de gerenciamento de estoque, reunindo:

* Interface desktop com Tkinter;
* Interface web com Flask;
* Banco de dados SQLite;
* Autenticação de usuários;
* Controle de permissões;
* Cadastro de produtos;
* Controle de categorias e fornecedores;
* Registro de entradas e saídas;
* Relatórios de estoque;
* Exportação de dados para CSV e Excel.

O sistema utiliza uma estrutura compartilhada de regras de negócio, permitindo que as interfaces desktop e web trabalhem com os mesmos dados.

---

### Objetivos

O projeto tem como principais objetivos:

* Desenvolver uma aplicação prática utilizando Python;
* Aplicar conceitos de programação orientada a objetos;
* Trabalhar com banco de dados SQLite;
* Implementar autenticação e controle de acesso;
* Organizar regras de negócio em módulos reutilizáveis;
* Criar interfaces desktop e web;
* Registrar e consultar movimentações de estoque;
* Gerar relatórios para análise dos dados;
* Aplicar conceitos de modelagem de dados e organização de sistemas.

---

### Funcionalidades

#### Autenticação

* Tela de login;
* Validação de usuário e senha;
* Usuário administrador;
* Usuário comum;
* Controle de acesso conforme o perfil;
* Senhas armazenadas utilizando hash SHA-256.

#### Gerenciamento de produtos

* Cadastro de produtos;
* Alteração de produtos;
* Exclusão de produtos;
* Consulta de produtos;
* Controle de quantidade em estoque;
* Definição de estoque mínimo;
* Associação com categorias e fornecedores.

#### Gerenciamento de categorias

* Cadastro de categorias;
* Alteração de categorias;
* Exclusão de categorias;
* Consulta de categorias.

#### Gerenciamento de fornecedores

* Cadastro de fornecedores;
* Alteração de fornecedores;
* Exclusão de fornecedores;
* Consulta de fornecedores.

#### Movimentações de estoque

* Registro de entradas;
* Registro de saídas;
* Atualização da quantidade disponível;
* Registro da data da movimentação;
* Associação da movimentação ao produto;
* Controle do estoque mínimo.

#### Relatórios

* Consulta do estoque atual;
* Consulta de movimentações;
* Exportação para CSV;
* Exportação para Excel;
* Utilização da biblioteca `pandas`;
* Geração de planilhas com `openpyxl`.

---

### Tecnologias utilizadas

* **Python 3**
* **Tkinter**
* **Flask**
* **SQLite**
* **Pandas**
* **OpenPyXL**
* **HTML**
* **CSS**
* **Jinja2**
* **SHA-256**

---

### Estrutura do projeto

```text
SISTEMA-DE-CONTROLE-DE-ESTOQUE/
│
├── database/
│   └── estoque.db
│
├── models/
│   ├── categoria.py
│   ├── fornecedor.py
│   ├── movimentacao.py
│   ├── produto.py
│   └── usuario.py
│
├── templates/
│   ├── base.html
│   ├── login.html
│   ├── index.html
│   ├── produtos.html
│   ├── categorias.html
│   ├── fornecedores.html
│   └── movimentacoes.html
│
├── static/
│   ├── css/
│   └── js/
│
├── docs/
│   └── images/
│       ├── tela-login.png
│       ├── tela-principal.png
│       ├── cadastro-produtos.png
│       ├── movimentacao-estoque.png
│       ├── relatorios.png
│       └── modelo-banco-dados.png
│
├── main.py
├── webapp.py
├── requirements.txt
└── README.md
```

> A estrutura apresentada pode variar conforme a versão do projeto e os arquivos existentes no repositório.

---

### Interfaces do sistema

O projeto possui duas formas de utilização.

#### Aplicação desktop

A aplicação desktop utiliza a biblioteca Tkinter e pode ser executada diretamente pelo arquivo `main.py`.

```bash
python main.py
```

#### Aplicação web

A aplicação web utiliza o framework Flask e pode ser executada pelo arquivo `webapp.py`.

```bash
python webapp.py
```

Após iniciar a aplicação web, acesse no navegador:

```text
http://127.0.0.1:5000
```

---

### Demonstração visual

As imagens de demonstração devem ser mantidas na pasta:

```text
docs/images/
```

#### Tela de login

![Tela de login](docs/images/tela-login.png)

#### Tela principal

![Tela principal](docs/images/tela-principal.png)

#### Cadastro de produtos

![Cadastro de produtos](docs/images/cadastro-produtos.png)

#### Movimentação de estoque

![Movimentação de estoque](docs/images/movimentacao-estoque.png)

#### Relatórios

![Relatórios](docs/images/relatorios.png)

#### Modelo do banco de dados

![Modelo do banco de dados](docs/images/modelo-banco-dados.png)

---

### Instalação

Clone o repositório:

```bash
git clone https://github.com/Sponge1774/SISTEMA-DE-CONTROLE-DE-ESTOQUE.git
```

Entre na pasta do projeto:

```bash
cd SISTEMA-DE-CONTROLE-DE-ESTOQUE
```

Crie um ambiente virtual:

```bash
python -m venv venv
```

Ative o ambiente virtual.

No Linux:

```bash
source venv/bin/activate
```

No Windows:

```powershell
venv\Scripts\activate
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

---

### Dependências

As principais bibliotecas utilizadas no projeto são:

```text
pandas
openpyxl
flask
```

Caso o arquivo `requirements.txt` ainda não exista, as dependências podem ser instaladas manualmente:

```bash
pip install pandas openpyxl flask
```

---

### Credenciais padrão

As credenciais utilizadas para o primeiro acesso são:

```text
Usuário: admin
Senha: admin123
```

Recomenda-se alterar a senha padrão em um ambiente de utilização real.

---

### Banco de dados

O sistema utiliza o banco de dados SQLite, armazenado no arquivo:

```text
database/estoque.db
```

O modelo de dados é composto pelas principais tabelas:

* `usuario`;
* `categoria`;
* `fornecedor`;
* `produto`;
* `movimentacao`.

Relacionamentos principais:

* Um usuário pode realizar várias movimentações;
* Uma categoria pode estar associada a vários produtos;
* Um fornecedor pode fornecer vários produtos;
* Um produto pode possuir várias movimentações;
* Cada movimentação está relacionada a um produto.

---

### Segurança

O sistema possui mecanismos básicos de segurança, incluindo:

* Autenticação de usuários;
* Controle de permissões;
* Separação entre usuário administrador e usuário comum;
* Armazenamento de senhas com hash SHA-256;
* Validação das operações de cadastro;
* Restrição de determinadas funções conforme o perfil.

Por se tratar de um projeto acadêmico, recomenda-se implementar mecanismos adicionais para utilização em produção, como:

* Hash com algoritmo específico para senhas, como Argon2 ou bcrypt;
* Controle de sessão mais robusto;
* Proteção contra CSRF;
* Validação avançada de entradas;
* Registro de logs;
* Controle de tentativas de login;
* Configuração de variáveis de ambiente.

---

### Sincronização

As interfaces desktop e web utilizam as mesmas regras de negócio e o mesmo banco de dados SQLite.

A sincronização entre as interfaces ocorre por meio da utilização compartilhada do banco de dados. A atualização dos dados depende da consulta ou recarregamento das informações na interface utilizada.

Uma possível evolução do projeto seria implementar atualização em tempo real entre as interfaces.

---

### Documentação acadêmica

O projeto foi acompanhado de documentação teórica e técnica, incluindo:

* Descrição do sistema;
* Objetivos do projeto;
* Tecnologias utilizadas;
* Modelagem do banco de dados;
* Descrição das funcionalidades;
* Regras de negócio;
* Estrutura das tabelas;
* Considerações sobre segurança;
* Possíveis melhorias futuras.

**Autor:** Eduardo Souza Mattos
**R.A.:** 35984
**Instituição:** Centro Universitário UniFECAF
**Curso:** Análise e Desenvolvimento de Sistemas
**Disciplina:** Development with Python
**Ano:** 2026

---

### Melhorias futuras

Entre as possíveis melhorias estão:

* Implementação de atualização em tempo real;
* Criação de uma API REST;
* Integração com banco de dados PostgreSQL ou MySQL;
* Inclusão de gráficos de movimentação;
* Dashboard administrativo;
* Controle de estoque por localização;
* Cadastro de usuários pela interface;
* Recuperação de senha;
* Relatórios em PDF;
* Implementação de testes automatizados;
* Uso de Docker;
* Deploy em servidor;
* Melhoria da interface responsiva;
* Implementação de níveis de permissão mais detalhados.

---

### Licença

Este projeto foi desenvolvido para fins acadêmicos e educacionais.

---

# Inventory Control System

Python-based inventory management application with two user interfaces: a desktop application developed with Tkinter and a web application developed with Flask.

The project uses shared business rules and an SQLite database to manage products, categories, suppliers, and stock movements.

---

## English

### About the project

The Inventory Control System was developed as an academic project for the **Development with Python** course at Centro Universitário UniFECAF.

The application demonstrates the use of Python in an integrated inventory management system, including:

* Tkinter desktop interface;
* Flask web interface;
* SQLite database;
* User authentication;
* Access control;
* Product management;
* Category and supplier management;
* Stock entries and exits;
* Inventory reports;
* CSV and Excel data export.

The system uses shared business rules, allowing both desktop and web interfaces to work with the same data.

---

### Objectives

The main objectives of the project are:

* Develop a practical application using Python;
* Apply object-oriented programming concepts;
* Work with an SQLite database;
* Implement authentication and access control;
* Organize business rules into reusable modules;
* Create desktop and web interfaces;
* Register and consult stock movements;
* Generate reports for data analysis;
* Apply data modeling and system organization concepts.

---

### Features

#### Authentication

* Login screen;
* Username and password validation;
* Administrator user;
* Common user;
* Profile-based access control;
* Password storage using SHA-256 hashing.

#### Product management

* Product registration;
* Product updates;
* Product deletion;
* Product search;
* Stock quantity control;
* Minimum stock level;
* Category and supplier association.

#### Category management

* Category registration;
* Category updates;
* Category deletion;
* Category search.

#### Supplier management

* Supplier registration;
* Supplier updates;
* Supplier deletion;
* Supplier search.

#### Stock movements

* Stock entry registration;
* Stock exit registration;
* Available quantity updates;
* Movement date registration;
* Product association;
* Minimum stock control.

#### Reports

* Current inventory consultation;
* Stock movement consultation;
* CSV export;
* Excel export;
* Use of the `pandas` library;
* Spreadsheet generation with `openpyxl`.

---

### Technologies

* **Python 3**
* **Tkinter**
* **Flask**
* **SQLite**
* **Pandas**
* **OpenPyXL**
* **HTML**
* **CSS**
* **Jinja2**
* **SHA-256**

---

### Project structure

```text
SISTEMA-DE-CONTROLE-DE-ESTOQUE/
│
├── database/
│   └── estoque.db
│
├── models/
│   ├── categoria.py
│   ├── fornecedor.py
│   ├── movimentacao.py
│   ├── produto.py
│   └── usuario.py
│
├── templates/
│   ├── base.html
│   ├── login.html
│   ├── index.html
│   ├── produtos.html
│   ├── categorias.html
│   ├── fornecedores.html
│   └── movimentacoes.html
│
├── static/
│   ├── css/
│   └── js/
│
├── docs/
│   └── images/
│       ├── tela-login.png
│       ├── tela-principal.png
│       ├── cadastro-produtos.png
│       ├── movimentacao-estoque.png
│       ├── relatorios.png
│       └── modelo-banco-dados.png
│
├── main.py
├── webapp.py
├── requirements.txt
└── README.md
```

> The structure may vary depending on the project version and the files available in the repository.

---

### System interfaces

The project provides two ways to use the system.

#### Desktop application

The desktop application uses Tkinter and can be started through `main.py`.

```bash
python main.py
```

#### Web application

The web application uses the Flask framework and can be started through `webapp.py`.

```bash
python webapp.py
```

After starting the web application, open the following address in your browser:

```text
http://127.0.0.1:5000
```

---

### Visual demonstration

Demonstration images should be stored in:

```text
docs/images/
```

#### Login screen

![Login screen](docs/images/tela-login.png)

#### Main screen

![Main screen](docs/images/tela-principal.png)

#### Product registration

![Product registration](docs/images/cadastro-produtos.png)

#### Stock movement

![Stock movement](docs/images/movimentacao-estoque.png)

#### Reports

![Reports](docs/images/relatorios.png)

#### Database model

![Database model](docs/images/modelo-banco-dados.png)

---

### Installation

Clone the repository:

```bash
git clone https://github.com/Sponge1774/SISTEMA-DE-CONTROLE-DE-ESTOQUE.git
```

Enter the project directory:

```bash
cd SISTEMA-DE-CONTROLE-DE-ESTOQUE
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the virtual environment.

On Linux:

```bash
source venv/bin/activate
```

On Windows:

```powershell
venv\Scripts\activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

---

### Dependencies

The main libraries used in the project are:

```text
pandas
openpyxl
flask
```

If the `requirements.txt` file does not exist, install the dependencies manually:

```bash
pip install pandas openpyxl flask
```

---

### Default credentials

The default credentials for the first access are:

```text
Username: admin
Password: admin123
```

The default password should be changed in a real-world environment.

---

### Database

The system uses an SQLite database stored in:

```text
database/estoque.db
```

The data model includes the following main tables:

* `usuario`;
* `categoria`;
* `fornecedor`;
* `produto`;
* `movimentacao`.

Main relationships:

* One user can perform multiple stock movements;
* One category can be associated with multiple products;
* One supplier can provide multiple products;
* One product can have multiple stock movements;
* Each movement is related to a product.

---

### Security

The system includes basic security mechanisms, such as:

* User authentication;
* Permission control;
* Separation between administrator and common users;
* Password storage using SHA-256 hashing;
* Validation of registration operations;
* Profile-based access restrictions.

Since this is an academic project, additional mechanisms are recommended for production use, including:

* Password hashing with algorithms such as Argon2 or bcrypt;
* More robust session management;
* CSRF protection;
* Advanced input validation;
* Log registration;
* Login attempt control;
* Environment variable configuration.

---

### Synchronization

The desktop and web interfaces use the same business rules and SQLite database.

Synchronization between the interfaces is achieved through the shared database. Data updates depend on querying or reloading information in the interface being used.

A possible future improvement would be implementing real-time updates between the interfaces.

---

### Academic documentation

The project was accompanied by theoretical and technical documentation, including:

* System description;
* Project objectives;
* Technologies used;
* Database modeling;
* Feature descriptions;
* Business rules;
* Table structure;
* Security considerations;
* Possible future improvements.

**Author:** Eduardo Souza Mattos
**Academic ID:** 35984
**Institution:** Centro Universitário UniFECAF
**Program:** Systems Analysis and Development
**Course:** Development with Python
**Year:** 2026

---

### Future improvements

Possible future improvements include:

* Real-time updates;
* REST API implementation;
* Integration with PostgreSQL or MySQL;
* Stock movement charts;
* Administrative dashboard;
* Inventory control by location;
* User registration through the interface;
* Password recovery;
* PDF reports;
* Automated tests;
* Docker support;
* Server deployment;
* Improved responsive interface;
* More detailed permission levels.

---

### License

This project was developed for academic and educational purposes.
