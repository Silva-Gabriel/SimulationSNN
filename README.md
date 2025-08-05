# SnnProject

Este projeto segue os princípios da **Clean Architecture** e está organizado em camadas bem definidas.

## Estrutura do Projeto

```
SnnProject/
├── SnnProject.sln                 # Solution principal
├── Api/                           # Camada de apresentação (Web API)
│   └── SnnProject.Api/
├── Application/                   # Camada de aplicação (Casos de uso)
│   └── SnnProject.Application/
├── Domain/                        # Camada de domínio (Entidades e regras de negócio)
│   └── SnnProject.Domain/
├── Infrastructure/                # Camada de infraestrutura (Dados, serviços externos)
│   └── SnnProject.Infrastructure/
└── Crosscutting/                  # Funcionalidades transversais (Logging, Utils, etc.)
    └── SnnProject.Crosscutting/
```

## Dependências entre Camadas

```
┌─────────────────┐
│       Api       │
└─────────────────┘
         │
         ▼
┌─────────────────┐    ┌─────────────────┐
│ Infrastructure  │◄───│  Crosscutting   │
└─────────────────┘    └─────────────────┘
         │
         ▼
┌─────────────────┐
│   Application   │
└─────────────────┘
         │
         ▼
┌─────────────────┐
│     Domain      │
└─────────────────┘
```

## Descrição das Camadas

### 🎯 **Domain** (Núcleo)

- **Propósito**: Contém as entidades de negócio, regras de domínio e interfaces
- **Dependências**: Nenhuma (camada independente)
- **Conteúdo**: Entidades, Value Objects, Enums, Interfaces de Repository

### 🔧 **Application** (Casos de Uso)

- **Propósito**: Orquestra a lógica de aplicação e casos de uso
- **Dependências**: Domain
- **Conteúdo**: Services, DTOs, Use Cases, Handlers, Validators

### 🗄️ **Infrastructure** (Dados e Serviços Externos)

- **Propósito**: Implementa interfaces de dados e serviços externos
- **Dependências**: Domain, Application
- **Conteúdo**: Repositories, DbContext, Configurações de banco, APIs externas

### 🌐 **Api** (Apresentação)

- **Propósito**: Exposição dos endpoints e controle de entrada/saída
- **Dependências**: Application, Infrastructure, Crosscutting
- **Conteúdo**: Controllers, Middlewares, Configurações de startup

### ⚡ **Crosscutting** (Transversal)

- **Propósito**: Funcionalidades que atravessam todas as camadas
- **Dependências**: Nenhuma
- **Conteúdo**: Logging, Extensions, Helpers, Utilities

## Como usar

### Compilar a solução

```bash
dotnet build
```

### Executar a API

```bash
dotnet run --project Api/SnnProject.Api/SnnProject.Api.csproj
```

### Executar com watch (auto-reload)

```bash
dotnet watch run --project Api/SnnProject.Api/SnnProject.Api.csproj
```

### Executar testes

```bash
dotnet test
```

## Debug no VS Code

O projeto está configurado com arquivos para debug no VS Code:

### 🐛 **Configurações de Debug (.vscode/launch.json)**

- **`.NET Core Launch (web)`**: Debug padrão da API
- **`.NET Core Launch (console)`**: Debug no console interno
- **`.NET Core Attach`**: Anexar a processo em execução
- **`Debug API with Swagger`**: Debug abrindo automaticamente o Swagger na porta padrão
- **`Debug API with Swagger (Port 5000)`**: Debug abrindo Swagger na porta 5000

### 📋 **Tarefas Disponíveis (.vscode/tasks.json)**

- **`build`**: Compila toda a solution (Ctrl+Shift+P → "Tasks: Run Task")
- **`watch`**: Executa API com auto-reload
- **`Run API`**: Executa a API normalmente
- **`run-api-swagger`**: Executa API e prepara para Swagger
- **`publish`**: Publica a API para produção
- **`restore`**: Restaura dependências NuGet
- **`clean`**: Limpa arquivos de build
- **`test`**: Executa todos os testes

### ⌨️ **Como usar o Debug com Swagger**

1. **F5**: Inicia debug → Escolha "Debug API with Swagger"
2. **Swagger abre automaticamente** no navegador quando a API estiver pronta
3. **URL do Swagger**: `http://localhost:[porta]/swagger`
4. **Breakpoints**: Clique na margem esquerda do editor
5. **Ctrl+Shift+P** → "Tasks: Run Task" → "run-api-swagger" para execução simples

## Tecnologias

- **.NET 8**
- **ASP.NET Core Web API**
- **Clean Architecture**

## Configuração do VS Code

### 🔧 **Extensões Recomendadas**

O projeto inclui um arquivo `.vscode/extensions.json` com extensões recomendadas:

- **C# Dev Kit**: Suporte completo para C#
- **C#**: Syntax highlighting e IntelliSense
- **REST Client**: Para testar APIs
- **Namespace**: Gerenciamento automático de namespaces

### ⚙️ **Configurações do Workspace**

- **Format on Save**: Formatação automática ao salvar
- **Organize Imports**: Organização automática de imports
- **File Nesting**: Organização visual de arquivos relacionados
- **Semantic Highlighting**: Destaque semântico de código

## Próximos Passos

1. **Configurar Entity Framework** na camada Infrastructure
2. **Implementar autenticação/autorização**
3. **Adicionar testes unitários e de integração**
4. **Configurar logging** na camada Crosscutting
5. **Implementar validações** na camada Application
6. **Configurar Swagger/OpenAPI**
