# Publicação na Microsoft Store (MSIX)

Este diretório contém os artefatos necessários para empacotar e publicar o aplicativo na Microsoft Store usando MSIX/Windows App SDK.

Conteúdo:
- Package.appxmanifest: Manifesto do pacote (identidade, recursos, dependências e capacidades)
- wapproj.xml: Projeto de empacotamento (Desktop Bridge)
- Assets/: logos e splash

Passos locais (PowerShell):
1. Instale o Windows 10/11 SDK e o Windows App SDK (VS Installer)
2. Certifique-se que o certificado de assinatura (.pfx) está instalado no CurrentUser\Personal
3. Build e gerar pacote:
   - dotnet restore
   - dotnet build
   - Em seguida, use o Visual Studio para "Empacotar Aplicativo" (gerar MSIX) ou use MakeAppx/SignTool

Via linha de comando (exemplo):
- makeappx pack /d "Microsoft Store" /p "SmartCRM_AI.msix"
- signtool sign /fd SHA256 /a /f "certificado.pfx" "SmartCRM_AI.msix"

Publicar na Store:
- Acesse o Partner Center, crie o app, reserve o nome, e envie o .msix/.msixupload

Observação:
- Ajuste o Identity Publisher/Name/Version do Package.appxmanifest conforme o app reservado no Partner Center.
- Se quiser automatizar no CI (GitHub Actions), crie secrets para o PFX e utilize a ação windows-store.
