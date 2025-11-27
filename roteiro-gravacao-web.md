# 🎥 Roteiro de Gravação - Frontend Web
## Sistema de Gestão de Estoque e Manutenção

---

## ⏱️ Tempo Sugerido: 5-7 minutos

---

## 🎬 Preparação Antes de Gravar

### Checklist Técnico
- [ ] Backend rodando (`docker-compose up` ou `python wsgi.py`)
- [ ] Frontend rodando (`npm run dev`)
- [ ] Banco de dados populado com dados de exemplo
- [ ] Navegador limpo (sem abas desnecessárias)
- [ ] Resolução da tela: 1920x1080 (Full HD)
- [ ] Zoom do navegador: 100%
- [ ] Extensões do navegador desabilitadas (ou modo anônimo)
- [ ] Notificações do sistema desabilitadas

### Dados de Exemplo para Preparar

**Usuários:**
- Admin: `admin` / `admin123`
- Técnico 1: `joao` / `senha123`
- Técnico 2: `maria` / `senha123`

**Peças:**
- 5-10 peças cadastradas
- Pelo menos 2 com estoque baixo (para mostrar alertas)
- Exemplos: Parafuso M6, Porca M8, Arruela, Rolamento, etc.

**Ordens de Serviço:**
- 3-5 ordens em diferentes status
- Pelo menos uma de cada: Pendente, Em Andamento, Concluída

---

## 📝 Roteiro de Gravação

### **[0:00 - 0:30] Introdução** (30 segundos)

**O que mostrar:**
- Tela inicial do navegador

**O que falar:**
> "Olá! Vou apresentar o frontend web do nosso Sistema de Gestão de Estoque e Manutenção. Desenvolvido em React com Vite, nossa aplicação oferece uma interface moderna e intuitiva para gerenciar peças, ordens de serviço e usuários. Vamos começar pelo login."

**Ação:**
- Mostrar URL na barra de endereço: `http://localhost:5173`

---

### **[0:30 - 1:15] Login e Dashboard** (45 segundos)

**O que mostrar:**
1. Tela de login
2. Processo de login
3. Dashboard principal

**O que falar:**
> "Esta é nossa tela de login. Vou fazer login como administrador..."

**Ações:**
1. Digitar usuário: `admin`
2. Digitar senha: `admin123` (pode aparecer como pontos)
3. Clicar em "Entrar"
4. Aguardar redirecionamento

**Ao chegar no Dashboard:**
> "Aqui temos o dashboard principal com uma visão geral do sistema. Podemos ver o total de peças cadastradas, alertas de estoque baixo, ordens de serviço em andamento e total de usuários. O menu lateral permite navegar entre todas as funcionalidades."

**Ações:**
- Apontar (com cursor) para cada card do dashboard
- Mostrar menu lateral brevemente

---

### **[1:15 - 2:30] Gestão de Peças** (75 segundos)

**O que mostrar:**
1. Listagem de peças
2. Criar nova peça
3. Editar peça
4. Indicadores de estoque baixo

**O que falar:**
> "Vamos para a gestão de peças. Aqui temos todas as peças cadastradas no sistema."

**Ações:**
1. Clicar em "Peças" no menu lateral
2. Mostrar a listagem (scroll suave se necessário)
3. Apontar para uma peça com estoque baixo (ícone vermelho)

> "Reparem que peças com estoque baixo são destacadas em vermelho. Vou cadastrar uma nova peça..."

**Criar Nova Peça:**
1. Clicar em "+ Nova Peça"
2. Preencher formulário:
   - **Nome:** "Correia Dentada"
   - **Descrição:** "Correia para motor elétrico"
   - **Quantidade:** 15
   - **Quantidade Mínima:** 5
   - **Quantidade Máxima:** 30
3. Clicar em "Salvar"
4. Mostrar a peça criada na lista

> "Pronto! A peça foi cadastrada e já aparece na nossa listagem."

**Editar Peça (rápido):**
1. Clicar no ícone de editar em uma peça
2. Alterar quantidade (ex: de 15 para 20)
3. Salvar
4. Mostrar atualização

> "Também podemos editar facilmente qualquer peça, atualizando suas informações em tempo real."

---

### **[2:30 - 3:00] Sistema de Alertas** (30 segundos)

**O que mostrar:**
1. Página de alertas
2. Peças com estoque crítico

**O que falar:**
> "O sistema possui alertas automáticos. Vamos ver quais peças estão com estoque baixo..."

**Ações:**
1. Clicar em "Alertas" no menu lateral
2. Mostrar lista de peças em estado crítico
3. Apontar para o déficit de cada peça

> "Aqui vemos todas as peças que atingiram ou estão abaixo da quantidade mínima. O sistema calcula automaticamente o déficit, facilitando a reposição."

---

### **[3:00 - 4:30] Ordens de Serviço** (90 segundos)

**O que mostrar:**
1. Listagem de ordens
2. Filtros
3. Criar nova ordem
4. Atualização automática de estoque

**O que falar:**
> "Agora vamos para as ordens de serviço. Aqui gerenciamos todas as manutenções e serviços."

**Ações:**
1. Clicar em "Ordens de Serviço" no menu
2. Mostrar listagem com diferentes status
3. Usar filtro (ex: filtrar por "Em Andamento")

> "Podemos filtrar por status ou técnico responsável. Vou criar uma nova ordem de serviço..."

**Criar Nova Ordem:**
1. Clicar em "+ Nova Ordem"
2. Preencher formulário:
   - **Descrição:** "Manutenção preventiva do compressor"
   - **Técnico:** Selecionar "João Silva"
   - **Status:** "Em Andamento"
   - **Peças:** Selecionar 2-3 peças com quantidades
     - Ex: Parafuso M6 (quantidade: 5)
     - Ex: Arruela (quantidade: 3)
3. Clicar em "Criar Ordem"

> "Ao criar a ordem, o sistema automaticamente atualiza o estoque, subtraindo as peças utilizadas. Vamos verificar..."

**Verificar Atualização de Estoque:**
1. Voltar para "Peças"
2. Mostrar que as quantidades foram atualizadas
3. Se alguma peça ficou em estoque baixo, mostrar o alerta

> "Vejam que as quantidades foram atualizadas automaticamente. Isso garante que o estoque esteja sempre sincronizado com as ordens de serviço."

---

### **[4:30 - 5:15] Gestão de Usuários** (45 segundos)

**O que mostrar:**
1. Listagem de usuários
2. Criar novo usuário
3. Tipos de usuário (admin/técnico)

**O que falar:**
> "O sistema também permite gerenciar usuários. Apenas administradores têm acesso a esta funcionalidade."

**Ações:**
1. Clicar em "Usuários" no menu
2. Mostrar lista de usuários
3. Apontar diferenças visuais entre admin e técnico

> "Vou cadastrar um novo técnico..."

**Criar Novo Usuário:**
1. Clicar em "+ Novo Usuário"
2. Preencher:
   - **Nome:** "Carlos Santos"
   - **Usuário:** "carlos"
   - **Senha:** "senha123"
   - **Tipo:** "Técnico"
3. Salvar
4. Mostrar usuário criado

> "Pronto! O novo técnico já pode fazer login e criar ordens de serviço."

---

### **[5:15 - 6:00] Responsividade e Tecnologias** (45 segundos)

**O que mostrar:**
1. Redimensionar janela do navegador
2. Mostrar adaptação responsiva
3. Mencionar tecnologias

**O que falar:**
> "Uma característica importante é a responsividade. Vou redimensionar a janela..."

**Ações:**
1. Redimensionar navegador para ~768px (tablet)
2. Mostrar que o layout se adapta
3. Redimensionar para ~375px (mobile)
4. Mostrar menu adaptado
5. Voltar para tamanho normal

> "A interface se adapta perfeitamente a diferentes tamanhos de tela, desde desktops até tablets."

**Mencionar tecnologias:**
> "O frontend foi desenvolvido com React 18, Vite para builds rápidos, React Router para navegação, Axios para comunicação com a API e Tailwind CSS para estilização moderna e eficiente."

---

### **[6:00 - 6:30] Demonstração de Edição e Exclusão** (30 segundos)

**O que mostrar:**
1. Editar uma ordem de serviço
2. Atualizar status

**O que falar:**
> "Podemos também atualizar o status das ordens. Vou marcar uma ordem como concluída..."

**Ações:**
1. Voltar para "Ordens de Serviço"
2. Clicar em uma ordem "Em Andamento"
3. Alterar status para "Concluída"
4. Salvar
5. Mostrar mudança visual (cor do badge)

> "O status é atualizado imediatamente, com feedback visual claro."

---

### **[6:30 - 7:00] Encerramento** (30 segundos)

**O que mostrar:**
1. Voltar ao Dashboard
2. Visão geral final

**O que falar:**
> "Voltando ao dashboard, podemos ver que todas as informações foram atualizadas em tempo real. O sistema oferece uma experiência completa e integrada para gestão de estoque e manutenção."

**Ações:**
1. Clicar em "Dashboard"
2. Mostrar cards atualizados
3. Fazer um scroll suave pela página

> "Este foi o frontend web do nosso sistema. Uma interface moderna, intuitiva e totalmente funcional. Obrigado!"

**Ação final:**
- Deixar o cursor parado no centro da tela por 2 segundos

---

## 🎯 Dicas Importantes

### Durante a Gravação

1. **Fale devagar e claramente**
   - Pause entre frases
   - Não tenha pressa

2. **Movimentos suaves**
   - Não mova o mouse muito rápido
   - Cliques deliberados e visíveis

3. **Destaque elementos importantes**
   - Use o cursor para apontar
   - Pause sobre elementos importantes

4. **Evite erros**
   - Se errar, pause e recomece a seção
   - Melhor gravar em partes e editar depois

5. **Mostre feedback visual**
   - Aguarde animações de carregamento
   - Mostre mensagens de sucesso

### O que NÃO fazer

- ❌ Não fale muito rápido
- ❌ Não clique repetidamente
- ❌ Não deixe abas desnecessárias abertas
- ❌ Não mostre dados sensíveis reais
- ❌ Não use dados de exemplo genéricos (ex: "teste", "asdf")
- ❌ Não grave com notificações aparecendo

---

## 🎨 Configurações de Gravação

### Software Recomendado

- **OBS Studio** (gratuito)
- **Loom** (fácil de usar)
- **QuickTime** (Mac)
- **ShareX** (Windows)

### Configurações de Vídeo

- **Resolução:** 1920x1080 (Full HD)
- **FPS:** 30 ou 60
- **Codec:** H.264
- **Bitrate:** 5000-8000 kbps

### Configurações de Áudio

- **Microfone:** Use um microfone externo se possível
- **Ambiente:** Silencioso, sem eco
- **Volume:** Teste antes de gravar
- **Formato:** AAC ou MP3

---

## 📋 Checklist Pós-Gravação

- [ ] Assistir o vídeo completo
- [ ] Verificar se o áudio está claro
- [ ] Confirmar que todas as funcionalidades foram mostradas
- [ ] Verificar se não há informações sensíveis
- [ ] Editar partes com erros (se necessário)
- [ ] Adicionar intro/outro (opcional)
- [ ] Adicionar música de fundo sutil (opcional)
- [ ] Exportar em alta qualidade

---

## 🎬 Estrutura Alternativa (Mais Curta - 3-4 minutos)

Se precisar de uma versão mais curta:

1. **Login + Dashboard** (30s)
2. **Criar Peça** (45s)
3. **Criar Ordem de Serviço** (60s)
4. **Mostrar Alertas** (30s)
5. **Responsividade** (30s)
6. **Encerramento** (15s)

**Total:** ~3:30 minutos

---

## 💡 Frases-Chave para Usar

- "Interface moderna e intuitiva"
- "Atualização em tempo real"
- "Totalmente responsivo"
- "Integração completa com o backend"
- "Feedback visual imediato"
- "Componentização reutilizável"
- "Experiência de usuário fluida"

---

## 🔄 Ordem Alternativa (Se Preferir)

Você pode gravar na seguinte ordem e editar depois:

1. Gravar todas as ações sem narração
2. Gravar a narração separadamente
3. Sincronizar na edição

Isso permite:
- Focar em uma coisa de cada vez
- Refazer a narração sem regravar a tela
- Melhor qualidade final

---

**Boa gravação! 🎥 Qualquer dúvida, estou aqui para ajudar!**
