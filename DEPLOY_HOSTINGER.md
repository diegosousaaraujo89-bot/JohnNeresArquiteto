# Deploy na Hostinger — John Neres Arquiteto

## Opção 1: Upload direto da pasta /dist (mais simples)

1. Acesse o **hPanel da Hostinger** → File Manager
2. Navegue até `public_html` e **delete** todos os arquivos existentes
3. Faça upload de **todos os arquivos dentro da pasta `/dist`**:
   - `index.html`
   - `assets/` (pasta completa)
   - `.htaccess`
   - `robots.txt`
   - `sitemap.xml`
4. Pronto — o site estará online

> ⚠️ O `.htaccess` é obrigatório para as rotas React funcionarem.
> Se não aparecer no File Manager, ative "Mostrar arquivos ocultos".

---

## Opção 2: Build local + FTP

```bash
# 1. Instalar dependências
npm install

# 2. Gerar build de produção
npm run build

# 3. Subir a pasta /dist via FTP para public_html
```

---

## Opção 3: GitHub + Deploy automático (recomendado para atualizações futuras)

1. Suba este projeto para um repositório GitHub
2. No hPanel → **Git** → conecte o repositório
3. Configure o build command: `npm install && npm run build`
4. Configure o publish directory: `dist`
5. Cada `git push` fará deploy automático

---

## Domínio personalizado

- No hPanel → **Domínios** → aponte para `public_html`
- Aguarde propagação de DNS (até 24h)
- Ative **SSL gratuito** em: hPanel → SSL → Let's Encrypt

---

## Estrutura dos arquivos para upload

```
public_html/
├── index.html        ← página principal
├── .htaccess         ← roteamento SPA (OBRIGATÓRIO)
├── robots.txt
├── sitemap.xml
└── assets/
    └── index-XXXXX.js   ← todo o site compilado
```
