# 📘 Manual do Usuário
## Sistema de Gestão de Estoque e Manutenção

---

## 📋 Índice

1. [Introdução](#introdução)
2. [Primeiros Passos](#primeiros-passos)
3. [Interface Web](#interface-web)
4. [Aplicativo Mobile](#aplicativo-mobile)
5. [Perguntas Frequentes](#perguntas-frequentes)
6. [Suporte](#suporte)

---

## 🎯 Introdução

### O que é o Sistema?

O **Sistema de Gestão de Estoque e Manutenção** é uma plataforma completa para controlar peças, equipamentos e ordens de serviço. Ele ajuda sua organização a:

- ✅ Controlar entrada e saída de peças
- ✅ Receber alertas quando o estoque está baixo
- ✅ Gerenciar ordens de serviço
- ✅ Acompanhar trabalho dos técnicos
- ✅ Acessar informações de qualquer lugar (web ou celular)

### Quem pode usar?

- **Administradores:** Acesso completo ao sistema
- **Técnicos:** Visualizar e criar ordens de serviço
- **Gestores:** Acompanhar relatórios e estoque

---

## 🚀 Primeiros Passos

### 1. Acessando o Sistema

#### **Via Web (Computador)**
1. Abra seu navegador (Chrome, Firefox, Edge)
2. Digite o endereço: `http://seu-servidor:5173`
3. Você verá a tela de login

#### **Via Mobile (Celular)**
1. Baixe o aplicativo na loja (Android/iOS)
2. Abra o aplicativo
3. Você verá a tela de login

### 2. Fazendo Login

1. Digite seu **nome de usuário**
2. Digite sua **senha**
3. Clique em **"Entrar"**

> 💡 **Primeira vez?** Solicite suas credenciais ao administrador do sistema.

### 3. Esqueci minha senha

Entre em contato com o administrador do sistema para redefinir sua senha.

---

## 💻 Interface Web

### Dashboard (Tela Inicial)

Ao fazer login, você verá o **Dashboard** com:

- 📊 **Resumo do Estoque:** Total de peças cadastradas
- 🔔 **Alertas:** Peças com estoque baixo
- 📋 **Ordens de Serviço:** Ordens em andamento
- 👥 **Usuários:** Total de usuários cadastrados

---

### 📦 Gestão de Peças

#### **Visualizar Peças**

1. Clique em **"Peças"** no menu lateral
2. Você verá a lista de todas as peças cadastradas
3. Use a **barra de busca** para encontrar peças específicas

**Informações exibidas:**
- Nome da peça
- Quantidade atual
- Quantidade mínima
- Quantidade máxima
- Status (🔴 Baixo, 🟢 Normal)

#### **Cadastrar Nova Peça**

1. Na tela de Peças, clique em **"+ Nova Peça"**
2. Preencha o formulário:
   - **Nome:** Nome da peça (ex: "Parafuso M6")
   - **Descrição:** Detalhes da peça (opcional)
   - **Quantidade:** Quantidade inicial
   - **Quantidade Mínima:** Quando alertar (ex: 10)
   - **Quantidade Máxima:** Limite máximo (ex: 100)
3. Clique em **"Salvar"**

> 💡 **Dica:** Configure a quantidade mínima para receber alertas automáticos!

#### **Editar Peça**

1. Na lista de peças, clique no **ícone de editar** (✏️)
2. Modifique as informações necessárias
3. Clique em **"Salvar Alterações"**

#### **Excluir Peça**

1. Na lista de peças, clique no **ícone de excluir** (🗑️)
2. Confirme a exclusão
3. A peça será removida permanentemente

> ⚠️ **Atenção:** Não é possível excluir peças que estão em ordens de serviço ativas.

---

### 🔧 Ordens de Serviço

#### **Visualizar Ordens**

1. Clique em **"Ordens de Serviço"** no menu lateral
2. Você verá todas as ordens cadastradas
3. Use os **filtros** para encontrar ordens específicas:
   - Por status (Pendente, Em Andamento, Concluída)
   - Por técnico
   - Por data

**Informações exibidas:**
- Número da ordem
- Descrição do problema
- Técnico responsável
- Status
- Data de criação
- Peças utilizadas

#### **Criar Nova Ordem de Serviço**

1. Clique em **"+ Nova Ordem"**
2. Preencha o formulário:
   - **Descrição:** Descreva o problema ou serviço
   - **Técnico Responsável:** Selecione da lista
   - **Peças Necessárias:** Selecione e informe quantidades
   - **Status:** Pendente, Em Andamento ou Concluída
3. Clique em **"Criar Ordem"**

> 💡 **Automático:** Quando você cria uma ordem, o estoque é atualizado automaticamente!

#### **Atualizar Status da Ordem**

1. Clique na ordem desejada
2. Altere o **Status**:
   - **Pendente:** Aguardando início
   - **Em Andamento:** Técnico trabalhando
   - **Concluída:** Serviço finalizado
3. Clique em **"Salvar"**

#### **Excluir Ordem**

1. Clique no **ícone de excluir** (🗑️) na ordem
2. Confirme a exclusão
3. A ordem será removida

> ⚠️ **Atenção:** Ao excluir uma ordem, as peças NÃO retornam ao estoque automaticamente.

---

### 🔔 Alertas de Estoque

O sistema monitora automaticamente o estoque e exibe alertas quando:

- Uma peça atinge a **quantidade mínima**
- Uma peça está **abaixo** da quantidade mínima

#### **Visualizar Alertas**

1. Clique em **"Alertas"** no menu lateral
2. Você verá todas as peças em situação crítica
3. Peças são destacadas em **vermelho** 🔴

#### **Resolver Alertas**

1. Identifique a peça com estoque baixo
2. Vá para **"Peças"**
3. Edite a peça e aumente a quantidade
4. O alerta desaparecerá automaticamente

---

### 👥 Gestão de Usuários

> 🔒 **Apenas Administradores** têm acesso a esta funcionalidade.

#### **Visualizar Usuários**

1. Clique em **"Usuários"** no menu lateral
2. Você verá todos os usuários cadastrados

#### **Cadastrar Novo Usuário**

1. Clique em **"+ Novo Usuário"**
2. Preencha:
   - **Nome:** Nome completo
   - **Nome de Usuário:** Login (sem espaços)
   - **Senha:** Senha inicial
   - **Tipo:** Administrador ou Técnico
3. Clique em **"Cadastrar"**

#### **Editar Usuário**

1. Clique no **ícone de editar** (✏️)
2. Modifique as informações
3. Clique em **"Salvar"**

#### **Excluir Usuário**

1. Clique no **ícone de excluir** (🗑️)
2. Confirme a exclusão

---

## 📱 Aplicativo Mobile

### Instalação

1. **Android:** Baixe na Google Play Store
2. **iOS:** Baixe na App Store
3. Instale e abra o aplicativo

### Login

1. Digite seu **usuário** e **senha**
2. Toque em **"Entrar"**

### Tela Inicial

Após o login, você verá:
- 📋 **Ordens de Serviço:** Lista de ordens
- ➕ **Criar Ordem:** Botão flutuante

### Criar Ordem de Serviço (Mobile)

1. Toque no **botão "+"** (canto inferior direito)
2. Preencha:
   - **Descrição:** Descreva o problema
   - **Técnico:** Selecione o responsável
   - **Peças:** Selecione as peças necessárias
3. Toque em **"Criar"**

### Visualizar Detalhes da Ordem

1. Toque em uma ordem da lista
2. Você verá todos os detalhes:
   - Descrição completa
   - Técnico responsável
   - Peças utilizadas
   - Status
   - Data de criação

### Atualizar Ordem

1. Abra a ordem
2. Toque em **"Editar"**
3. Modifique as informações
4. Toque em **"Salvar"**

### Logout

1. Toque no **ícone de perfil**
2. Toque em **"Sair"**

---

## ❓ Perguntas Frequentes

### **1. Como sei se uma peça está acabando?**
O sistema exibe alertas automáticos no Dashboard e na seção "Alertas" quando uma peça atinge a quantidade mínima.

### **2. Posso usar o sistema offline?**
Não. O sistema requer conexão com a internet para sincronizar dados em tempo real.

### **3. Quantos usuários podem usar ao mesmo tempo?**
O sistema suporta múltiplos usuários simultâneos sem problemas.

### **4. Como faço para imprimir relatórios?**
Use a função de impressão do navegador (Ctrl+P ou Cmd+P) em qualquer tela.

### **5. Posso acessar de qualquer navegador?**
Sim! O sistema funciona em Chrome, Firefox, Safari, Edge e outros navegadores modernos.

### **6. O que acontece se eu excluir uma peça por engano?**
A exclusão é permanente. Entre em contato com o administrador para restaurar dados do backup.

### **7. Como altero minha senha?**
Atualmente, apenas administradores podem alterar senhas. Entre em contato com o suporte.

### **8. O aplicativo mobile tem todas as funcionalidades do web?**
Atualmente, o mobile possui funcionalidades essenciais (ordens de serviço). Mais recursos serão adicionados em futuras versões.

### **9. Posso usar no tablet?**
Sim! Tanto a versão web quanto o aplicativo mobile funcionam em tablets.

### **10. Como reporto um problema ou bug?**
Entre em contato com o suporte técnico (veja seção abaixo).

---

## 🆘 Suporte

### Precisa de Ajuda?

**Equipe de Desenvolvimento:**
- **Backend e Documentação:** Camila Galieta Bernardes
- **Mobile:** Cristian Moises Brunone Cordero
- **Frontend:** Marcio Kiyoshi Shikasho
- **Frontend e Documentação:** Adriano Felipe Alves dos Reis

**Instituição:** SENAI SC - Campus Florianópolis

### Reportar Problemas

Se encontrar algum problema:
1. Anote o que estava fazendo quando o erro ocorreu
2. Tire um print da tela (se possível)
3. Entre em contato com o administrador do sistema

---

## 📚 Recursos Adicionais

### Vídeos Tutoriais
- 🎥 Como criar uma ordem de serviço
- 🎥 Como cadastrar peças
- 🎥 Como gerenciar usuários

### Documentação Técnica
Para desenvolvedores e administradores de sistema, consulte:
- `documentacao-backend.md`
- `documentacao-web.md`
- `documentacao-mobile.md`

---

## 📝 Notas da Versão

**Versão Atual:** 1.0.0

**Funcionalidades Disponíveis:**
- ✅ Gestão completa de peças
- ✅ Ordens de serviço
- ✅ Alertas automáticos
- ✅ Gestão de usuários
- ✅ Interface web responsiva
- ✅ Aplicativo mobile (Android/iOS)

**Próximas Funcionalidades:**
- 🔄 Gestão de estoque no mobile
- 🔔 Notificações push
- 📊 Relatórios avançados
- 📸 Upload de fotos nas ordens
- 🗺️ Geolocalização de técnicos

---

**Obrigado por usar nosso sistema! 🚀**
