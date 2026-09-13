# 📦 Sistema de Controle de Estoque

Aplicação de gerenciamento de estoque desenvolvida em Python como projeto acadêmico da disciplina **Development with Python**, do Centro Universitário UniFECAF.

O sistema permite cadastrar produtos, registrar entradas e saídas de estoque, controlar usuários e gerar relatórios, utilizando duas interfaces: desktop, desenvolvida com Tkinter, e web, desenvolvida com Flask.

As duas interfaces compartilham as mesmas regras de negócio e o mesmo banco de dados SQLite, permitindo que as informações sejam utilizadas por ambas as aplicações.

---

## 🎯 Objetivo do projeto

Desenvolver uma aplicação de controle de estoque capaz de organizar produtos, registrar movimentações e fornecer informações para auxiliar o acompanhamento dos níveis de estoque.

O projeto também tem como objetivos demonstrar conhecimentos em:

* Programação em Python;
* Desenvolvimento de interfaces gráficas;
* Desenvolvimento de aplicações web;
* Modelagem e persistência de dados;
* Regras de negócio e validação de informações;
* Autenticação e controle de acesso;
* Geração de relatórios;
* Organização de projetos de software.

---

## 🚀 Funcionalidades

### 🔐 Autenticação e usuários

* Login com usuário e senha.
* Controle de sessão na interface web.
* Dois perfis de acesso: Administrador e Comum.
* Cadastro de novos usuários, restrito ao Administrador.
* Armazenamento de senhas utilizando hash SHA-256.

### 📦 Gestão de produtos

* Cadastro de produtos.
* Edição e exclusão de produtos.
* Geração automática de código único para o produto.
* Validação de campos obrigatórios e valores numéricos.
* Cadastro e associação de categorias.
* Cadastro e associação de fornecedores.
* Definição da quantidade atual e da quantidade mínima de estoque.

### 🔄 Movimentações de estoque

* Registro de entradas de produtos.
* Registro de saídas de produtos.
* Atualização da quantidade disponível.
* Preservação do preço unitário praticado no momento da movimentação.
* Registro do usuário responsável pela operação.
* Histórico das movimentações.

### 📊 Consultas e relatórios

* Visualização do estoque atual.
* Identificação de produtos abaixo da quantidade mínima.
* Consulta de movimentações.
* Geração de relatórios de estoque.
* Geração de relatórios de movimentações.
* Exportação dos relatórios para CSV e Excel.

### 🖥️ Duas interfaces

O projeto possui duas formas de utilização:

**Desktop — Tkinter**

Interface gráfica executada diretamente no computador.

**Web — Flask**

Interface acessível pelo navegador, executada localmente por meio de um servidor Flask.

As duas interfaces utilizam as mesmas funções de negócio e o mesmo banco de dados.

---

## 🏗️ Arquitetura da aplicação

A aplicação foi organizada de forma a separar as interfaces, as regras de negócio e a persistência dos dados.

```text
┌──────────────────────────────┐
│       INTERFACES             │
│                              │
│  Tkinter       Flask         │
│  Desktop       Web           │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       REGRAS DE NEGÓCIO       │
│                              │
│  models/                     │
│  Usuários                    │
│  Produtos                    │
│  Categorias                  │
│  Fornecedores                │
│  Movimentações               │
│  Relatórios                  │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       BANCO DE DADOS         │
│                              │
│  SQLite                      │
│  database/estoque.db         │
└──────────────────────────────┘
```

Essa organização permite que as duas interfaces utilizem as mesmas validações e operações, evitando a duplicação das regras de negócio.

---

## 🗂️ Estrutura do projeto

```text
SISTEMA-DE-CONTROLE-DE-ESTOQUE/
│
├── main.py
├── webapp.py
├── requirements.txt
│
├── database/
│   ├── db.py
│   └── schema.sql
│
├── models/
│   ├── usuario.py
│   ├── categoria.py
│   ├── fornecedor.py
│   ├── produto.py
│   └── relatorio.py
│
├── ui/
│   ├── login.py
│   └── principal.py
│
├── templates/
│   ├── base.html
│   ├── login.html
│   ├── dashboard.html
│   ├── produto_form.html
│   ├── fornecedor_form.html
│   ├── movimentacao_form.html
│   ├── usuario_form.html
│   └── relatorios.html
│
├── database/
│   └── estoque.db
│
├── Parte_Teorica_Documentacao_Modelagem.pdf
│
├── Projeto_Python_Controle_Estoque.zip
│
├── LICENSE
│
└── README.md
```

> A estrutura acima representa a organização da aplicação. O arquivo SQLite é criado automaticamente na primeira execução, caso ainda não exista.

---

## 🛠️ Tecnologias utilizadas

| Tecnologia | Aplicação                             |
| ---------- | ------------------------------------- |
| Python 3   | Linguagem de programação              |
| Tkinter    | Interface desktop                     |
| Flask      | Interface web                         |
| SQLite     | Banco de dados relacional             |
| Pandas     | Processamento e geração de relatórios |
| Openpyxl   | Exportação de relatórios para Excel   |
| HTML       | Estrutura das páginas web             |
| Jinja2     | Templates da aplicação Flask          |

---

## ▶️ Como executar

### 1. Pré-requisitos

Instale o Python 3 no computador.

O projeto utiliza Tkinter e SQLite, disponíveis na instalação padrão do Python em ambientes compatíveis.

### 2. Clone o repositório

```bash
git clone https://github.com/Sponge1774/SISTEMA-DE-CONTROLE-DE-ESTOQUE.git
```

Entre na pasta do projeto:

```bash
cd SISTEMA-DE-CONTROLE-DE-ESTOQUE
```

### 3. Instale as dependências

```bash
pip install -r requirements.txt
```

Em distribuições Linux que utilizam o gerenciamento de pacotes do sistema, pode ser necessário utilizar:

```bash
pip install -r requirements.txt --break-system-packages
```

### 4. Execute a interface desktop

```bash
python main.py
```

A aplicação abrirá a interface gráfica do sistema.

### 5. Execute a interface web

Em outro terminal, dentro da pasta do projeto:

```bash
python webapp.py
```

Depois, abra o navegador no endereço:

```text
http://127.0.0.1:5000
```

As duas interfaces podem ser executadas simultaneamente, desde que estejam em terminais separados.

---

## 👤 Usuário administrador padrão

Na primeira execução, o sistema cria automaticamente o banco de dados e um usuário administrador padrão.

| Campo  | Valor         |
| ------ | ------------- |
| Login  | admin         |
| Senha  | admin123      |
| Perfil | Administrador |

**Importante:** altere a senha padrão antes de utilizar o sistema em um ambiente real.

---

## 🔄 Sincronização entre as interfaces

A aplicação utiliza um único banco de dados SQLite compartilhado entre o Tkinter e o Flask.

Quando uma movimentação ou cadastro é realizado em uma interface, os dados são gravados no mesmo arquivo de banco de dados.

* No Tkinter, utilize a opção de atualização da lista para consultar os dados mais recentes.
* No Flask, recarregue a página para consultar as informações atualizadas.

A sincronização atual é feita sob demanda. Uma atualização automática em tempo real, sem recarregar a página ou a tela, não faz parte do escopo implementado.

---

## 🗃️ Modelagem do banco de dados

O banco de dados SQLite foi estruturado com as seguintes entidades principais:

* `usuario`
* `categoria`
* `fornecedor`
* `produto`
* `movimentacao`

A tabela `movimentacao` registra as entradas e saídas, mantendo o vínculo com o produto e o usuário responsável pela operação.

O arquivo `database/schema.sql` apresenta o script SQL de referência para a estrutura do banco de dados.

---

## 📚 Documentação acadêmica

Este repositório contém a documentação teórica e a modelagem da aplicação, incluindo:

* Introdução e justificativa do sistema;
* Estrutura de dados e relacionamentos;
* Arquitetura das interfaces desktop e web;
* Fluxograma da lógica da aplicação;
* Reflexões sobre o desafio proposto;
* Código-fonte da aplicação;
* Script SQL do banco de dados;
* Análise conceitual sobre sincronização em tempo real;
* Capturas de tela da aplicação em execução.

📄 [Consultar a documentação teórica e a modelagem](Parte_Teorica_Documentacao_Modelagem.pdf)

---

## 🔮 Possíveis evoluções

Entre as melhorias que podem ser implementadas em versões futuras estão:

* Sincronização automática em tempo real utilizando WebSockets ou polling.
* Geração de relatórios em PDF.
* Inclusão de gráficos para análise do estoque.
* Importação de produtos em lote por CSV.
* Utilização de bcrypt ou Argon2 para armazenamento de senhas.
* Implementação de testes automatizados.
* Migração para um banco de dados cliente-servidor, como PostgreSQL ou MySQL.
* Publicação da interface web em um servidor de produção.

---

## 🎓 Contexto acadêmico

**Instituição:** Centro Universitário UniFECAF

**Disciplina:** Development with Python

**Aluno:** Eduardo Souza Mattos

**R.A.:** 35984

**Ano:** 2026

---

## 📄 Licença

Este projeto está disponibilizado sob a licença MIT.

Consulte o arquivo [LICENSE](LICENSE) para obter os detalhes.
