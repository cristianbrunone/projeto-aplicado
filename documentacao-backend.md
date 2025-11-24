# 🔧 Documentação Técnica - Backend
## Sistema de Gestão de Estoque e Manutenção

---

## 📋 Índice

1. [Visão Geral](#visão-geral)
2. [Arquitetura](#arquitetura)
3. [Tecnologias](#tecnologias)
4. [Instalação e Configuração](#instalação-e-configuração)
5. [Estrutura do Projeto](#estrutura-do-projeto)
6. [Modelos de Dados](#modelos-de-dados)
7. [API Endpoints](#api-endpoints)
8. [Serviços](#serviços)
9. [Deploy](#deploy)
10. [Testes](#testes)

---

## 🎯 Visão Geral

O backend do sistema é uma **API RESTful** desenvolvida em **Python** utilizando o framework **Flask**. Ele fornece endpoints para gerenciamento de usuários, peças, ordens de serviço e alertas de estoque.

### Características Principais

- ✅ API RESTful completa
- ✅ Autenticação de usuários
- ✅ ORM com SQLAlchemy
- ✅ Banco de dados PostgreSQL
- ✅ Containerização com Docker
- ✅ Migrations automáticas
- ✅ Sistema de alertas automáticos
- ✅ Validação de dados
- ✅ Tratamento de erros robusto

---

## 🏗️ Arquitetura

### Padrão de Arquitetura

O backend segue uma arquitetura em camadas:

```
┌─────────────────────────────────┐
│      Routes (Endpoints)         │  ← Recebe requisições HTTP
├─────────────────────────────────┤
│      Services (Lógica)          │  ← Processa regras de negócio
├─────────────────────────────────┤
│      Models (ORM)               │  ← Define estrutura de dados
├─────────────────────────────────┤
│      Database (PostgreSQL)      │  ← Armazena dados
└─────────────────────────────────┘
```

### Fluxo de Requisição

```
Cliente → Route → Service → Model → Database
                                       ↓
Cliente ← JSON Response ← Service ← Model
```

---

## 💻 Tecnologias

| Tecnologia | Versão | Propósito |
|------------|--------|-----------|
| **Python** | 3.11+ | Linguagem principal |
| **Flask** | 3.0+ | Framework web |
| **SQLAlchemy** | 2.0+ | ORM (Object-Relational Mapping) |
| **PostgreSQL** | 15+ | Banco de dados relacional |
| **psycopg2** | 2.9+ | Driver PostgreSQL |
| **Flask-CORS** | 4.0+ | Gerenciamento de CORS |
| **Docker** | 24+ | Containerização |

---

## 🚀 Instalação e Configuração

### Pré-requisitos

- Python 3.11+
- PostgreSQL 15+
- Docker e Docker Compose (opcional, mas recomendado)

### Opção 1: Com Docker (Recomendado)

```bash
# Clone o repositório
git clone <url-do-repositorio>
cd projeto-aplicado

# Suba os containers
docker-compose up --build

# O backend estará disponível em http://localhost:6000
```

### Opção 2: Instalação Manual

```bash
# Navegue até o diretório backend
cd backend

# Crie um ambiente virtual
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate  # Windows

# Instale as dependências
pip install -r requirements.txt

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o .env com suas configurações

# Execute as migrations
flask db upgrade

# Inicie o servidor
python wsgi.py
```

### Variáveis de Ambiente

Crie um arquivo `.env` na raiz do backend:

```env
# Database
DATABASE_URL=postgresql://usuario:senha@localhost:5432/gestao_estoque

# Flask
FLASK_APP=wsgi.py
FLASK_ENV=development
SECRET_KEY=sua-chave-secreta-aqui

# Server
HOST=0.0.0.0
PORT=6000
```

---

## 📁 Estrutura do Projeto

```
backend/
├── app/
│   ├── __init__.py           # Inicialização da aplicação Flask
│   ├── models/
│   │   ├── __init__.py
│   │   └── models.py         # Modelos SQLAlchemy
│   ├── routes/
│   │   └── routes.py         # Definição de rotas/endpoints
│   ├── services/
│   │   ├── alertas.py        # Lógica de alertas de estoque
│   │   ├── login.py          # Autenticação
│   │   ├── notificacoes_estoque.py
│   │   ├── ordem_servico.py  # Lógica de ordens de serviço
│   │   ├── peca.py           # Lógica de peças
│   │   └── usuario.py        # Lógica de usuários
│   └── utils/
│       └── json_response.py  # Helpers para respostas JSON
├── Dockerfile                # Configuração Docker
├── requirements.txt          # Dependências Python
├── wait-for-db.sh           # Script de inicialização
└── wsgi.py                  # Entry point da aplicação
```

---

## 🗄️ Modelos de Dados

### 1. Usuario

Representa usuários do sistema (administradores e técnicos).

```python
class Usuario(db.Model):
    __tablename__ = 'usuarios'
    
    id = db.Column(db.Integer, primary_key=True)
    nome = db.Column(db.String(100), nullable=False)
    usuario = db.Column(db.String(50), unique=True, nullable=False)
    senha = db.Column(db.String(255), nullable=False)
    tipo = db.Column(db.String(20), nullable=False)  # 'admin' ou 'tecnico'
    created_at = db.Column(db.DateTime, default=datetime.utcnow)
```

**Relacionamentos:**
- Um usuário pode ter várias ordens de serviço (como técnico)

---

### 2. Peca

Representa peças/itens do estoque.

```python
class Peca(db.Model):
    __tablename__ = 'pecas'
    
    id = db.Column(db.Integer, primary_key=True)
    nome = db.Column(db.String(100), nullable=False)
    descricao = db.Column(db.Text)
    quantidade = db.Column(db.Integer, nullable=False, default=0)
    quantidade_minima = db.Column(db.Integer, nullable=False)
    quantidade_maxima = db.Column(db.Integer, nullable=False)
    created_at = db.Column(db.DateTime, default=datetime.utcnow)
    updated_at = db.Column(db.DateTime, onupdate=datetime.utcnow)
```

**Validações:**
- `quantidade >= 0`
- `quantidade_minima < quantidade_maxima`

---

### 3. OrdemServico

Representa ordens de serviço/manutenção.

```python
class OrdemServico(db.Model):
    __tablename__ = 'ordens_servico'
    
    id = db.Column(db.Integer, primary_key=True)
    descricao = db.Column(db.Text, nullable=False)
    status = db.Column(db.String(20), nullable=False)  # 'pendente', 'em_andamento', 'concluida'
    tecnico_id = db.Column(db.Integer, db.ForeignKey('usuarios.id'))
    pecas_utilizadas = db.Column(db.JSON)  # Lista de {peca_id, quantidade}
    created_at = db.Column(db.DateTime, default=datetime.utcnow)
    updated_at = db.Column(db.DateTime, onupdate=datetime.utcnow)
    
    # Relacionamento
    tecnico = db.relationship('Usuario', backref='ordens')
```

**Status possíveis:**
- `pendente`: Aguardando início
- `em_andamento`: Em execução
- `concluida`: Finalizada

---

## 🔌 API Endpoints

### Autenticação

#### `POST /login`

Autentica um usuário e retorna seus dados.

**Request:**
```json
{
  "usuario": "admin",
  "senha": "senha123"
}
```

**Response (200):**
```json
{
  "id": 1,
  "nome": "Administrador",
  "usuario": "admin",
  "tipo": "admin"
}
```

**Response (401):**
```json
{
  "error": "Credenciais inválidas"
}
```

---

### Usuários

#### `GET /usuarios`

Lista todos os usuários.

**Response (200):**
```json
[
  {
    "id": 1,
    "nome": "João Silva",
    "usuario": "joao",
    "tipo": "tecnico",
    "created_at": "2024-01-15T10:30:00"
  }
]
```

---

#### `POST /usuarios`

Cria um novo usuário.

**Request:**
```json
{
  "nome": "Maria Santos",
  "usuario": "maria",
  "senha": "senha123",
  "tipo": "tecnico"
}
```

**Response (201):**
```json
{
  "id": 2,
  "nome": "Maria Santos",
  "usuario": "maria",
  "tipo": "tecnico"
}
```

---

#### `PUT /usuarios/<id>`

Atualiza um usuário existente.

**Request:**
```json
{
  "nome": "Maria Santos Silva",
  "tipo": "admin"
}
```

**Response (200):**
```json
{
  "id": 2,
  "nome": "Maria Santos Silva",
  "usuario": "maria",
  "tipo": "admin"
}
```

---

#### `DELETE /usuarios/<id>`

Exclui um usuário.

**Response (200):**
```json
{
  "message": "Usuário excluído com sucesso"
}
```

---

### Peças

#### `GET /peca`

Lista todas as peças.

**Response (200):**
```json
[
  {
    "id": 1,
    "nome": "Parafuso M6",
    "descricao": "Parafuso métrico 6mm",
    "quantidade": 50,
    "quantidade_minima": 10,
    "quantidade_maxima": 100,
    "created_at": "2024-01-15T10:30:00"
  }
]
```

---

#### `POST /peca`

Cria uma nova peça.

**Request:**
```json
{
  "nome": "Porca M6",
  "descricao": "Porca métrica 6mm",
  "quantidade": 30,
  "quantidade_minima": 5,
  "quantidade_maxima": 50
}
```

**Response (201):**
```json
{
  "id": 2,
  "nome": "Porca M6",
  "quantidade": 30,
  "quantidade_minima": 5,
  "quantidade_maxima": 50
}
```

---

#### `PUT /peca/<id>`

Atualiza uma peça existente.

**Request:**
```json
{
  "quantidade": 45,
  "quantidade_minima": 8
}
```

**Response (200):**
```json
{
  "id": 2,
  "nome": "Porca M6",
  "quantidade": 45,
  "quantidade_minima": 8
}
```

---

#### `DELETE /peca/<id>`

Exclui uma peça.

**Response (200):**
```json
{
  "message": "Peça excluída com sucesso"
}
```

---

### Ordens de Serviço

#### `GET /ordemservico`

Lista todas as ordens de serviço.

**Response (200):**
```json
[
  {
    "id": 1,
    "descricao": "Manutenção preventiva",
    "status": "em_andamento",
    "tecnico_id": 2,
    "tecnico_nome": "João Silva",
    "pecas_utilizadas": [
      {"peca_id": 1, "quantidade": 5}
    ],
    "created_at": "2024-01-15T10:30:00"
  }
]
```

---

#### `POST /ordemservico`

Cria uma nova ordem de serviço.

**Request:**
```json
{
  "descricao": "Troca de componentes",
  "status": "pendente",
  "tecnico_id": 2,
  "pecas_utilizadas": [
    {"peca_id": 1, "quantidade": 3},
    {"peca_id": 2, "quantidade": 2}
  ]
}
```

**Response (201):**
```json
{
  "id": 2,
  "descricao": "Troca de componentes",
  "status": "pendente",
  "tecnico_id": 2
}
```

> **Nota:** Ao criar uma ordem, o estoque é **automaticamente atualizado** (subtraindo as peças utilizadas).

---

#### `PUT /ordemservico/<id>`

Atualiza uma ordem de serviço.

**Request:**
```json
{
  "status": "concluida"
}
```

**Response (200):**
```json
{
  "id": 2,
  "status": "concluida"
}
```

---

#### `DELETE /ordemservico/<id>`

Exclui uma ordem de serviço.

**Response (200):**
```json
{
  "message": "Ordem de serviço excluída com sucesso"
}
```

---

### Alertas

#### `GET /estoque/alertas`

Retorna peças com estoque baixo (quantidade <= quantidade_minima).

**Response (200):**
```json
[
  {
    "id": 3,
    "nome": "Arruela M6",
    "quantidade": 2,
    "quantidade_minima": 10,
    "diferenca": -8
  }
]
```

---

#### `GET /notificacoes-estoque`

Retorna notificações de estoque baixo (alias para `/estoque/alertas`).

---

## 🔧 Serviços

### `services/login.py`

Gerencia autenticação de usuários.

**Funções principais:**
- `autenticar_usuario(usuario, senha)`: Valida credenciais

---

### `services/usuario.py`

Gerencia operações CRUD de usuários.

**Funções principais:**
- `listar_usuarios()`: Retorna todos os usuários
- `criar_usuario(dados)`: Cria novo usuário
- `atualizar_usuario(id, dados)`: Atualiza usuário
- `excluir_usuario(id)`: Remove usuário

---

### `services/peca.py`

Gerencia operações CRUD de peças.

**Funções principais:**
- `listar_pecas()`: Retorna todas as peças
- `criar_peca(dados)`: Cria nova peça
- `atualizar_peca(id, dados)`: Atualiza peça
- `excluir_peca(id)`: Remove peça
- `atualizar_estoque(peca_id, quantidade)`: Atualiza quantidade

---

### `services/ordem_servico.py`

Gerencia operações de ordens de serviço.

**Funções principais:**
- `listar_ordens()`: Retorna todas as ordens
- `criar_ordem(dados)`: Cria ordem e atualiza estoque
- `atualizar_ordem(id, dados)`: Atualiza ordem
- `excluir_ordem(id)`: Remove ordem

**Lógica especial:**
- Ao criar ordem, valida se há peças suficientes no estoque
- Atualiza automaticamente o estoque ao criar ordem

---

### `services/alertas.py`

Gerencia alertas de estoque baixo.

**Funções principais:**
- `obter_alertas_estoque()`: Retorna peças com quantidade <= quantidade_minima

---

## 🐳 Deploy

### Docker Compose

O projeto inclui configuração completa para Docker Compose.

**Arquivo `docker-compose.yml`:**

```yaml
version: '3.8'

services:
  db:
    image: postgres:15
    environment:
      POSTGRES_DB: gestao_estoque
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      interval: 5s
      timeout: 5s
      retries: 5

  backend:
    build: ./backend
    ports:
      - "6000:6000"
    environment:
      DATABASE_URL: postgresql://postgres:postgres@db:5432/gestao_estoque
    depends_on:
      db:
        condition: service_healthy
    command: ["./wait-for-db.sh", "db", "python", "wsgi.py"]

volumes:
  postgres_data:
```

### Comandos Úteis

```bash
# Iniciar todos os serviços
docker-compose up -d

# Ver logs
docker-compose logs -f backend

# Parar serviços
docker-compose down

# Rebuild após mudanças
docker-compose up --build

# Acessar shell do container
docker-compose exec backend bash

# Executar migrations
docker-compose exec backend flask db upgrade
```

---

## 🧪 Testes

### Testes Manuais com cURL

#### Testar Login

```bash
curl -X POST http://localhost:6000/login \
  -H "Content-Type: application/json" \
  -d '{"usuario": "admin", "senha": "admin123"}'
```

#### Listar Peças

```bash
curl http://localhost:6000/peca
```

#### Criar Peça

```bash
curl -X POST http://localhost:6000/peca \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "Teste",
    "quantidade": 10,
    "quantidade_minima": 5,
    "quantidade_maxima": 20
  }'
```

### Testes com Postman

1. Importe a collection (se disponível)
2. Configure a variável `base_url` para `http://localhost:6000`
3. Execute os testes

---

## 🔒 Segurança

### Boas Práticas Implementadas

- ✅ Senhas não são retornadas nas respostas da API
- ✅ Validação de dados de entrada
- ✅ Tratamento de erros sem expor detalhes internos
- ✅ CORS configurado adequadamente

### Melhorias Futuras

- 🔄 Implementar JWT para autenticação
- 🔄 Hash de senhas com bcrypt
- 🔄 Rate limiting
- 🔄 Logs de auditoria
- 🔄 Validação de permissões por tipo de usuário

---

## 📊 Monitoramento

### Logs

Os logs são exibidos no console. Para produção, configure logging para arquivo:

```python
import logging

logging.basicConfig(
    filename='app.log',
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s'
)
```

---

## 🛠️ Troubleshooting

### Problema: Banco de dados não conecta

**Solução:**
- Verifique se o PostgreSQL está rodando
- Confirme as credenciais no `.env`
- Teste a conexão: `psql -h localhost -U postgres`

### Problema: Migrations não aplicam

**Solução:**
```bash
docker-compose exec backend flask db stamp head
docker-compose exec backend flask db migrate
docker-compose exec backend flask db upgrade
```

### Problema: Porta 6000 já em uso

**Solução:**
- Altere a porta no `docker-compose.yml`
- Ou mate o processo: `lsof -ti:6000 | xargs kill -9`

---

## 📚 Referências

- [Flask Documentation](https://flask.palletsprojects.com/)
- [SQLAlchemy Documentation](https://docs.sqlalchemy.org/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Docker Documentation](https://docs.docker.com/)

---

## 👥 Equipe de Desenvolvimento

- **Camila Galieta Bernardes** - Backend e Documentação

---

**Versão:** 1.0.0  
**Última atualização:** Novembro 2024
