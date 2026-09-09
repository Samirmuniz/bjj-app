# 🥋 Leandro Cardoso Jiu-Jitsu — Gestão de Alunos

App mobile e PWA focado na gestão prática de alunos para a academia **Leandro Cardoso Jiu-Jitsu**. Projetado para funcionar de forma **100% offline**, garantindo controle rápido e visual direto no celular do instrutor, sem depender de conexão com a internet.

---

## 📋 Funcionalidades Principal

- **Perfis de Alunos:** Cadastro contendo Nome, Telefone, Faixa, Graus, Mensalidade e Observações.
- **Exibição Visual da Faixa:** Representação gráfica realista da faixa de jiu-jitsu (cor principal + tarja e quantidade exata de graus).
- **Controle de Mensalidades:** Alternância de status de pagamento (`Pago` / `Pendente`) com apenas um toque no painel.
- **Chamada Dinâmica:** Registro de presença por data (padrão diário) com contador em tempo real e histórico vinculado ao perfil do aluno.
- **Painel Inicial (Dashboard):** Métricas rápidas com total de alunos, mensalidades pendentes e presenças registradas no dia.
- **Modo PWA (Progressive Web App):** Instalável no smartphone com ícone na tela inicial, carregamento instantâneo e execução em tela cheia.

---

## 🧱 Stack Técnica

O projeto preza pela simplicidade absoluta, performance e ausência de dependências pesadas na camada de interface:
- **Core:** HTML5, CSS3 e JavaScript Puro (Vanilla JS).
- **Armazenamento:** Persistência de dados local via `localStorage` do navegador/WebView.
- **Offline & Instalação:** Web App Manifest (`manifest.json`) e Service Workers (`sw.js`).
- **Build Nativo (Opcional):** Capacitor v6 para empacotamento Android (`.apk`).

---

## 📁 Estrutura do Projeto

```text
.
├── index.html              # Interface do app + lógica de negócios em Vanilla JS
├── manifest.json           # Metadados e configurações de instalação do PWA
├── sw.js                   # Service Worker responsável pelo cache offline
├── .gitattributes          # Normalização de finais de linha de texto
├── icons/
│   ├── icon-192.png        # Ícone de inicialização PWA (Resolução Média)
│   └── icon-512.png        # Ícone de inicialização PWA (Alta Resolução)
└── capacitor-project/      # Estrutura nativa para empacotamento Android
    ├── capacitor.config.json # Configurações globais do Capacitor
    ├── package.json        # Dependências do ecossistema Android/Capacitor
    └── www/                # Diretório espelho onde os arquivos Web são injetados
```

---

## ▶️ Como Executar Localmente

### Opção 1: Direto no Navegador (Uso Geral)
Não há necessidade de etapas de build ou ferramentas adicionais. Basta abrir o arquivo `index.html` com um duplo clique no seu navegador preferido.

### Opção 2: Simulação Completa PWA (Offline & Instalação)
Para testar o comportamento de Service Workers e a instalação do app no computador ou celular, você deve utilizar um servidor HTTP local (já que o protocolo `file://` bloqueia os recursos do PWA):

**Via Node.js:**
```bash
# Na raiz do projeto, instale e rode o pacote serve
npx serve .
```

**Via Python:**
```bash
# Se tiver o Python instalado em sua máquina
python3 -m http.server 8080
```
Abra o endereço gerado (ex: `http://localhost:8080`) no seu navegador.

---

## 📱 Gerando o APK para Android

O projeto utiliza o **Capacitor 6** para encapsular o código Web dentro de um ambiente nativo Android (`com.leandrocardoso.jiujitsu`). Existem dois caminhos principais para gerar o instalador `.apk`:

### Caminho Rápido: PWABuilder (Sem instalar nada)
1. Realize o deploy do seu código PWA em uma plataforma gratuita (como *Netlify Drop*, *Vercel* ou *GitHub Pages*).
2. Copie a URL gerada e cole no site [pwabuilder.com](https://pwabuilder.com).
3. Selecione a plataforma **Android**, clique em **Generate Package** e baixe o arquivo `.apk` pronto para instalar.

### Caminho Nativo: Localmente via Android Studio
Certifique-se de ter o **Node.js** e o **Android Studio** instalados em sua máquina.

```bash
# 1. Acesse a pasta do projeto Capacitor
cd capacitor-project

# 2. Instale as dependências necessárias do CLI do Capacitor
npm install

# 3. Sincronize o código da pasta web com o ambiente Android
npx cap sync android

# 4. Abra o projeto no Android Studio
npx cap open android
```
**No Android Studio:** Aguarde o Gradle sincronizar, vá no menu superior em **Build** ➡️ **Build Bundle(s) / APK(s)** ➡️ **Build APK(s)**. O arquivo `.apk` de teste será gerada na pasta do projeto.

---

## 💾 Sobre a Privacidade e os Dados

- **Privacidade Total:** Os dados de alunos e histórico permanecem confinados unicamente dentro do aparelho onde o aplicativo está rodando.
- **Sem Sincronização em Nuvem:** Por operar de forma puramente local, as informações não são compartilhadas ou sincronizadas de forma automática entre múltiplos celulares.
- **Atenção:** Apagar o cache do navegador ou desinstalar o aplicativo no celular resultará na exclusão definitiva dos dados salvos.

---

## 📄 Licença

Uso estrito e interno da **Academia Leandro Cardoso Jiu-Jitsu**. Todos os direitos reservados.
