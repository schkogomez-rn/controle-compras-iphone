# Controle de Compras (PWA)

Aplicativo PWA (Progressive Web App) para controle de compras, preços, mercados e leitura de códigos de barras. Funciona 100% offline em iPhones (iOS) e celulares Android.

---

## 🚀 Como Publicar Grátis no GitHub Pages

O projeto já está preparado com GitHub Actions para publicação automática com certificado HTTPS (essencial para câmera e PWA).

1. No seu repositório no GitHub: `https://github.com/schkogomez-rn/controle-compras-iphone`
2. Vá em **Settings** (Configurações) > **Pages** (no menu lateral esquerdo).
3. Na seção **Build and deployment**:
   - Em **Source**, selecione: **Deploy from a branch**
   - Em **Branch**, selecione: `main` e pasta `/ (root)`
   - Clique em **Save** (Salvar).
4. Em cerca de 1 a 2 minutos, o app estará publicado e acessível no endereço:
   👉 **`https://schkogomez-rn.github.io/controle-compras-iphone/`**

---

## 📱 Como Instalar e Usar no Celular

### No iPhone / iPad (iOS)
1. Abra o link acima no navegador **Safari**.
2. Toque no botão de **Compartilhar** (ícone do quadrado com seta para cima ⎋ na barra inferior).
3. Role a lista para baixo e toque em **Adicionar à Tela de Início** (ícone ＋).
4. Toque em **Adicionar** no canto superior direito.
5. O ícone do app aparecerá na tela de início do seu iPhone. Ao abrir, ele roda em tela cheia, como um aplicativo nativo da App Store.

### No Android
1. Abra o link acima no **Google Chrome**.
2. Aparecerá automaticamente um aviso ou botão **"Instalar aplicativo"** (ou toque nos três pontinhos **⋮** no canto superior direito e escolha **Instalar aplicativo** / **Adicionar à tela inicial**).
3. O app será instalado no seu aparelho e funcionará com ícone próprio e tela cheia.

---

## 🛠️ Tecnologias e Recursos
- **Progressive Web App (PWA)** com Service Worker e cache local.
- **Funcionamento Offline:** grava e consulta todos os dados no armazenamento local (`localStorage`), sem depender de servidor.
- **Leitor de Código de Barras (EAN/UPC):** suporte à câmera ao vivo e captura por foto em alta resolução com biblioteca ZXing.
- **🏬 Cadastros de Supermercados Visitados:** gestão de redes, filiais, endereços, dias especiais de feiras/ofertas e acompanhamento de gastos e visitas por mercado.
- **⚖️ Comparador de Produtos com Melhores Preços:** indicação visual de menores preços (`🏆 Melhor Preço`), cálculo automático de economia (em R$ e %), comparação equivalente por unidade base (R$/kg, R$/L, un), confronto direto entre 2 supermercados e ranking dos mais baratos.
- **Backup e Exportação:** exportação em CSV para Excel e backup completo em formato JSON.