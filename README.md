# Innovatis Soluções em TI — Landing Page

Deploy no GitHub Pages com domínio customizado `innovatis.com.br`.

---

## Arquivos do projeto

- `index.html` — Página única (HTML + CSS + JS inline)
- `sitemap.xml` — Mapa do site para indexação
- `robots.txt` — Instruções para rastreadores
- `CNAME` — Domínio customizado (obrigatório para GitHub Pages)

---

## Passo a passo de deploy

### 1. Criar repositório no GitHub e subir os arquivos

```bash
git init
git add index.html sitemap.xml robots.txt CNAME
git commit -m "Initial commit: landing page Innovatis Soluções em TI"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git
git push -u origin main
```

Substitua `SEU_USUARIO` e `SEU_REPOSITORIO` pelos seus valores.

---

### 2. Ativar GitHub Pages

1. No GitHub, vá em **Settings → Pages**
2. Em **Source**, selecione **Deploy from a branch**
3. Branch: `main` | Folder: `/ (root)`
4. Clique em **Save**

O site ficará disponível em `https://SEU_USUARIO.github.io/SEU_REPOSITORIO/` em poucos minutos.

---

### 3. Configurar DNS no provedor do domínio

No painel do seu registrador (Registro.br, GoDaddy, Cloudflare, etc.), crie dois registros:

#### A) Registro A (domínio raiz → IPs do GitHub Pages)

| Tipo | Host/@ | Valor (IP) |
|------|--------|------------|
| A    | @      | 185.199.108.153 |
| A    | @      | 185.199.109.153 |
| A    | @      | 185.199.110.153 |
| A    | @      | 185.199.111.153 |

> **Importante:** Crie **4 registros A** separados, um para cada IP acima.

#### B) Registro CNAME (www → GitHub Pages)

| Tipo | Host | Valor |
|------|------|-------|
| CNAME | www | SEU_USUARIO.github.io |

Substitua `SEU_USUARIO` pelo seu username do GitHub.

---

### 4. Configurar domínio customizado no GitHub Pages

1. Ainda em **Settings → Pages**, role até **Custom domain**
2. Digite: `innovatis.com.br`
3. Clique em **Save**
4. Aguarde a verificação DNS (pode levar alguns minutos)

---

### 5. Ativar HTTPS

Assim que o domínio for verificado (check verde ✅), marque a opção **Enforce HTTPS**.

---

### 6. ⚠️ IMPORTANTE: Não apague o arquivo `CNAME`

O arquivo `CNAME` na raiz do repositório **é o que mantém o domínio customizado funcionando**. Se você apagá-lo e fizer commit, o GitHub Pages removerá a configuração do domínio e o site voltará para `usuario.github.io/repo`.

> **Nunca delete o `CNAME`** a menos que queira remover o domínio customizado.

---

### 7. Atualizações futuras

Qualquer novo `git push` na branch `main` atualiza o site automaticamente em poucos minutos. Não é necessário reconfigurar domínio nem SSL.

```bash
git add .
git commit -m "Atualização: descrição da mudança"
git push
```

---

### 8. Submeter ao Google Search Console (indexação)

1. Acesse https://search.google.com/search-console
2. **Adicionar propriedade** → tipo **URL prefix** → `https://innovatis.com.br/`
3. Verifique a propriedade:
   - **Opção A (recomendada):** Verificação via DNS — adicione o registro TXT fornecido no seu provedor de DNS
   - **Opção B:** Tag HTML — adicione a `<meta name="google-site-verification" content="...">` no `<head>` do `index.html` e faça novo deploy
4. Após verificado, vá em **Sitemaps** → adicione `sitemap.xml` → **Enviar**
5. Use **Inspeção de URL** → insira `https://innovatis.com.br/` → **Solicitar indexação**

---

## Personalização rápida

Edite no `index.html` (procure por `AJUSTE:`):

- **Telefone/WhatsApp:** `(31) 98288-8685` → `WA_NUMBER = '5531982888685'`
- **E-mail:** `innovatis.solucoes@gmail.com`
- **Horário:** `Seg–Sex 8h–18h, Sáb 8h–12h`
- **Estatísticas (contadores):** `data-count="5"`, `data-count="1200"`, `data-count="300"`, `data-count="100"`
- **Avaliações Google:** bloco comentado no JS (`ONDE PLUGAR A INTEGRAÇÃO REAL`)
- **Redes sociais (footer):** links `href="#"` → substitua pelos reais

---

## Tecnologias

- HTML5 semântico + CSS3 (custom properties, grid, flex)
- JavaScript vanilla (ES6+) — sem dependências externas
- Google Fonts: **Sora** (títulos) + **Inter** (corpo)
- Progressive enhancement: funciona sem JS
- `prefers-reduced-motion` e `prefers-color-scheme` respeitados
- Schema.org `LocalBusiness` + Open Graph + Twitter Cards

---

## Licença

Uso interno — Innovatis Soluções em TI.