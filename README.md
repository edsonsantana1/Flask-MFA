# Flask MFA v2 – Autenticação Multifator com Dashboard

Um projeto educacional que demonstra a implementação de **autenticação multifator (MFA)** em uma aplicação web Flask, incluindo login, registro de usuários e um dashboard interativo com estatísticas de uso.

## 🔗 Links Rápidos

| Tipo | Link |
| 
| **Deploy no Render** Acessar Aplicação `https://flask-mfa-zc12.onrender.com` |
| **Repositório GitHub** | `https://github.com/edsonsantana1/Flask-MFA.git` |

---

## 🎯 Visão Geral

Este projeto demonstra uma aplicação web completa em **Flask** com funcionalidades de segurança moderna. Ele foi desenvolvido para fins educacionais, permitindo que desenvolvedores entendam como implementar autenticação multifator (MFA) usando TOTP (Time-based One-Time Password) em uma aplicação web.

### Principais Características

A aplicação oferece as seguintes funcionalidades:

| Funcionalidade | Descrição |
| 
| **Autenticação de Usuário** | Sistema de login e registro com validação de credenciais |
| **MFA com TOTP** | Autenticação multifator usando Google Authenticator ou Microsoft Authenticator |
| **QR Code Dinâmico** | Geração automática de QR Code para configuração do MFA |
| **Dashboard Interativo** | Visualização de estatísticas de uso e informações da sessão |
| **API JSON** | Endpoints para retornar dados em formato JSON |
| **Design Responsivo** | Interface construída com Bootstrap para funcionar em todos os dispositivos |
| **Pronto para Deploy** | Configuração incluída para deploy na plataforma Render |

---

## 🧰 Tecnologias Utilizadas

A aplicação foi construída utilizando as seguintes tecnologias e bibliotecas:

| Tecnologia | Versão | Propósito |
| 
| **Python** | 3.8+ | Linguagem de programação |
| **Flask** | 2.0+ | Framework web |
| **Jinja2** | Integrado | Motor de templates HTML |
| **Bootstrap** | 5.x | Framework CSS responsivo |
| **pyotp** | 2.8+ | Geração e validação de TOTP |
| **qrcode** | 7.3+ | Geração de QR Code |
| **Pillow** | 9.0+ | Processamento de imagens (dependência do qrcode) |
| **gunicorn** | 20.0+ | Servidor WSGI para produção |

---

## 📁 Estrutura do Projeto

A organização dos arquivos segue uma estrutura clara e modular, facilitando a manutenção e expansão:

```
flask_mfa_render_v2/
├── app.py                      # Aplicação Flask principal
├── requirements.txt            # Dependências Python
├── render.yaml                 # Configuração de deploy na Render
├── .gitignore                  # Arquivos ignorados pelo Git
├── README.md                   # Este arquivo
│
├── static/                     # Arquivos estáticos
│   └── styles.css              # Estilos CSS customizados
│
└── templates/                  # Templates HTML (Jinja2)
    ├── base.html               # Layout base (header, footer, navegação)
    ├── index.html              # Página inicial / landing page
    ├── register.html           # Formulário de registro de novo usuário
    ├── login.html              # Formulário de login
    ├── mfa_setup.html          # Exibição de QR Code e chave TOTP
    ├── mfa_verify.html         # Verificação do código MFA (6 dígitos)
    └── dashboard.html          # Dashboard com estatísticas e informações
```

### Descrição dos Arquivos Principais

**app.py**: Contém toda a lógica da aplicação Flask, incluindo rotas de autenticação, geração de QR Code, validação de TOTP e gerenciamento de sessões.

**requirements.txt**: Lista todas as dependências Python necessárias para executar a aplicação. Inclui Flask, pyotp, qrcode e outras bibliotecas essenciais.

**render.yaml**: Arquivo de configuração específico para deploy automático na plataforma Render. Define variáveis de ambiente, comandos de build e configurações de servidor.

**templates/base.html**: Template base que define a estrutura HTML comum a todas as páginas, incluindo navegação, header e footer.

**static/styles.css**: Arquivo de estilos CSS customizados que complementam o Bootstrap, permitindo personalizações visuais específicas da aplicação.

---

## ⚙️ Instalação e Configuração

### Pré-requisitos

Antes de começar, certifique-se de ter os seguintes itens instalados em seu sistema:

- **Python 3.8 ou superior**: Verifique com `python3 --version`
- **pip** (gerenciador de pacotes Python): Geralmente incluído com Python
- **Git** (opcional, mas recomendado): Para clonar o repositório

### Passos de Instalação Local

Siga os passos abaixo para configurar o projeto em seu ambiente local:

**1. Clone o repositório** (ou extraia os arquivos):

```bash
git clone https://github.com/edsonsantana1/Flask-MFA.git
cd flask_mfa_render_v2
```

**2. Crie um ambiente virtual Python**:

```bash
python3 -m venv venv
```

**3. Ative o ambiente virtual**:

No **macOS/Linux**:
```bash
source venv/bin/activate
```

No **Windows** (PowerShell):
```powershell
venv\Scripts\Activate.ps1
```

No **Windows** (CMD):
```cmd
venv\Scripts\activate.bat
```

**4. Instale as dependências**:

```bash
pip install -r requirements.txt
```

**5. Configure a variável de ambiente para a chave secreta**:

No **macOS/Linux**:
```bash
export APP_SECRET='sua_chave_secreta_muito_segura_aqui'
```

No **Windows** (PowerShell):
```powershell
$env:APP_SECRET='sua_chave_secreta_muito_segura_aqui'
```

> **Dica de Segurança**: Use uma chave secreta forte com pelo menos 32 caracteres, incluindo letras maiúsculas, minúsculas, números e caracteres especiais.

**6. Execute a aplicação**:

```bash
python app.py
```

A aplicação estará disponível em `http://localhost:5000`.

---

## 🚀 Como Usar

### Primeiro Acesso

Ao acessar a aplicação pela primeira vez, você será direcionado para a página inicial. A partir daí, você pode:

1. **Registrar uma nova conta**: Clique em "Registrar" e preencha o formulário com um nome de usuário e senha
2. **Fazer login**: Use suas credenciais para acessar a aplicação
3. **Configurar MFA**: Após o login, você será solicitado a configurar a autenticação multifator

### Fluxo Típico de Uso

**Passo 1: Registro**

Acesse a página de registro e crie uma nova conta fornecendo:
- Nome de usuário (único)
- Senha (recomenda-se usar uma senha forte)

**Passo 2: Login**

Faça login com suas credenciais na página de login.

**Passo 3: Configuração de MFA**

Após o login bem-sucedido, você será redirecionado para a página de configuração de MFA. Nesta página, você verá:
- Um **QR Code** para escanear com seu aplicativo autenticador
- Uma **chave secreta** (backup) para recuperação em caso de perda do dispositivo

**Passo 4: Verificação de MFA**

Escaneie o QR Code com um aplicativo autenticador (Google Authenticator, Microsoft Authenticator, Authy, etc.) e insira o código de 6 dígitos gerado para verificar a configuração.

**Passo 5: Acesso ao Dashboard**

Após a verificação bem-sucedida, você terá acesso ao dashboard com estatísticas de uso e informações da sua sessão.

### Usuário de Demonstração

Para testar rapidamente a aplicação sem criar uma nova conta, use as seguintes credenciais:

| Campo | Valor |
| 
| **Usuário** | `demo` |
| **Senha** | `password` |

> **Nota**: Este usuário de demonstração é pré-criado apenas para fins de teste. Em produção, remova ou altere essas credenciais.

---

## ✨ Funcionalidades Principais

### 1. Autenticação de Usuário

A aplicação implementa um sistema de autenticação seguro com:

- Validação de credenciais no login
- Proteção contra força bruta (pode ser expandida)
- Sessões seguras com Flask
- Logout seguro com limpeza de sessão

### 2. Autenticação Multifator (MFA) com TOTP

A implementação de MFA utiliza o padrão TOTP (Time-based One-Time Password), que é:

- **Seguro**: Baseado em algoritmo HMAC-SHA1
- **Compatível**: Funciona com qualquer aplicativo autenticador padrão
- **Offline**: Não requer conexão com internet para gerar códigos
- **Regenerável**: Novos códigos são gerados a cada 30 segundos

### 3. Geração de QR Code

A aplicação gera dinamicamente um QR Code que contém:

- Identificação da aplicação (AgroSilo MFA)
- Nome de usuário
- Chave secreta TOTP criptografada

O QR Code é codificado em base64 e exibido diretamente no navegador, sem necessidade de salvar arquivos.

### 4. Dashboard com Estatísticas

O dashboard fornece informações úteis sobre a sessão do usuário:

- Nome de usuário autenticado
- Hora de login
- Número de acessos ao dashboard
- Informações de segurança (MFA ativado)
- Opção de logout

### 5. API JSON

A aplicação oferece endpoints de API para integração com outras aplicações:

```bash
GET /api/stats
```

Retorna estatísticas em formato JSON:

```json
{
  "username": "demo",
  "mfa_enabled": true,
  "login_time": "2024-01-15 10:30:45",
  "dashboard_visits": 5
}
```

---

## 🔐 Fluxo de Autenticação

O diagrama abaixo ilustra o fluxo completo de autenticação na aplicação:

```
┌─────────────────────────────────────────────────────────────┐
│                    FLUXO DE AUTENTICAÇÃO                    │
└─────────────────────────────────────────────────────────────┘

    ┌──────────────┐
    │  Página      │
    │  Inicial     │
    └──────┬───────┘
           │
    ┌──────▼──────────────┐
    │  Registrar ou       │
    │  Fazer Login?       │
    └──────┬──────────────┘
           │
    ┌──────┴──────────────────────────┐
    │                                 │
┌───▼────────┐              ┌────────▼──────┐
│  Registrar │              │  Fazer Login  │
│  Novo User │              │               │
└───┬────────┘              └────────┬──────┘
    │                                │
    │ (Usuário criado)              │ (Credenciais válidas)
    │                                │
    └────────────┬────────────────────┘
                 │
         ┌───────▼────────────┐
         │  Configurar MFA    │
         │  (Exibir QR Code)  │
         └───────┬────────────┘
                 │
         ┌───────▼────────────────┐
         │  Escanear QR Code com  │
         │  Aplicativo Autenticador│
         └───────┬────────────────┘
                 │
         ┌───────▼────────────────┐
         │  Inserir Código TOTP   │
         │  (6 dígitos)           │
         └───────┬────────────────┘
                 │
         ┌───────▼────────────────┐
         │  Código Válido?        │
         └───────┬────────────────┘
                 │
         ┌───────▼────────────────┐
         │  Acesso ao Dashboard   │
         │  (Sessão Ativa)        │
         └────────────────────────┘
```



