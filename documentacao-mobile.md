# 📱 Documentação Técnica - Mobile
## Sistema de Gestão de Estoque e Manutenção

---

## 📋 Índice

1. [Visão Geral](#visão-geral)
2. [Arquitetura](#arquitetura)
3. [Tecnologias](#tecnologias)
4. [Instalação e Configuração](#instalação-e-configuração)
5. [Estrutura do Projeto](#estrutura-do-projeto)
6. [Camadas da Aplicação](#camadas-da-aplicação)
7. [Gerenciamento de Estado](#gerenciamento-de-estado)
8. [Modelos de Dados](#modelos-de-dados)
9. [Serviços de API](#serviços-de-api)
10. [Telas e Navegação](#telas-e-navegação)
11. [Build e Deploy](#build-e-deploy)

---

## 🎯 Visão Geral

O aplicativo mobile é desenvolvido em **Flutter**, permitindo deploy em **Android** e **iOS** com um único código-base. Utiliza arquitetura **MVVM** (Model-View-ViewModel) com **Riverpod** para gerenciamento de estado.

### Características Principais

- ✅ Multiplataforma (Android/iOS)
- ✅ Arquitetura MVVM
- ✅ Clean Architecture
- ✅ Gerenciamento de estado com Riverpod
- ✅ Integração completa com API REST
- ✅ Navegação declarativa
- ✅ Componentes reutilizáveis
- ✅ Logging estruturado

---

## 🏗️ Arquitetura

### Clean Architecture + MVVM

O projeto segue os princípios de Clean Architecture combinados com MVVM:

```
┌─────────────────────────────────────────┐
│  Presentation Layer (Views)             │  ← UI e interação do usuário
├─────────────────────────────────────────┤
│  ViewModel Layer                        │  ← Lógica de apresentação
├─────────────────────────────────────────┤
│  Domain Layer (Models, Repository)      │  ← Regras de negócio
├─────────────────────────────────────────┤
│  Data Layer (API Services, Repository)  │  ← Fonte de dados
└─────────────────────────────────────────┘
```

### Fluxo de Dados

```
User Action → View → ViewModel → Repository → API Service → Backend
                                                                ↓
User Interface ← View ← ViewModel ← Repository ← API Service ← Response
```

---

## 💻 Tecnologias

| Tecnologia | Versão | Propósito |
|------------|--------|-----------|
| **Flutter** | 3.16+ | Framework mobile |
| **Dart** | 3.2+ | Linguagem de programação |
| **Riverpod** | 2.4+ | Gerenciamento de estado |
| **Dio** | 5.4+ | Cliente HTTP |
| **Go Router** | - | Navegação |
| **Hive** | - | Armazenamento local |
| **Logger** | - | Logging |

---

## 🚀 Instalação e Configuração

### Pré-requisitos

- Flutter SDK 3.16+
- Dart SDK 3.2+
- Android Studio (para Android)
- Xcode (para iOS, apenas macOS)
- Dispositivo físico ou emulador

### Instalação

```bash
# Navegue até o diretório mobile
cd mobile

# Instale as dependências
flutter pub get

# Verifique a instalação
flutter doctor

# Execute o app (Android)
flutter run

# Execute o app (iOS)
flutter run -d ios
```

### Configuração da API

Edite o arquivo de configuração da API:

**`lib/data/services/api_config.dart`:**

```dart
class ApiConfig {
  static const String baseUrl = 'http://10.0.2.2:6000'; // Android Emulator
  // static const String baseUrl = 'http://localhost:6000'; // iOS Simulator
  // static const String baseUrl = 'https://api.seudominio.com'; // Produção
}
```

> **Nota:** 
> - Android Emulator: Use `10.0.2.2` para acessar localhost
> - iOS Simulator: Use `localhost`
> - Dispositivo físico: Use o IP da máquina na rede local

---

## 📁 Estrutura do Projeto

```
mobile/lib/
├── core/                          # Núcleo da aplicação
│   ├── providers/                 # Providers globais
│   ├── router/                    # Configuração de rotas
│   └── theme/                     # Tema e estilos
├── data/                          # Camada de dados
│   ├── services/                  # Serviços de API
│   │   ├── auth_api_service.dart
│   │   ├── order_service_api.dart
│   │   └── api_config.dart
│   └── repository_impl/           # Implementação de repositórios
│       ├── auth_repository_impl.dart
│       └── order_repository_impl.dart
├── domain/                        # Camada de domínio
│   ├── models/                    # Modelos de dados
│   │   ├── user_model.dart
│   │   ├── order_service_model.dart
│   │   ├── part_model.dart
│   │   └── stock_model.dart
│   └── repository/                # Interfaces de repositórios
│       ├── auth_repository.dart
│       └── order_repository.dart
├── view_model/                    # ViewModels (Riverpod)
│   ├── auth_view_model.dart
│   └── order_service_view_model.dart
├── features/                      # Features/Telas
│   └── views/
│       ├── login_view.dart
│       ├── home_view.dart
│       ├── profile_view.dart
│       ├── setting_view.dart
│       └── children/
│           ├── order_view.dart
│           └── order_form_view.dart
├── shared/                        # Componentes compartilhados
│   └── widgets/
│       ├── scaffold_home.dart
│       ├── text_form.dart
│       ├── elevated_button.dart
│       └── order_service_card.dart
└── main.dart                      # Entry point
```

---

## 🔧 Camadas da Aplicação

### 1. Presentation Layer (Views)

Contém as telas e widgets da aplicação.

**Responsabilidades:**
- Renderizar UI
- Capturar interações do usuário
- Observar mudanças de estado do ViewModel
- Exibir feedback visual (loading, erros)

**Exemplo:**

```dart
class OrderView extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final ordersState = ref.watch(orderViewModelProvider);
    
    return ordersState.when(
      loading: () => CircularProgressIndicator(),
      error: (error, stack) => Text('Erro: $error'),
      data: (orders) => ListView.builder(
        itemCount: orders.length,
        itemBuilder: (context, index) => OrderCard(order: orders[index]),
      ),
    );
  }
}
```

---

### 2. ViewModel Layer

Gerencia o estado e a lógica de apresentação.

**Responsabilidades:**
- Processar ações do usuário
- Chamar métodos do Repository
- Gerenciar estados (loading, success, error)
- Transformar dados para a View

**Exemplo:**

```dart
class OrderServiceViewModel extends StateNotifier<AsyncValue<List<OrderServiceModel>>> {
  final OrderRepository _repository;
  
  OrderServiceViewModel(this._repository) : super(const AsyncValue.loading()) {
    loadOrders();
  }
  
  Future<void> loadOrders() async {
    state = const AsyncValue.loading();
    try {
      final orders = await _repository.fetchOrders();
      state = AsyncValue.data(orders);
    } catch (e, stack) {
      state = AsyncValue.error(e, stack);
    }
  }
  
  Future<void> createOrder(OrderServiceModel order) async {
    try {
      await _repository.createOrder(order);
      await loadOrders(); // Recarrega lista
    } catch (e) {
      // Tratar erro
    }
  }
}
```

---

### 3. Domain Layer

Define modelos e interfaces de repositórios.

**Responsabilidades:**
- Definir entidades de negócio (Models)
- Definir contratos de repositórios (interfaces)
- Regras de validação de domínio

**Exemplo de Model:**

```dart
class OrderServiceModel {
  final int? id;
  final String descricao;
  final String status;
  final int tecnicoId;
  final List<PartUsage> pecasUtilizadas;
  final DateTime? createdAt;
  
  OrderServiceModel({
    this.id,
    required this.descricao,
    required this.status,
    required this.tecnicoId,
    required this.pecasUtilizadas,
    this.createdAt,
  });
  
  factory OrderServiceModel.fromJson(Map<String, dynamic> json) {
    return OrderServiceModel(
      id: json['id'],
      descricao: json['descricao'],
      status: json['status'],
      tecnicoId: json['tecnico_id'],
      pecasUtilizadas: (json['pecas_utilizadas'] as List)
          .map((p) => PartUsage.fromJson(p))
          .toList(),
      createdAt: json['created_at'] != null 
          ? DateTime.parse(json['created_at']) 
          : null,
    );
  }
  
  Map<String, dynamic> toJson() {
    return {
      'descricao': descricao,
      'status': status,
      'tecnico_id': tecnicoId,
      'pecas_utilizadas': pecasUtilizadas.map((p) => p.toJson()).toList(),
    };
  }
}
```

**Exemplo de Repository Interface:**

```dart
abstract class OrderRepository {
  Future<List<OrderServiceModel>> fetchOrders();
  Future<OrderServiceModel> createOrder(OrderServiceModel order);
  Future<OrderServiceModel> updateOrder(int id, OrderServiceModel order);
  Future<void> deleteOrder(int id);
}
```

---

### 4. Data Layer

Implementa repositórios e serviços de API.

**Responsabilidades:**
- Comunicação com backend
- Serialização/deserialização de dados
- Tratamento de erros de rede
- Cache (futuro)

**Exemplo de API Service:**

```dart
class OrderServiceApi {
  final Dio _dio;
  
  OrderServiceApi(this._dio);
  
  Future<List<OrderServiceModel>> getOrders() async {
    try {
      final response = await _dio.get('/ordemservico');
      return (response.data as List)
          .map((json) => OrderServiceModel.fromJson(json))
          .toList();
    } on DioException catch (e) {
      throw _handleError(e);
    }
  }
  
  Future<OrderServiceModel> createOrder(OrderServiceModel order) async {
    try {
      final response = await _dio.post('/ordemservico', data: order.toJson());
      return OrderServiceModel.fromJson(response.data);
    } on DioException catch (e) {
      throw _handleError(e);
    }
  }
  
  Exception _handleError(DioException e) {
    if (e.response != null) {
      return Exception('Erro ${e.response!.statusCode}: ${e.response!.data}');
    } else {
      return Exception('Erro de conexão: ${e.message}');
    }
  }
}
```

**Exemplo de Repository Implementation:**

```dart
class OrderRepositoryImpl implements OrderRepository {
  final OrderServiceApi _api;
  
  OrderRepositoryImpl(this._api);
  
  @override
  Future<List<OrderServiceModel>> fetchOrders() async {
    return await _api.getOrders();
  }
  
  @override
  Future<OrderServiceModel> createOrder(OrderServiceModel order) async {
    return await _api.createOrder(order);
  }
  
  @override
  Future<OrderServiceModel> updateOrder(int id, OrderServiceModel order) async {
    return await _api.updateOrder(id, order);
  }
  
  @override
  Future<void> deleteOrder(int id) async {
    await _api.deleteOrder(id);
  }
}
```

---

## 🔄 Gerenciamento de Estado

### Riverpod

O projeto utiliza **Riverpod** para gerenciamento de estado reativo.

**Providers Principais:**

```dart
// Provider do Dio (HTTP Client)
final dioProvider = Provider<Dio>((ref) {
  final dio = Dio(BaseOptions(
    baseURL: ApiConfig.baseUrl,
    connectTimeout: Duration(seconds: 5),
    receiveTimeout: Duration(seconds: 3),
  ));
  
  // Interceptors para logging
  dio.interceptors.add(LogInterceptor(
    requestBody: true,
    responseBody: true,
  ));
  
  return dio;
});

// Provider do API Service
final orderApiProvider = Provider<OrderServiceApi>((ref) {
  final dio = ref.watch(dioProvider);
  return OrderServiceApi(dio);
});

// Provider do Repository
final orderRepositoryProvider = Provider<OrderRepository>((ref) {
  final api = ref.watch(orderApiProvider);
  return OrderRepositoryImpl(api);
});

// Provider do ViewModel
final orderViewModelProvider = StateNotifierProvider<OrderServiceViewModel, AsyncValue<List<OrderServiceModel>>>((ref) {
  final repository = ref.watch(orderRepositoryProvider);
  return OrderServiceViewModel(repository);
});
```

**Uso na View:**

```dart
class OrderView extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    // Observa mudanças no estado
    final ordersState = ref.watch(orderViewModelProvider);
    
    return ordersState.when(
      loading: () => Center(child: CircularProgressIndicator()),
      error: (error, stack) => Center(child: Text('Erro: $error')),
      data: (orders) => ListView.builder(
        itemCount: orders.length,
        itemBuilder: (context, index) {
          return OrderServiceCard(order: orders[index]);
        },
      ),
    );
  }
}
```

---

## 📊 Modelos de Dados

### 1. UserModel

```dart
class UserModel {
  final int id;
  final String nome;
  final String usuario;
  final String tipo;
  
  UserModel({
    required this.id,
    required this.nome,
    required this.usuario,
    required this.tipo,
  });
  
  factory UserModel.fromJson(Map<String, dynamic> json) {
    return UserModel(
      id: json['id'],
      nome: json['nome'],
      usuario: json['usuario'],
      tipo: json['tipo'],
    );
  }
}
```

---

### 2. PartModel

```dart
class PartModel {
  final int id;
  final String nome;
  final String? descricao;
  final int quantidade;
  final int quantidadeMinima;
  final int quantidadeMaxima;
  
  PartModel({
    required this.id,
    required this.nome,
    this.descricao,
    required this.quantidade,
    required this.quantidadeMinima,
    required this.quantidadeMaxima,
  });
  
  factory PartModel.fromJson(Map<String, dynamic> json) {
    return PartModel(
      id: json['id'],
      nome: json['nome'],
      descricao: json['descricao'],
      quantidade: json['quantidade'],
      quantidadeMinima: json['quantidade_minima'],
      quantidadeMaxima: json['quantidade_maxima'],
    );
  }
  
  bool get isLowStock => quantidade <= quantidadeMinima;
}
```

---

### 3. OrderServiceModel

```dart
class OrderServiceModel {
  final int? id;
  final String descricao;
  final String status;
  final int tecnicoId;
  final String? tecnicoNome;
  final List<PartUsage> pecasUtilizadas;
  final DateTime? createdAt;
  
  OrderServiceModel({
    this.id,
    required this.descricao,
    required this.status,
    required this.tecnicoId,
    this.tecnicoNome,
    required this.pecasUtilizadas,
    this.createdAt,
  });
  
  factory OrderServiceModel.fromJson(Map<String, dynamic> json) {
    return OrderServiceModel(
      id: json['id'],
      descricao: json['descricao'],
      status: json['status'],
      tecnicoId: json['tecnico_id'],
      tecnicoNome: json['tecnico_nome'],
      pecasUtilizadas: (json['pecas_utilizadas'] as List?)
          ?.map((p) => PartUsage.fromJson(p))
          .toList() ?? [],
      createdAt: json['created_at'] != null 
          ? DateTime.parse(json['created_at']) 
          : null,
    );
  }
  
  Map<String, dynamic> toJson() {
    return {
      'descricao': descricao,
      'status': status,
      'tecnico_id': tecnicoId,
      'pecas_utilizadas': pecasUtilizadas.map((p) => p.toJson()).toList(),
    };
  }
}

class PartUsage {
  final int pecaId;
  final int quantidade;
  
  PartUsage({required this.pecaId, required this.quantidade});
  
  factory PartUsage.fromJson(Map<String, dynamic> json) {
    return PartUsage(
      pecaId: json['peca_id'],
      quantidade: json['quantidade'],
    );
  }
  
  Map<String, dynamic> toJson() {
    return {
      'peca_id': pecaId,
      'quantidade': quantidade,
    };
  }
}
```

---

## 🔌 Serviços de API

### AuthApiService

```dart
class AuthApiService {
  final Dio _dio;
  
  AuthApiService(this._dio);
  
  Future<UserModel> login(String usuario, String senha) async {
    try {
      final response = await _dio.post('/login', data: {
        'usuario': usuario,
        'senha': senha,
      });
      return UserModel.fromJson(response.data);
    } on DioException catch (e) {
      if (e.response?.statusCode == 401) {
        throw Exception('Credenciais inválidas');
      }
      throw Exception('Erro ao fazer login: ${e.message}');
    }
  }
}
```

---

### OrderServiceApi

```dart
class OrderServiceApi {
  final Dio _dio;
  
  OrderServiceApi(this._dio);
  
  Future<List<OrderServiceModel>> getOrders() async {
    final response = await _dio.get('/ordemservico');
    return (response.data as List)
        .map((json) => OrderServiceModel.fromJson(json))
        .toList();
  }
  
  Future<OrderServiceModel> createOrder(OrderServiceModel order) async {
    final response = await _dio.post('/ordemservico', data: order.toJson());
    return OrderServiceModel.fromJson(response.data);
  }
  
  Future<OrderServiceModel> updateOrder(int id, OrderServiceModel order) async {
    final response = await _dio.put('/ordemservico/$id', data: order.toJson());
    return OrderServiceModel.fromJson(response.data);
  }
  
  Future<void> deleteOrder(int id) async {
    await _dio.delete('/ordemservico/$id');
  }
}
```

---

## 📱 Telas e Navegação

### Telas Implementadas

1. **LoginView** (`/login`)
   - Autenticação de usuários
   - Validação de campos
   - Feedback de erro

2. **HomeView** (`/home`)
   - Tela principal com navegação
   - Bottom navigation bar
   - Acesso a todas as funcionalidades

3. **OrderView** (`/orders`)
   - Listagem de ordens de serviço
   - Pull-to-refresh
   - Navegação para detalhes

4. **OrderFormView** (`/orders/new`)
   - Criação de novas ordens
   - Seleção de técnico
   - Seleção de peças

5. **ProfileView** (`/profile`)
   - Informações do usuário
   - Logout

6. **SettingView** (`/settings`)
   - Configurações do app

---

### Navegação

**Router Configuration:**

```dart
final routerProvider = Provider<GoRouter>((ref) {
  return GoRouter(
    initialLocation: '/login',
    routes: [
      GoRoute(
        path: '/login',
        builder: (context, state) => LoginView(),
      ),
      GoRoute(
        path: '/home',
        builder: (context, state) => HomeView(),
        routes: [
          GoRoute(
            path: 'orders',
            builder: (context, state) => OrderView(),
          ),
          GoRoute(
            path: 'orders/new',
            builder: (context, state) => OrderFormView(),
          ),
          GoRoute(
            path: 'profile',
            builder: (context, state) => ProfileView(),
          ),
          GoRoute(
            path: 'settings',
            builder: (context, state) => SettingView(),
          ),
        ],
      ),
    ],
  );
});
```

---

## 🏗️ Build e Deploy

### Build para Android

```bash
# Debug APK
flutter build apk --debug

# Release APK
flutter build apk --release

# App Bundle (para Google Play)
flutter build appbundle --release

# Localização dos arquivos:
# APK: build/app/outputs/flutter-apk/app-release.apk
# AAB: build/app/outputs/bundle/release/app-release.aab
```

---

### Build para iOS

```bash
# Debug
flutter build ios --debug

# Release
flutter build ios --release

# Abrir no Xcode
open ios/Runner.xcworkspace
```

---

### Configurações de Build

**Android (`android/app/build.gradle`):**

```gradle
android {
    defaultConfig {
        applicationId "com.senai.gestao_estoque"
        minSdkVersion 21
        targetSdkVersion 34
        versionCode 1
        versionName "1.0.0"
    }
    
    buildTypes {
        release {
            signingConfig signingConfigs.release
            minifyEnabled true
            shrinkResources true
        }
    }
}
```

**iOS (`ios/Runner/Info.plist`):**

```xml
<key>CFBundleDisplayName</key>
<string>Gestão Estoque</string>
<key>CFBundleVersion</key>
<string>1</string>
<key>CFBundleShortVersionString</key>
<string>1.0.0</string>
```

---

## 🧪 Testes

### Testes Unitários

```dart
void main() {
  group('OrderServiceModel', () {
    test('fromJson should parse correctly', () {
      final json = {
        'id': 1,
        'descricao': 'Test',
        'status': 'pendente',
        'tecnico_id': 2,
        'pecas_utilizadas': [],
      };
      
      final order = OrderServiceModel.fromJson(json);
      
      expect(order.id, 1);
      expect(order.descricao, 'Test');
      expect(order.status, 'pendente');
    });
  });
}
```

**Executar testes:**

```bash
flutter test
```

---

## 🔒 Segurança

### Boas Práticas

- ✅ Não armazenar senhas em texto plano
- ✅ Usar HTTPS em produção
- ✅ Validar inputs do usuário
- ✅ Timeout em requisições HTTP

### Armazenamento Seguro

Para armazenar tokens de autenticação:

```dart
import 'package:flutter_secure_storage/flutter_secure_storage.dart';

final storage = FlutterSecureStorage();

// Salvar token
await storage.write(key: 'auth_token', value: token);

// Ler token
final token = await storage.read(key: 'auth_token');

// Deletar token
await storage.delete(key: 'auth_token');
```

---

## 📚 Dependências

**`pubspec.yaml`:**

```yaml
dependencies:
  flutter:
    sdk: flutter
  
  # State Management
  flutter_riverpod: ^2.4.0
  
  # HTTP Client
  dio: ^5.4.0
  
  # Routing
  go_router: ^12.0.0
  
  # Local Storage
  hive: ^2.2.3
  hive_flutter: ^1.1.0
  
  # Logging
  logger: ^2.0.0
  
  # Utils
  intl: ^0.18.1

dev_dependencies:
  flutter_test:
    sdk: flutter
  flutter_lints: ^3.0.0
```

---

## 🛠️ Troubleshooting

### Problema: Erro de conexão com API

**Solução:**
- Android Emulator: Use `10.0.2.2:6000`
- iOS Simulator: Use `localhost:6000`
- Dispositivo físico: Use IP da máquina (ex: `192.168.1.100:6000`)

### Problema: Build falha no Android

**Solução:**
```bash
cd android
./gradlew clean
cd ..
flutter clean
flutter pub get
flutter build apk
```

### Problema: Dependências não instalam

**Solução:**
```bash
flutter clean
flutter pub cache repair
flutter pub get
```

---

## 📚 Referências

- [Flutter Documentation](https://docs.flutter.dev/)
- [Riverpod Documentation](https://riverpod.dev/)
- [Dio Documentation](https://pub.dev/packages/dio)
- [Go Router Documentation](https://pub.dev/packages/go_router)

---

## 👥 Equipe de Desenvolvimento

- **Cristian Moises Brunone Cordero** - Mobile

---

## 🔄 Roadmap

### Funcionalidades Futuras

- [ ] Gestão completa de estoque no mobile
- [ ] Notificações push (Firebase Cloud Messaging)
- [ ] Upload de fotos nas ordens
- [ ] Geolocalização de técnicos
- [ ] Modo offline com sincronização
- [ ] Relatórios e gráficos
- [ ] Dark mode
- [ ] Internacionalização (i18n)

---

**Versão:** 1.0.0  
**Última atualização:** Novembro 2024
