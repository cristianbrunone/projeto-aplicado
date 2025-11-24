# 🎓 Apresentação Final - 15 Minutos
## Sistema de Gestão de Estoque e Manutenção

---

## 👥 Divisão de Tempo e Responsabilidades

| Apresentador | Tema | Tempo | Slides |
|--------------|------|-------|--------|
| **Pessoa 1** | Introdução + Contexto + Backend | 4 min | 1-8 |
| **Pessoa 2** | Frontend Web - Parte 1 | 4 min | 9-14 |
| **Pessoa 3** | Frontend Web - Parte 2 | 3 min | 15-18 |
| **Pessoa 4** | Mobile + Conclusão | 4 min | 19-25 |

**Total:** 15 minutos

---

## 📑 Estrutura da Apresentação

### **PESSOA 1: Introdução + Contexto + Backend** (4 minutos)

#### **Slide 1: Capa** (20 segundos)
- Título: "Sistema de Gestão de Estoque e Manutenção"
- Subtítulo: "Projeto Aplicado IV - SENAI SC"
- Equipe: Camila, Cristian, Marcio, Adriano

**Fala:**
> "Boa tarde! Vamos apresentar nosso projeto final: um sistema completo de gestão de estoque e manutenção desenvolvido para atender uma demanda real do SENAI ES."

---

#### **Slide 2: O Problema** (30 segundos)
- Contexto da demanda (SENAI ES)
- Problemas identificados:
  - Controle manual de estoque
  - Falta de alertas automáticos
  - Dificuldade em rastrear ordens de serviço
  - Ausência de mobilidade

**Fala:**
> "O SENAI ES enfrentava desafios no controle de peças e manutenção. O processo manual gerava perda de tempo, falta de visibilidade do estoque e dificuldade no acompanhamento de ordens de serviço."

---

#### **Slide 3: A Solução** (30 segundos)
- Sistema integrado com 3 plataformas
- Diagrama: Backend ↔ Web ↔ Mobile
- Principais funcionalidades

**Fala:**
> "Nossa solução é um sistema completo com backend robusto, interface web moderna e aplicativo mobile, todos integrados e sincronizados em tempo real."

---

#### **Slide 4: Arquitetura Geral** (40 segundos)
- Diagrama de arquitetura
- Tecnologias principais
- Fluxo de dados

**Fala:**
> "Adotamos uma arquitetura moderna: API RESTful em Python, frontend em React, mobile em Flutter, tudo orquestrado com Docker e banco PostgreSQL."

---

#### **Slide 5: Backend - Tecnologias** (30 segundos)
- Python 3.11
- Flask (framework web)
- SQLAlchemy (ORM)
- PostgreSQL
- Docker

**Fala:**
> "O backend foi desenvolvido em Python com Flask, utilizando SQLAlchemy para ORM e PostgreSQL como banco de dados. Toda a aplicação é containerizada com Docker."

---

#### **Slide 6: Backend - API RESTful** (40 segundos)
- Endpoints principais:
  - `/login` - Autenticação
  - `/usuarios` - Gestão de usuários
  - `/peca` - Gestão de peças
  - `/ordemservico` - Ordens de serviço
  - `/estoque/alertas` - Alertas automáticos

**Fala:**
> "A API oferece endpoints completos para autenticação, gestão de usuários, peças, ordens de serviço e um sistema inteligente de alertas de estoque."

---

#### **Slide 7: Backend - Funcionalidades** (30 segundos)
- CRUD completo para todas as entidades
- Sistema de autenticação
- Validações de dados
- Alertas automáticos (estoque < mínimo)
- Logs e tratamento de erros

**Fala:**
> "Implementamos CRUD completo, autenticação segura, validações robustas e um sistema de alertas que notifica automaticamente quando o estoque atinge níveis críticos."

---

#### **Slide 8: Backend - Deploy** (20 segundos)
- Docker Compose
- Migrations automáticas
- Variáveis de ambiente
- Fácil escalabilidade

**Fala:**
> "O deploy é simplificado com Docker Compose. Basta um comando para subir toda a infraestrutura, incluindo banco de dados e migrations automáticas."

---

### **PESSOA 2: Frontend Web - Parte 1** (4 minutos)

#### **Slide 9: Frontend Web - Visão Geral** (30 segundos)
- React.js + Vite
- Interface moderna e responsiva
- Componentização
- React Router para navegação

**Fala:**
> "O frontend web foi desenvolvido em React com Vite, proporcionando uma interface moderna, rápida e totalmente responsiva. Utilizamos componentização para reutilização de código."

---

#### **Slide 10: Dashboard Principal** (40 segundos)
- Screenshot do dashboard
- Visão geral do sistema
- Cards informativos
- Navegação intuitiva

**Fala:**
> "Esta é a tela principal. O dashboard oferece uma visão completa do sistema com informações em tempo real sobre estoque, ordens de serviço e alertas."

**[DEMO AO VIVO - mostrar dashboard]**

---

#### **Slide 11: Gestão de Peças** (50 segundos)
- Screenshot da listagem de peças
- Funcionalidades:
  - Listagem com busca e filtros
  - Cadastro de novas peças
  - Edição e exclusão
  - Controle de quantidade mín/máx

**Fala:**
> "A gestão de peças permite cadastrar, editar e excluir itens do estoque. Cada peça tem quantidade mínima e máxima configurável, gerando alertas automáticos."

**[DEMO AO VIVO - criar uma peça]**

---

#### **Slide 12: Sistema de Alertas** (40 segundos)
- Screenshot de alertas
- Notificações visuais
- Lista de peças em estoque baixo
- Destaque visual (cores, badges)

**Fala:**
> "O sistema monitora constantemente o estoque e exibe alertas visuais quando peças atingem o nível mínimo. Isso evita falta de materiais."

**[DEMO AO VIVO - mostrar alertas]**

---

#### **Slide 13: Ordens de Serviço - Listagem** (40 segundos)
- Screenshot da listagem
- Status das ordens
- Filtros por técnico, status
- Informações resumidas

**Fala:**
> "As ordens de serviço podem ser visualizadas, filtradas por status ou técnico, e acompanhadas em tempo real."

**[DEMO AO VIVO - navegar pelas ordens]**

---

#### **Slide 14: Ordens de Serviço - Criação** (40 segundos)
- Screenshot do formulário
- Campos principais:
  - Descrição
  - Técnico responsável
  - Peças utilizadas
  - Status

**Fala:**
> "A criação de ordens é simples: descrevemos o problema, atribuímos um técnico, selecionamos as peças necessárias e o sistema atualiza o estoque automaticamente."

**[DEMO AO VIVO - criar ordem de serviço]**

---

### **PESSOA 3: Frontend Web - Parte 2** (3 minutos)

#### **Slide 15: Gestão de Usuários** (40 segundos)
- Screenshot da listagem de usuários
- Funcionalidades:
  - Cadastro de técnicos e administradores
  - Edição de perfis
  - Controle de permissões

**Fala:**
> "O sistema permite gerenciar usuários com diferentes níveis de acesso. Podemos cadastrar técnicos, administradores e controlar suas permissões."

**[DEMO AO VIVO - mostrar listagem]**

---

#### **Slide 16: Responsividade** (30 segundos)
- Screenshots em diferentes resoluções
- Desktop, tablet, mobile
- Adaptação automática

**Fala:**
> "A interface é totalmente responsiva, adaptando-se automaticamente a diferentes tamanhos de tela, desde desktops até tablets."

**[DEMO AO VIVO - redimensionar janela]**

---

#### **Slide 17: Tecnologias Frontend** (50 segundos)
- React.js 18
- Vite (build tool)
- React Router (navegação)
- Axios (HTTP client)
- Tailwind CSS (estilização)
- Componentização modular

**Fala:**
> "Utilizamos as tecnologias mais modernas: React 18, Vite para builds rápidos, React Router para navegação, Axios para comunicação com API e Tailwind CSS para estilização eficiente."

---

#### **Slide 18: Integração com Backend** (40 segundos)
- Fluxo de comunicação
- Axios interceptors
- Tratamento de erros
- Loading states
- Feedback visual

**Fala:**
> "A integração com o backend é feita via Axios, com interceptors para autenticação, tratamento de erros robusto e feedback visual em todas as operações."

---

### **PESSOA 4: Mobile + Conclusão** (4 minutos)

#### **Slide 19: Mobile - Visão Geral** (30 segundos)
- Flutter + Dart
- Multiplataforma (Android/iOS)
- Arquitetura MVVM
- Riverpod (state management)

**Fala:**
> "O aplicativo mobile foi desenvolvido em Flutter, permitindo deploy em Android e iOS com um único código. Utilizamos arquitetura MVVM e Riverpod para gerenciamento de estado."

---

#### **Slide 20: Mobile - Arquitetura** (40 segundos)
- Diagrama de camadas:
  - Presentation (Views)
  - ViewModel
  - Domain (Models, Repository)
  - Data (API Services)

**Fala:**
> "Seguimos Clean Architecture com separação clara de responsabilidades: camada de apresentação, ViewModels, domínio e dados. Isso garante código testável e manutenível."

---

#### **Slide 21: Mobile - Funcionalidades Implementadas** (50 segundos)
- ✅ Autenticação
- ✅ Listagem de ordens de serviço
- ✅ Criação de ordens
- ✅ Visualização de detalhes
- ✅ Sincronização em tempo real

**Fala:**
> "O app mobile já possui autenticação completa, listagem e criação de ordens de serviço, tudo sincronizado em tempo real com o backend."

**[DEMO AO VIVO - mostrar app no emulador/dispositivo]**

---

#### **Slide 22: Mobile - Demonstração** (60 segundos)
- Login
- Dashboard
- Criar ordem de serviço
- Listar ordens

**Fala:**
> "Vamos ver o app funcionando: fazemos login, acessamos o dashboard, criamos uma nova ordem de serviço e visualizamos todas as ordens em andamento."

**[DEMO AO VIVO - navegação completa]**

---

#### **Slide 23: Funcionalidades Futuras** (30 segundos)
- 🔄 Gestão de estoque no mobile
- 🔔 Notificações push
- 📊 Relatórios e gráficos
- 📸 Upload de fotos nas ordens
- 🗺️ Geolocalização de técnicos

**Fala:**
> "Já planejamos expansões futuras: gestão completa de estoque no mobile, notificações push, relatórios com gráficos, upload de fotos e geolocalização de técnicos."

---

#### **Slide 24: Resultados e Impacto** (40 segundos)
- ✅ Sistema completo e funcional
- ✅ 3 plataformas integradas
- ✅ Arquitetura profissional
- ✅ Pronto para produção
- ✅ Atende demanda real do SENAI

**Fala:**
> "Entregamos um sistema completo, com três plataformas integradas, arquitetura profissional e pronto para uso em produção. Atendemos plenamente a demanda do SENAI ES."

---

#### **Slide 25: Encerramento** (30 segundos)
- Agradecimentos
- Equipe:
  - Camila Galieta Bernardes - Backend e Documentação
  - Cristian Moises Brunone Cordero - Mobile
  - Marcio Kiyoshi Shikasho - Frontend
  - Adriano Felipe Alves dos Reis - Frontend e Documentação
- SENAI SC - Campus Florianópolis
- Perguntas?

**Fala:**
> "Agradecemos a atenção! Este projeto representa nosso aprendizado e dedicação ao longo do curso. Estamos à disposição para perguntas."

---

## 🎯 Dicas para a Apresentação

### Preparação
- [ ] Ensaiar a apresentação completa pelo menos 3 vezes
- [ ] Cronometrar cada parte (usar timer)
- [ ] Testar todas as demos ao vivo
- [ ] Preparar dados de exemplo realistas
- [ ] Ter backup de screenshots caso demo falhe
- [ ] Testar projetor/tela com antecedência

### Durante a Apresentação
- [ ] Falar de forma clara e pausada
- [ ] Manter contato visual com a banca
- [ ] Usar apontador laser para destacar elementos
- [ ] Não ler slides (usar como apoio)
- [ ] Demonstrar entusiasmo e confiança
- [ ] Respeitar o tempo de cada apresentador

### Transições entre Apresentadores
- [ ] Pessoa 1 → Pessoa 2: "Agora, [nome] vai demonstrar o frontend web"
- [ ] Pessoa 2 → Pessoa 3: "Continuando com mais funcionalidades do web..."
- [ ] Pessoa 3 → Pessoa 4: "[Nome] vai apresentar o aplicativo mobile"

### Possíveis Perguntas da Banca
- **Sobre escalabilidade:** "Como o sistema se comporta com muitos usuários?"
- **Sobre segurança:** "Como é feita a autenticação?"
- **Sobre testes:** "Vocês implementaram testes automatizados?"
- **Sobre deploy:** "Como seria o deploy em produção?"
- **Sobre desafios:** "Qual foi o maior desafio técnico?"

---

## 📊 Checklist Final

### Antes da Apresentação
- [ ] Slides prontos e revisados
- [ ] Demos testadas e funcionando
- [ ] Banco de dados populado com dados de exemplo
- [ ] Backend rodando
- [ ] Frontend rodando
- [ ] Mobile rodando (emulador ou dispositivo)
- [ ] Backup de screenshots
- [ ] Cronômetro preparado
- [ ] Água para os apresentadores

### Material de Apoio
- [ ] Slides em PDF (backup)
- [ ] Link do repositório GitHub
- [ ] Documentação impressa (opcional)
- [ ] Cartões com pontos-chave (opcional)

---

**Boa sorte na apresentação! Vocês estão preparados! 🚀**
