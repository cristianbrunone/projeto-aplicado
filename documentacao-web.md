# 🌐 Documentação Técnica - Frontend Web
## Sistema de Gestão de Estoque e Manutenção

---

## 📋 Índice

1. [Visão Geral](#visão-geral)
2. [Arquitetura](#arquitetura)
3. [Tecnologias](#tecnologias)
4. [Instalação e Configuração](#instalação-e-configuração)
5. [Estrutura do Projeto](#estrutura-do-projeto)
6. [Componentes](#componentes)
7. [Páginas](#páginas)
8. [Serviços e API](#serviços-e-api)
9. [Roteamento](#roteamento)
10. [Estilização](#estilização)
11. [Deploy](#deploy)

---

## 🎯 Visão Geral

O frontend web é uma **Single Page Application (SPA)** desenvolvida em **React.js** com **Vite** como build tool. Oferece uma interface moderna, responsiva e intuitiva para gerenciamento de estoque e ordens de serviço.

### Características Principais

- ✅ Interface moderna e responsiva
- ✅ Componentização reutilizável
- ✅ Integração completa com API REST
- ✅ Navegação com React Router
- ✅ Gerenciamento de estado com Context API
- ✅ Feedback visual em tempo real
- ✅ Validação de formulários
- ✅ Design system consistente

---

## 🏗️ Arquitetura

### Padrão de Arquitetura

O frontend segue uma arquitetura baseada em componentes:

```
┌─────────────────────────────────┐
│      Pages (Páginas)            │  ← Rotas principais
├─────────────────────────────────┤
│      Components (Componentes)   │  ← UI reutilizável
├─────────────────────────────────┤
│      Services (API)             │  ← Comunicação com backend
├─────────────────────────────────┤
│      Contexts (Estado)          │  ← Estado global
└─────────────────────────────────┘
```

### Fluxo de Dados

```
User Interaction → Component → Service → API (Backend)
                                            ↓
User Interface ← Component ← Service ← Response
```

---

## 💻 Tecnologias

| Tecnologia | Versão | Propósito |
|------------|--------|-----------|
| **React** | 18.2+ | Biblioteca UI |
| **Vite** | 5.0+ | Build tool e dev server |
| **React Router** | 6.20+ | Navegação SPA |
| **Axios** | 1.6+ | Cliente HTTP |
| **Tailwind CSS** | 3.4+ | Framework CSS |
| **Lucide React** | - | Ícones |

---

## 🚀 Instalação e Configuração

### Pré-requisitos

- Node.js 18+
- npm ou yarn

### Instalação

```bash
# Navegue até o diretório frontend
cd frontend

# Instale as dependências
npm install

# Inicie o servidor de desenvolvimento
npm run dev

# O frontend estará disponível em http://localhost:5173
```

### Variáveis de Ambiente

Crie arquivos de ambiente:

**`.env.development`:**
```env
VITE_API_URL=http://localhost:6000
```

**`.env.production`:**
```env
VITE_API_URL=https://api.seudominio.com
```

---

## 📁 Estrutura do Projeto

```
frontend/
├── public/                    # Arquivos estáticos
├── src/
│   ├── components/           # Componentes reutilizáveis
│   │   ├── AlertCard.jsx
│   │   ├── Header.jsx
│   │   ├── Sidebar.jsx
│   │   ├── OrderCard.jsx
│   │   ├── PartCard.jsx
│   │   └── UserCard.jsx
│   ├── contexts/             # Contextos React
│   │   └── AuthContext.jsx
│   ├── pages/                # Páginas/Rotas
│   │   ├── Dashboard.jsx
│   │   ├── Login.jsx
│   │   ├── Parts.jsx
│   │   ├── Orders.jsx
│   │   ├── Users.jsx
│   │   └── Alerts.jsx
│   ├── services/             # Serviços de API
│   │   ├── api.js
│   │   ├── authService.js
│   │   ├── partService.js
│   │   ├── orderService.js
│   │   └── userService.js
│   ├── utils/                # Utilitários
│   │   └── helpers.js
│   ├── App.jsx               # Componente raiz
│   ├── main.jsx              # Entry point
│   ├── index.css             # Estilos globais
│   └── config.js             # Configurações
├── index.html
├── package.json
├── vite.config.js
└── tailwind.config.js
```

---

## 🧩 Componentes

### 1. Header

Cabeçalho da aplicação com informações do usuário.

**Localização:** `src/components/Header.jsx`

**Props:**
- `userName` (string): Nome do usuário logado
- `userType` (string): Tipo do usuário (admin/tecnico)

**Uso:**
```jsx
<Header userName="João Silva" userType="admin" />
```

---

### 2. Sidebar

Menu lateral de navegação.

**Localização:** `src/components/Sidebar.jsx`

**Features:**
- Links para todas as páginas
- Destaque da página ativa
- Ícones intuitivos
- Botão de logout

**Uso:**
```jsx
<Sidebar />
```

---

### 3. PartCard

Card para exibição de peças.

**Localização:** `src/components/PartCard.jsx`

**Props:**
- `part` (object): Dados da peça
  - `id` (number)
  - `nome` (string)
  - `quantidade` (number)
  - `quantidade_minima` (number)
  - `quantidade_maxima` (number)
- `onEdit` (function): Callback ao editar
- `onDelete` (function): Callback ao excluir

**Uso:**
```jsx
<PartCard 
  part={partData} 
  onEdit={handleEdit}
  onDelete={handleDelete}
/>
```

---

### 4. OrderCard

Card para exibição de ordens de serviço.

**Localização:** `src/components/OrderCard.jsx`

**Props:**
- `order` (object): Dados da ordem
  - `id` (number)
  - `descricao` (string)
  - `status` (string)
  - `tecnico_nome` (string)
  - `created_at` (string)
- `onStatusChange` (function): Callback ao mudar status
- `onDelete` (function): Callback ao excluir

**Uso:**
```jsx
<OrderCard 
  order={orderData}
  onStatusChange={handleStatusChange}
  onDelete={handleDelete}
/>
```

---

### 5. AlertCard

Card para exibição de alertas de estoque.

**Localização:** `src/components/AlertCard.jsx`

**Props:**
- `alert` (object): Dados do alerta
  - `id` (number)
  - `nome` (string)
  - `quantidade` (number)
  - `quantidade_minima` (number)
  - `diferenca` (number)

**Uso:**
```jsx
<AlertCard alert={alertData} />
```

---

### 6. UserCard

Card para exibição de usuários.

**Localização:** `src/components/UserCard.jsx`

**Props:**
- `user` (object): Dados do usuário
  - `id` (number)
  - `nome` (string)
  - `usuario` (string)
  - `tipo` (string)
- `onEdit` (function): Callback ao editar
- `onDelete` (function): Callback ao excluir

**Uso:**
```jsx
<UserCard 
  user={userData}
  onEdit={handleEdit}
  onDelete={handleDelete}
/>
```

---

## 📄 Páginas

### 1. Login (`/login`)

Página de autenticação.

**Localização:** `src/pages/Login.jsx`

**Features:**
- Formulário de login
- Validação de campos
- Feedback de erro
- Redirecionamento após login

**Fluxo:**
1. Usuário insere credenciais
2. Submit chama `authService.login()`
3. Se sucesso, salva dados no `AuthContext`
4. Redireciona para `/dashboard`

---

### 2. Dashboard (`/dashboard`)

Tela inicial com visão geral do sistema.

**Localização:** `src/pages/Dashboard.jsx`

**Features:**
- Cards com estatísticas:
  - Total de peças
  - Alertas de estoque
  - Ordens em andamento
  - Total de usuários
- Acesso rápido às principais funcionalidades

**Dados exibidos:**
```jsx
{
  totalParts: 150,
  lowStockAlerts: 5,
  activeOrders: 12,
  totalUsers: 8
}
```

---

### 3. Parts (`/parts`)

Gestão completa de peças.

**Localização:** `src/pages/Parts.jsx`

**Features:**
- Listagem de peças
- Busca e filtros
- Modal de cadastro
- Modal de edição
- Exclusão com confirmação
- Indicadores visuais de estoque baixo

**Operações:**
- **Listar:** `GET /peca`
- **Criar:** `POST /peca`
- **Editar:** `PUT /peca/:id`
- **Excluir:** `DELETE /peca/:id`

---

### 4. Orders (`/orders`)

Gestão de ordens de serviço.

**Localização:** `src/pages/Orders.jsx`

**Features:**
- Listagem de ordens
- Filtros por status e técnico
- Modal de criação
- Atualização de status
- Visualização de detalhes
- Exclusão

**Status possíveis:**
- `pendente` (🟡)
- `em_andamento` (🔵)
- `concluida` (🟢)

---

### 5. Users (`/users`)

Gestão de usuários (apenas admin).

**Localização:** `src/pages/Users.jsx`

**Features:**
- Listagem de usuários
- Cadastro de novos usuários
- Edição de perfis
- Exclusão
- Diferenciação visual por tipo (admin/tecnico)

**Restrição:**
- Apenas usuários tipo `admin` podem acessar

---

### 6. Alerts (`/alerts`)

Visualização de alertas de estoque.

**Localização:** `src/pages/Alerts.jsx`

**Features:**
- Lista de peças com estoque baixo
- Destaque visual (vermelho)
- Informação de déficit
- Link direto para editar peça

---

## 🔌 Serviços e API

### Configuração Base

**Localização:** `src/services/api.js`

```javascript
import axios from 'axios';

const api = axios.create({
  baseURL: import.meta.env.VITE_API_URL || 'http://localhost:6000',
  headers: {
    'Content-Type': 'application/json'
  }
});

export default api;
```

---

### authService

**Localização:** `src/services/authService.js`

**Métodos:**

```javascript
// Login
const login = async (usuario, senha) => {
  const response = await api.post('/login', { usuario, senha });
  return response.data;
};

// Logout
const logout = () => {
  localStorage.removeItem('user');
};

// Obter usuário atual
const getCurrentUser = () => {
  return JSON.parse(localStorage.getItem('user'));
};
```

---

### partService

**Localização:** `src/services/partService.js`

**Métodos:**

```javascript
// Listar todas as peças
const getAll = async () => {
  const response = await api.get('/peca');
  return response.data;
};

// Criar peça
const create = async (partData) => {
  const response = await api.post('/peca', partData);
  return response.data;
};

// Atualizar peça
const update = async (id, partData) => {
  const response = await api.put(`/peca/${id}`, partData);
  return response.data;
};

// Excluir peça
const remove = async (id) => {
  const response = await api.delete(`/peca/${id}`);
  return response.data;
};
```

---

### orderService

**Localização:** `src/services/orderService.js`

**Métodos:**

```javascript
// Listar ordens
const getAll = async () => {
  const response = await api.get('/ordemservico');
  return response.data;
};

// Criar ordem
const create = async (orderData) => {
  const response = await api.post('/ordemservico', orderData);
  return response.data;
};

// Atualizar ordem
const update = async (id, orderData) => {
  const response = await api.put(`/ordemservico/${id}`, orderData);
  return response.data;
};

// Excluir ordem
const remove = async (id) => {
  const response = await api.delete(`/ordemservico/${id}`);
  return response.data;
};
```

---

### userService

**Localização:** `src/services/userService.js`

**Métodos:**

```javascript
// Listar usuários
const getAll = async () => {
  const response = await api.get('/usuarios');
  return response.data;
};

// Criar usuário
const create = async (userData) => {
  const response = await api.post('/usuarios', userData);
  return response.data;
};

// Atualizar usuário
const update = async (id, userData) => {
  const response = await api.put(`/usuarios/${id}`, userData);
  return response.data;
};

// Excluir usuário
const remove = async (id) => {
  const response = await api.delete(`/usuarios/${id}`);
  return response.data;
};
```

---

## 🛣️ Roteamento

**Localização:** `src/App.jsx`

```jsx
import { BrowserRouter, Routes, Route, Navigate } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/login" element={<Login />} />
        <Route path="/dashboard" element={<PrivateRoute><Dashboard /></PrivateRoute>} />
        <Route path="/parts" element={<PrivateRoute><Parts /></PrivateRoute>} />
        <Route path="/orders" element={<PrivateRoute><Orders /></PrivateRoute>} />
        <Route path="/users" element={<PrivateRoute><Users /></PrivateRoute>} />
        <Route path="/alerts" element={<PrivateRoute><Alerts /></PrivateRoute>} />
        <Route path="/" element={<Navigate to="/dashboard" />} />
      </Routes>
    </BrowserRouter>
  );
}
```

### Rotas Protegidas

```jsx
const PrivateRoute = ({ children }) => {
  const { user } = useAuth();
  return user ? children : <Navigate to="/login" />;
};
```

---

## 🎨 Estilização

### Tailwind CSS

O projeto utiliza **Tailwind CSS** para estilização.

**Configuração:** `tailwind.config.js`

```javascript
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx}"
  ],
  theme: {
    extend: {
      colors: {
        primary: '#3b82f6',
        secondary: '#64748b',
        success: '#10b981',
        warning: '#f59e0b',
        danger: '#ef4444'
      }
    }
  },
  plugins: []
}
```

### Classes Comuns

```css
/* Botões */
.btn-primary: bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded
.btn-danger: bg-red-600 hover:bg-red-700 text-white px-4 py-2 rounded

/* Cards */
.card: bg-white shadow-md rounded-lg p-6

/* Inputs */
.input: border border-gray-300 rounded px-3 py-2 focus:outline-none focus:ring-2
```

---

## 🐳 Deploy

### Build para Produção

```bash
# Build
npm run build

# Preview do build
npm run preview
```

### Deploy com Docker

**Dockerfile:**

```dockerfile
FROM node:18-alpine as build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

**Build e Run:**

```bash
docker build -t frontend-gestao .
docker run -p 80:80 frontend-gestao
```

### Deploy com Firebase Hosting

```bash
# Install Firebase CLI
npm install -g firebase-tools

# Login
firebase login

# Initialize
firebase init hosting

# Deploy
firebase deploy
```

---

## 🧪 Testes

### Testes Manuais

1. **Login:**
   - Testar com credenciais válidas
   - Testar com credenciais inválidas
   - Verificar redirecionamento

2. **CRUD de Peças:**
   - Criar peça
   - Editar peça
   - Excluir peça
   - Verificar validações

3. **Ordens de Serviço:**
   - Criar ordem
   - Atualizar status
   - Verificar atualização de estoque

4. **Responsividade:**
   - Testar em diferentes resoluções
   - Verificar mobile (375px)
   - Verificar tablet (768px)
   - Verificar desktop (1920px)

---

## 🔒 Segurança

### Boas Práticas

- ✅ Validação de inputs
- ✅ Sanitização de dados
- ✅ Proteção de rotas privadas
- ✅ Não expor dados sensíveis no localStorage

### Melhorias Futuras

- 🔄 Implementar JWT
- 🔄 HTTPS obrigatório
- 🔄 Content Security Policy
- 🔄 Rate limiting no frontend

---

## 🛠️ Troubleshooting

### Problema: API não conecta

**Solução:**
- Verifique `VITE_API_URL` no `.env`
- Confirme que o backend está rodando
- Verifique CORS no backend

### Problema: Build falha

**Solução:**
```bash
rm -rf node_modules package-lock.json
npm install
npm run build
```

### Problema: Rota não encontrada após refresh

**Solução:**
Configure o servidor para redirecionar todas as rotas para `index.html` (SPA).

**Nginx:**
```nginx
location / {
  try_files $uri $uri/ /index.html;
}
```

---

## 📚 Referências

- [React Documentation](https://react.dev/)
- [Vite Documentation](https://vitejs.dev/)
- [React Router Documentation](https://reactrouter.com/)
- [Tailwind CSS Documentation](https://tailwindcss.com/)
- [Axios Documentation](https://axios-http.com/)

---

## 👥 Equipe de Desenvolvimento

- **Marcio Kiyoshi Shikasho** - Frontend
- **Adriano Felipe Alves dos Reis** - Frontend e Documentação

---

**Versão:** 1.0.0  
**Última atualização:** Novembro 2024
