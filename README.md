# Sistema de Controle de Estoque — Development with Python

Aplicação de controle de estoque desenvolvida em **Python**, com **duas
interfaces independentes que compartilham o mesmo banco de dados**:

- **Desktop**, feita com **Tkinter** (`main.py`);
- **Web**, feita com **Flask** (`webapp.py`), acessível pelo navegador.

Ambas usam exatamente as mesmas regras de negócio (pasta `models/`) e o
mesmo arquivo de banco de dados (`database/estoque.db`), então qualquer
cadastro ou movimentação feita em uma interface aparece na outra assim que
a página/tela é atualizada.

## Estrutura de pastas

```
app/
├── main.py                  # ponto de entrada da interface DESKTOP (Tkinter)
├── webapp.py                # ponto de entrada da interface WEB (Flask)
├── requirements.txt         # dependências externas (pandas, openpyxl, flask)
├── database/
│   ├── db.py                 # criação das tabelas e conexão com o SQLite
│   └── schema.sql            # script SQL da estrutura do banco (referência)
├── models/                   # regras de negócio, compartilhadas pelas 2 interfaces
│   ├── usuario.py
│   ├── categoria.py
│   ├── fornecedor.py
│   ├── produto.py
│   └── relatorio.py
├── ui/                        # interface DESKTOP (Tkinter)
│   ├── login.py
│   └── principal.py
├── templates/                 # interface WEB (Flask) — páginas HTML
│   ├── base.html
│   ├── login.html
│   ├── dashboard.html
│   ├── produto_form.html
│   ├── fornecedor_form.html
│   ├── movimentacao_form.html
│   ├── usuario_form.html
│   └── relatorios.html
└── README.md
```

## Como executar

1. Instale o Python 3 (https://www.python.org/) — Tkinter e sqlite3 já vêm
   inclusos na instalação padrão.
2. Instale as dependências externas (pandas, openpyxl e Flask):
   ```
   pip install -r requirements.txt --break-system-packages
   ```

### Rodando a interface Desktop (Tkinter)

```
python main.py
```

### Rodando a interface Web (Flask)

```
python webapp.py
```

Depois, abra o navegador em **http://127.0.0.1:5000**.

> Você pode rodar as duas interfaces **ao mesmo tempo**, em dois terminais
> diferentes — elas vão continuar sincronizadas, pois compartilham o mesmo
> arquivo `database/estoque.db`.

Na primeira execução (de qualquer uma das duas interfaces) o banco
`database/estoque.db` é criado automaticamente, junto com um usuário
administrador padrão:
- **login:** admin
- **senha:** admin123

## Solução de problemas comuns

Durante o desenvolvimento e os testes deste projeto, foram encontrados (e
resolvidos) os seguintes problemas operacionais, documentados aqui para
referência futura:

- **"http://127.0.0.1:5000 não abre" ou o navegador não carrega a página:**
  o motivo mais comum é a **porta 5000 já estar ocupada** por uma execução
  anterior do `webapp.py` que não foi encerrada corretamente (por exemplo, o
  terminal foi fechado sem interromper o processo com `Ctrl+C`, deixando o
  servidor "preso" em segundo plano). Para diagnosticar e resolver:
  ```
  # Verifica se algum processo já está usando a porta 5000
  lsof -i :5000

  # Encerra esse processo (troque <PID> pelo número mostrado no comando acima)
  kill -9 <PID>

  # Roda o servidor novamente
  python webapp.py
  ```
  Depois de encerrar o processo antigo, o terminal volta a mostrar a mensagem
  `Running on http://127.0.0.1:5000`, e o navegador passa a abrir normalmente.

- **`ModuleNotFoundError` ao rodar `main.py` ou `webapp.py`:** normalmente
  indica que as dependências não foram instaladas no ambiente atual. Rode
  novamente `pip install -r requirements.txt --break-system-packages` dentro
  da pasta do projeto.

- **A janela do Tkinter abre cortada, sem mostrar o botão de confirmação:**
  pode ocorrer em telas com escala de fonte (DPI) maior que o padrão. Basta
  redimensionar a janela manualmente (arrastando a borda inferior) ou clicar
  no ícone de maximizar na barra de título da janela.

## Funcionalidades implementadas

- [x] Login com validação de usuário e senha (senha armazenada como hash SHA-256)
- [x] Dois perfis de acesso (administrador / comum)
- [x] Cadastro de produtos com validação de campos obrigatórios e numéricos
- [x] Código do produto gerado automaticamente (aleatório e único)
- [x] Categoria e fornecedor normalizados em tabelas próprias
- [x] Registro de entrada e saída de estoque, com preço histórico preservado
- [x] Listagem com destaque visual para produtos abaixo da quantidade mínima
- [x] Cadastro de novos usuários (restrito ao administrador)
- [x] Geração de relatórios exportáveis (CSV ou Excel) usando pandas
- [x] **Duas interfaces (desktop com Tkinter e web com Flask), sincronizadas
      através do mesmo banco de dados SQLite**
- [x] Persistência em banco de dados relacional (SQLite)

## Como funciona a sincronização entre desktop e navegador (webapp.py)

As duas interfaces são **processos independentes**, mas chamam exatamente
as mesmas funções de `models/`, que sempre leem/gravam diretamente no
arquivo `database/estoque.db`. Não há cópia de dados em memória entre elas.

- No **Tkinter**, clicar em **"Atualizar Lista"** busca os dados mais
  recentes do banco.
- No **Flask**, isso acontece automaticamente a cada requisição — ou seja,
  toda vez que a página é carregada ou recarregada (F5), ela já mostra os
  dados mais atuais gravados por qualquer uma das duas interfaces.

Esse é o nível de sincronização "sob demanda" (ao atualizar/recarregar).
Uma sincronização "em tempo real" (sem precisar recarregar a página)
exigiria mecanismos adicionais, como WebSockets (ex.: Flask-SocketIO) ou
consultas repetidas via JavaScript (polling) — fora do escopo deste projeto.

## Possíveis evoluções

- Sincronização em tempo real entre as interfaces (WebSockets/polling)
- Exportar relatórios também em PDF ou com gráficos
- Uso de bcrypt para reforçar a criptografia de senha
- Importação de produtos em lote a partir de um arquivo CSV
