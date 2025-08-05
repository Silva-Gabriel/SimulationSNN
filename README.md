# SnnProject

Este projeto segue os princípios da **Clean Architecture** e está organizado em camadas bem definidas.

## ✨ **Características Principais**

- 🏗️ **Clean Architecture** com separação clara de responsabilidades
- 🔧 **ASP.NET Core 8** Web API com Swagger integrado
- 🐛 **Debug otimizado** para VS Code com launch automático do Swagger
- 📦 **Estrutura organizada** sem subpastas desnecessárias
- ⚙️ **Configurações prontas** para desenvolvimento (.vscode/)
- 🔗 **Git configurado** e pronto para GitHub
- 📝 **Documentação completa** com instruções de uso

## Estrutura do Projeto

```
SnnProject/
├── .vscode/                       # Configurações do VS Code
│   ├── launch.json               # Configurações de debug
│   ├── tasks.json                # Tarefas de build/run
│   ├── settings.json             # Configurações do workspace
│   └── extensions.json           # Extensões recomendadas
├── Api/                          # Camada de apresentação (Web API)
│   ├── Program.cs
│   ├── SnnProject.Api.csproj
│   ├── appsettings.json
│   └── Properties/
├── Application/                  # Camada de aplicação (Casos de uso)
│   └── SnnProject.Application/
├── Domain/                       # Camada de domínio (Entidades e regras de negócio)
│   └── SnnProject.Domain/
├── Infrastructure/               # Camada de infraestrutura (Dados, serviços externos)
│   └── SnnProject.Infrastructure/
├── Crosscutting/                # Funcionalidades transversais (Logging, Utils, etc.)
│   └── SnnProject.Crosscutting/
├── SnnProject.sln               # Solution principal
├── README.md                    # Documentação do projeto
└── .gitignore                   # Arquivos ignorados pelo Git
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
dotnet run --project Api/SnnProject.Api.csproj
```

### Executar com watch (auto-reload)

```bash
dotnet watch run --project Api/SnnProject.Api.csproj
```

### Executar testes

```bash
dotnet test
```

## Debug no VS Code

O projeto está configurado com arquivos para debug no VS Code:

### 🐛 **Configuração de Debug (.vscode/launch.json)**

- **`Debug API with Swagger`**: Configuração única otimizada que:
  - ✅ Compila o projeto automaticamente
  - ✅ Inicia a API em modo debug
  - ✅ Detecta automaticamente a porta
  - ✅ Abre o Swagger no navegador

### 📋 **Tarefas Disponíveis (.vscode/tasks.json)**

- **`build`**: Compila toda a solution (tarefa padrão)
- **`watch`**: Executa API com auto-reload
- **`Run API`**: Executa a API normalmente
- **`run-api-swagger`**: Executa API e prepara para Swagger
- **`publish`**: Publica a API para produção
- **`restore`**: Restaura dependências NuGet
- **`clean`**: Limpa arquivos de build
- **`test`**: Executa todos os testes

### ⌨️ **Como usar o Debug com Swagger**

1. **F5** ou **Ctrl+F5**: Inicia automaticamente com Swagger
2. **Swagger abre automaticamente** no navegador
3. **Breakpoints**: Clique na margem esquerda do editor
4. **Tasks**: Ctrl+Shift+P → "Tasks: Run Task" → Escolher tarefa
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

## Controle de Versão

### 📦 **Git & GitHub**

O projeto está configurado com Git e pronto para GitHub:

- ✅ **Repositório Git inicializado**
- ✅ **.gitignore otimizado** para .NET
- ✅ **Commit inicial** realizado
- ✅ **Branch main** configurada

### 🚀 **Para conectar ao GitHub:**

1. **Crie um repositório** no GitHub
2. **Execute os comandos:**
   ```bash
   git remote add origin https://github.com/SEU_USUARIO/NOME_REPO.git
   git push -u origin main
   ```

### 📝 **Comandos Git úteis:**

```bash
# Adicionar mudanças
git add .

# Fazer commit
git commit -m "Sua mensagem"

# Enviar para GitHub
git push

# Ver status
git status
```

## Próximos Passos

1. **Configurar Entity Framework** na camada Infrastructure
2. **Implementar autenticação/autorização**
3. **Adicionar testes unitários e de integração**
4. **Configurar logging** na camada Crosscutting
5. **Implementar validações** na camada Application
6. **Configurar Swagger/OpenAPI**
