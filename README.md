# SmartCRM AI - Microsoft Store Publishing

Este repositório contém todos os artefatos necessários para empacotar e publicar o **SmartCRM AI** na Microsoft Store usando MSIX.

## 📁 Estrutura do Projeto

```
📦 smartcrm-ai-store
├── .github/workflows/
│   └── msix-build.yml              # Automação CI/CD para build MSIX
├── Microsoft Store/
│   ├── Assets/
│   │   └── readme.txt              # Lista de assets necessários (logos, splash screen)
│   ├── Package.appxmanifest       # Manifesto MSIX (identidade, capacidades, recursos)
│   ├── wapproj.xml                # Projeto de empacotamento Windows App
│   └── README-PUBLISH.md          # Guia completo de publicação
└── README.md                      # Este arquivo
```

## 🚀 Publicação Rápida

### 1. **Preparar Assets**
Criar imagens PNG nas dimensões especificadas em `Microsoft Store/Assets/readme.txt`:
- Logo principal: 300x300px
- Logo pequeno: 88x88px  
- Splash screen: 620x300px
- Entre outros...

### 2. **Configurar Manifesto**
Editar `Package.appxmanifest` com:
- **Identity Name/Publisher**: Conforme reservado no Partner Center
- **Version**: Versão do aplicativo (ex: 1.0.1.0)

### 3. **Build Local**
```powershell
# Clone este repositório
git clone https://github.com/ElAvila-eng/smartcrm-ai-store.git

# Navegar para o diretório
cd smartcrm-ai-store

# Executar build MSIX (requer Windows SDK)
makeappx pack /d "Microsoft Store" /p "SmartCRM_AI.msix"
```

### 4. **Build Automatizado (CI/CD)**
O workflow GitHub Actions em `.github/workflows/msix-build.yml` automatiza:
- ✅ Build do projeto .NET
- ✅ Criação do pacote MSIX
- ✅ Upload de artefatos
- 🔧 Assinatura digital (opcional, via secrets)
- 🔧 Deploy automático na Store (opcional)

## 📋 Checklist de Publicação

- [ ] Assets criados conforme dimensões especificadas
- [ ] Manifesto atualizado com dados corretos do Partner Center
- [ ] App testado localmente via MSIX
- [ ] Conta de desenvolvedor Microsoft ativa
- [ ] App reservado no Partner Center
- [ ] Certificado de assinatura configurado (opcional para CI/CD)

## 🔗 Links Úteis

- [Microsoft Partner Center](https://partner.microsoft.com/dashboard)
- [Documentação MSIX](https://docs.microsoft.com/windows/msix/)
- [Guias de Design da Microsoft Store](https://docs.microsoft.com/windows/apps/design/)

## 🛠️ Tecnologias

- **MSIX**: Formato de pacote moderno do Windows
- **GitHub Actions**: CI/CD automatizado
- **Windows App SDK**: Framework para apps modernos
- **.NET 8**: Runtime da aplicação

---

**© 2025 Zelo CRM - SmartCRM AI System**