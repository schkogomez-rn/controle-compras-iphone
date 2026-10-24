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
- **✨ Leitura Direta por IA de Fotos de Produtos:** visão computacional multimodal (Google Gemini Vision: Gemini 1.5/2.0 Flash) que analisa a foto da embalagem, rótulo ou etiqueta de preço e extrai automaticamente nome, marca, peso/conteúdo, unidade, código de barras e preço da gôndola.
- **📚 Banco de Dados Central de Produtos (Catálogo):** cadastro permanente e detalhado de produtos com fotos, códigos EAN, marcas, categorias e preços de referência, com auto-completar inteligente, consulta à base global Open Food Facts e pré-carregamento de itens essenciais.
- **Leitor de Código de Barras (EAN/UPC):** suporte à câmera ao vivo e captura por foto em alta resolução com biblioteca ZXing.
- **🏬 Cadastros de Supermercados Visitados:** gestão de redes, filiais, endereços, dias especiais de feiras/ofertas e acompanhamento de gastos e visitas por mercado.
- **📍 Recomendador de Supermercados de Natal (RN) - CNAE 4711-3/02:** indicação inteligente de supermercados em Natal para qualquer produto com base no menor preço histórico ou dias de feiras/ofertas nos bairros (Cidade da Esperança, Lagoa Nova, Tirol, Capim Macio, Ponta Negra, Candelária, Alecrim, Zona Norte, etc.), com integração com a API CNPJ (cnpja.com) e catálogo verificado offline de 14 redes.
- **⚖️ Comparador de Produtos com Melhores Preços:** indicação visual de menores preços (`🏆 Melhor Preço`), cálculo automático de economia (em R$ e %), comparação equivalente por unidade base (R$/kg, R$/L, un), confronto direto entre 2 supermercados e ranking dos mais baratos.
- **Backup e Exportação:** exportação em CSV para Excel e backup completo em formato JSON incluindo catálogo de produtos e histórico.

---

## 📍 Módulo Standalone: Sugestão de Supermercados em Natal (RN)

O projeto inclui o módulo ES6+ [`sugestao-supermercado-natal.js`](file:///e:/SistemaDeCompras/ControledeCompras_iPhone_PWA/controle-compras-iphone/sugestao-supermercado-natal.js), pronto para ser executado no Node.js ou importado em outras aplicações:

```bash
# Indicação de supermercado por produto:
node sugestao-supermercado-natal.js "Arroz 5kg"
node sugestao-supermercado-natal.js "Feijão" "Cidade da Esperança"

# Inserção/cadastro dos supermercados de Cidade da Esperança (RedeMAIS & Superfácil):
node sugestao-supermercado-natal.js --inserir
```

### Exemplo de uso como módulo em JavaScript:
```javascript
import { 
  indicarSupermercado, 
  inserirSupermercados, 
  SUPERMERCADOS_CIDADE_ESPERANCA 
} from './sugestao-supermercado-natal.js';

// 1. Indicação inteligente no bairro Cidade da Esperança:
const resultado = await indicarSupermercado({
  produto: 'Arroz 5kg',
  bairro: 'Cidade da Esperança' // RedeMAIS / Superfácil
});

console.log(resultado.supermercado.nome);       // Ex.: RedeMAIS - Cidade da Esperança
console.log(resultado.supermercado.enderecoFormatado);
console.log(resultado.motivo);                  // Ex.: Menor preço histórico ou dia de feira
console.log(resultado.supermercado.mapsUrl);    // Link direto para rota no Google Maps

// 2. Inserção / cadastro via API REST ou banco de dados:
await inserirSupermercados(SUPERMERCADOS_CIDADE_ESPERANCA, {
  apiUrl: 'https://sua-api.com/supermercados',
  apiToken: 'SEU_TOKEN_AQUI'
});
```