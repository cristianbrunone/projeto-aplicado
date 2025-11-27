# 📱 Roteiro de Gravação - Mobile (Flutter)
## Sistema de Gestão de Estoque e Manutenção

---

## ⏱️ Tempo Sugerido: 4-5 minutos

---

## 🎬 Preparação Antes de Gravar

### Checklist Técnico

- [ ] Backend rodando (`docker-compose up`)
- [ ] App mobile compilado e rodando
- [ ] Emulador/Dispositivo configurado
- [ ] Dados de exemplo no banco de dados
- [ ] Bateria do dispositivo carregada (se físico)
- [ ] Modo "Não Perturbe" ativado
- [ ] Notificações desabilitadas
- [ ] Brilho da tela ajustado (não muito alto)

### Escolha do Dispositivo

**Opção 1: Emulador Android (Recomendado para gravação)**
- Mais fácil de gravar
- Resolução controlada
- Sem interrupções

**Opção 2: Dispositivo Físico**
- Mais realista
- Requer espelhamento de tela
- Use scrcpy (Android) ou QuickTime (iOS)

### Configuração do Emulador

```bash
# Criar emulador Android (se não tiver)
flutter emulators --create

# Listar emuladores disponíveis
flutter emulators

# Iniciar emulador
flutter emulators --launch <emulator_id>

# Rodar app
flutter run
```

**Configurações recomendadas do emulador:**
- Dispositivo: Pixel 6 ou Pixel 7
- Resolução: 1080 x 2400 (FHD+)
- Android: 13 ou 14
- Orientação: Portrait (vertical)

### Dados de Exemplo

**Usuários:**
- Admin: `admin` / `admin123`
- Técnico: `joao` / `senha123`

**Ordens de Serviço:**
- 5-8 ordens em diferentes status
- Dados realistas (não "teste", "asdf")

---

## 📝 Roteiro de Gravação

### **[0:00 - 0:20] Introdução** (20 segundos)

**O que mostrar:**
- Tela inicial do app (splash screen ou login)

**O que falar:**
> "Olá! Vou apresentar o aplicativo mobile do nosso Sistema de Gestão de Estoque e Manutenção. Desenvolvido em Flutter, o app está disponível para Android e iOS, permitindo que técnicos acessem e gerenciem ordens de serviço de qualquer lugar."

**Ação:**
- Mostrar tela de login do app

---

### **[0:20 - 0:50] Login** (30 segundos)

**O que mostrar:**
1. Tela de login
2. Processo de autenticação
3. Transição para home

**O que falar:**
> "Vou fazer login como técnico. O app se conecta à mesma API do sistema web, garantindo sincronização total dos dados."

**Ações:**
1. Tocar no campo "Usuário"
2. Digitar: `joao` (mostrar teclado virtual)
3. Tocar no campo "Senha"
4. Digitar: `senha123`
5. Tocar em "Entrar"
6. Aguardar loading
7. Mostrar transição para tela principal

> "Login realizado com sucesso! Vamos para a tela principal."

---

### **[0:50 - 1:30] Tela Principal e Navegação** (40 segundos)

**O que mostrar:**
1. Home com lista de ordens
2. Bottom navigation bar
3. Navegação entre telas

**O que falar:**
> "Esta é a tela principal do app. Aqui vemos todas as ordens de serviço. Cada card mostra informações essenciais: descrição, técnico responsável, status e data de criação."

**Ações:**
1. Mostrar lista de ordens (scroll suave)
2. Apontar para elementos de um card:
   - Descrição
   - Nome do técnico
   - Badge de status
   - Data
3. Mostrar bottom navigation bar

> "O app possui navegação intuitiva na parte inferior. Podemos acessar ordens, perfil e configurações."

**Ações:**
1. Tocar em "Perfil" (mostrar tela de perfil brevemente)
2. Voltar para "Ordens"

---

### **[1:30 - 2:00] Visualizar Detalhes de Ordem** (30 segundos)

**O que mostrar:**
1. Tocar em uma ordem
2. Tela de detalhes
3. Informações completas

**O que falar:**
> "Vou abrir uma ordem para ver os detalhes completos..."

**Ações:**
1. Tocar em um card de ordem
2. Mostrar tela de detalhes com:
   - Descrição completa
   - Técnico responsável
   - Status
   - Peças utilizadas (se houver)
   - Data de criação
3. Scroll suave para mostrar todas as informações

> "Aqui temos todos os detalhes da ordem: descrição completa, técnico, status e as peças que foram utilizadas neste serviço."

**Ação:**
- Voltar para lista (botão voltar ou gesto)

---

### **[2:00 - 3:30] Criar Nova Ordem de Serviço** (90 segundos)

**O que mostrar:**
1. Botão de adicionar
2. Formulário de criação
3. Seleção de técnico
4. Seleção de peças
5. Criação bem-sucedida

**O que falar:**
> "Agora vou criar uma nova ordem de serviço. Vou tocar no botão de adicionar..."

**Ações:**
1. Tocar no FAB (Floating Action Button) "+"
2. Mostrar formulário de criação

> "Aqui temos o formulário para criar uma nova ordem. Vou preencher as informações..."

**Preencher Formulário:**

1. **Descrição:**
   - Tocar no campo
   - Digitar: "Troca de rolamentos do motor principal"
   - Fechar teclado

2. **Técnico Responsável:**
   - Tocar no dropdown/seletor
   - Mostrar lista de técnicos
   - Selecionar "João Silva"

3. **Status:**
   - Tocar no seletor de status
   - Selecionar "Em Andamento"

4. **Peças Utilizadas:**
   - Tocar em "Adicionar Peças"
   - Selecionar primeira peça (ex: "Rolamento 6205")
   - Definir quantidade: 2
   - Adicionar outra peça (ex: "Graxa Industrial")
   - Definir quantidade: 1
   - Mostrar lista de peças selecionadas

> "Selecionei as peças necessárias para este serviço. O sistema vai atualizar o estoque automaticamente ao criar a ordem."

**Criar Ordem:**
1. Tocar em "Criar Ordem" ou "Salvar"
2. Mostrar loading/feedback
3. Aguardar confirmação
4. Voltar para lista

> "Ordem criada com sucesso! Vejam que ela já aparece na nossa lista."

**Ação:**
- Scroll até encontrar a ordem recém-criada
- Destacar visualmente (tocar nela brevemente)

---

### **[3:30 - 4:00] Pull to Refresh** (30 segundos)

**O que mostrar:**
1. Gesto de pull-to-refresh
2. Atualização da lista
3. Sincronização com backend

**O que falar:**
> "O app possui pull-to-refresh para sincronizar os dados com o servidor. Vou puxar a lista para baixo..."

**Ações:**
1. Fazer gesto de pull-to-refresh (arrastar de cima para baixo)
2. Mostrar indicador de loading
3. Aguardar atualização
4. Mostrar lista atualizada

> "Pronto! A lista foi atualizada com os dados mais recentes do servidor. Isso garante que todos os técnicos vejam as mesmas informações em tempo real."

---

### **[4:00 - 4:30] Arquitetura e Tecnologias** (30 segundos)

**O que mostrar:**
1. Navegar entre telas
2. Mostrar fluidez
3. Mencionar tecnologias

**O que falar:**
> "O aplicativo foi desenvolvido com Flutter, utilizando arquitetura MVVM e Riverpod para gerenciamento de estado. Isso garante código limpo, testável e de fácil manutenção."

**Ações:**
1. Navegar para "Perfil"
2. Mostrar informações do usuário
3. Navegar para "Configurações"
4. Voltar para "Ordens"

> "A arquitetura segue Clean Architecture, com separação clara entre camadas de apresentação, domínio e dados. Toda comunicação com o backend é feita via API REST usando Dio."

---

### **[4:30 - 5:00] Funcionalidades Futuras e Encerramento** (30 segundos)

**O que mostrar:**
1. Scroll pela lista final
2. Visão geral do app

**O que falar:**
> "Atualmente o app possui as funcionalidades essenciais para técnicos: visualizar e criar ordens de serviço. Já estamos planejando expansões futuras como gestão completa de estoque, notificações push, upload de fotos nas ordens e geolocalização de técnicos."

**Ações:**
1. Scroll suave pela lista de ordens
2. Mostrar bottom navigation
3. Deixar na tela principal

> "Este foi o aplicativo mobile do nosso sistema. Uma solução multiplataforma, moderna e totalmente integrada com o backend. Obrigado!"

**Ação final:**
- Deixar app na tela de ordens por 2 segundos

---

## 🎯 Dicas Importantes

### Durante a Gravação

1. **Toques visíveis**
   - Ative "Mostrar toques" nas configurações do desenvolvedor (Android)
   - Toque de forma deliberada e visível
   - Pause após cada toque importante

2. **Movimentos suaves**
   - Scroll devagar e suave
   - Evite gestos muito rápidos
   - Aguarde animações completarem

3. **Orientação**
   - Mantenha sempre em modo portrait (vertical)
   - Não rotacione o dispositivo

4. **Teclado virtual**
   - Mostre o teclado ao digitar
   - Digite devagar para ser visível
   - Feche o teclado quando terminar

5. **Feedback visual**
   - Aguarde loading indicators
   - Mostre mensagens de sucesso/erro
   - Destaque elementos importantes

### O que NÃO fazer

- ❌ Não toque muito rápido
- ❌ Não faça scroll muito rápido
- ❌ Não mostre notificações pessoais
- ❌ Não use dados genéricos ("teste", "asdf")
- ❌ Não grave com bateria baixa (mostra na tela)
- ❌ Não grave com conexão instável

---

## 🎨 Configurações de Gravação

### Android - Habilitar Toques Visíveis

```bash
# Via ADB
adb shell settings put system show_touches 1

# Para desabilitar depois
adb shell settings put system show_touches 0
```

Ou manualmente:
1. Configurações → Sistema → Opções do desenvolvedor
2. Ativar "Mostrar toques"

### Ferramentas de Gravação

**Android:**
- **scrcpy** (recomendado) - Espelhamento + gravação
- **ADB screenrecord** - Nativo do Android
- **OBS Studio** - Captura de tela do emulador

**iOS:**
- **QuickTime Player** (Mac) - Gravação de tela do iPhone
- **OBS Studio** - Captura de tela do simulador

### Comando scrcpy (Android)

```bash
# Instalar scrcpy
brew install scrcpy  # Mac
# ou
sudo apt install scrcpy  # Linux

# Gravar tela
scrcpy --record mobile-demo.mp4

# Gravar com melhor qualidade
scrcpy --record mobile-demo.mp4 --bit-rate 8M --max-fps 60
```

### Configurações de Vídeo

- **Resolução:** 1080 x 2400 (nativa do dispositivo)
- **FPS:** 30 ou 60
- **Codec:** H.264
- **Bitrate:** 5000-8000 kbps
- **Orientação:** Portrait (vertical)

---

## 📋 Checklist de Dados de Exemplo

### Ordens de Serviço (Criar antes de gravar)

1. **Ordem Pendente:**
   - Descrição: "Verificação de vazamento no sistema hidráulico"
   - Técnico: Maria Santos
   - Status: Pendente

2. **Ordem Em Andamento:**
   - Descrição: "Substituição de correias do compressor"
   - Técnico: João Silva
   - Status: Em Andamento
   - Peças: Correia Dentada (2), Parafuso M8 (8)

3. **Ordem Concluída:**
   - Descrição: "Manutenção preventiva mensal - Setor A"
   - Técnico: João Silva
   - Status: Concluída
   - Peças: Graxa (1), Filtro de Ar (2)

4. **Ordem Pendente:**
   - Descrição: "Reparo no sistema elétrico da prensa"
   - Técnico: Carlos Santos
   - Status: Pendente

5. **Ordem Em Andamento:**
   - Descrição: "Troca de rolamentos do motor secundário"
   - Técnico: Maria Santos
   - Status: Em Andamento
   - Peças: Rolamento 6205 (4), Graxa Industrial (1)

---

## 🎬 Estrutura Alternativa (Mais Curta - 3 minutos)

Se precisar de uma versão mais curta:

1. **Introdução + Login** (30s)
2. **Visualizar Ordens** (30s)
3. **Criar Nova Ordem** (90s)
4. **Pull to Refresh** (20s)
5. **Encerramento** (20s)

**Total:** ~3 minutos

---

## 💡 Frases-Chave para Usar

- "Multiplataforma - Android e iOS"
- "Arquitetura MVVM com Clean Architecture"
- "Sincronização em tempo real"
- "Interface nativa e fluida"
- "Gerenciamento de estado com Riverpod"
- "Integração completa com a API"
- "Experiência mobile otimizada"

---

## 🔄 Fluxo Alternativo (Demonstração Técnica)

Se o público for mais técnico, mencione:

1. **Arquitetura:**
   - "Camadas bem definidas: Presentation, ViewModel, Domain, Data"
   - "Separação de responsabilidades"

2. **State Management:**
   - "Riverpod para gerenciamento de estado reativo"
   - "Providers para injeção de dependências"

3. **Networking:**
   - "Dio para requisições HTTP"
   - "Tratamento de erros robusto"

4. **Modelos:**
   - "Serialização/deserialização automática"
   - "Type-safe models"

---

## 📱 Dicas de Espelhamento de Tela

### Android (scrcpy)

```bash
# Espelhar sem gravar
scrcpy

# Espelhar e gravar
scrcpy --record demo.mp4

# Espelhar com melhor qualidade
scrcpy --bit-rate 8M --max-size 1080

# Espelhar sem controle (apenas visualização)
scrcpy --no-control
```

### iOS (QuickTime - Mac)

1. Conectar iPhone via cabo
2. Abrir QuickTime Player
3. Arquivo → Nova Gravação de Filme
4. Selecionar iPhone como fonte
5. Clicar em gravar

---

## 🎤 Dicas de Narração

### Tom de Voz
- Entusiasmado mas profissional
- Claro e pausado
- Confiante

### Estrutura das Frases
- Frases curtas e diretas
- Evite "uhm", "ahh", "né"
- Pause entre ações importantes

### Exemplo de Boa Narração
✅ "Vou criar uma nova ordem. *[pausa]* Toco no botão de adicionar. *[pausa]* Agora preencho a descrição..."

### Exemplo de Má Narração
❌ "Então, uhm, agora eu vou, tipo, criar uma ordem, né, então vou clicar aqui..."

---

## 📋 Checklist Pós-Gravação

- [ ] Assistir vídeo completo
- [ ] Verificar áudio claro
- [ ] Confirmar que toques estão visíveis (se Android)
- [ ] Verificar se todas as funcionalidades foram mostradas
- [ ] Confirmar que não há informações sensíveis
- [ ] Verificar qualidade do vídeo (resolução, nitidez)
- [ ] Editar partes com erros (se necessário)
- [ ] Adicionar intro/outro (opcional)
- [ ] Converter para formato adequado (MP4)

---

## 🎥 Edição Pós-Produção (Opcional)

### Elementos para Adicionar

1. **Intro (5s):**
   - Título: "Sistema Mobile - Flutter"
   - Seu nome

2. **Legendas:**
   - Adicionar legendas para pontos-chave
   - Ex: "Arquitetura MVVM", "Riverpod", "API REST"

3. **Zoom:**
   - Zoom em elementos pequenos (botões, campos)
   - Destaque de ações importantes

4. **Transições:**
   - Transições suaves entre seções
   - Fade in/out

5. **Música de Fundo:**
   - Volume baixo (não deve competir com narração)
   - Música neutra e profissional

---

## 🚀 Comandos Úteis

### Verificar dispositivos conectados
```bash
flutter devices
```

### Rodar no dispositivo específico
```bash
flutter run -d <device_id>
```

### Build para demonstração
```bash
# Android APK
flutter build apk --release

# iOS (apenas Mac)
flutter build ios --release
```

### Limpar e rebuildar (se houver problemas)
```bash
flutter clean
flutter pub get
flutter run
```

---

**Boa gravação! 📱 Mostre o poder do Flutter! 🚀**
