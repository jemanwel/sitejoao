[README.md](https://github.com/user-attachments/files/32885314/README.md)
# Site João Tufanini

Landing page de conversão, de página única (15 seções), para a mentoria
estratégica de alta performance de **João Tufanini** (psicólogo, CRP 06/72.409).
Objetivo único: o visitante agendar um diagnóstico estratégico pelo WhatsApp.

---

## Stack

- HTML, CSS e JavaScript puros. **Sem framework, sem build, sem Node.**
- **Zero dependências externas em runtime:** fontes auto-hospedadas (woff2) e
  imagens em WebP, tudo servido do próprio domínio.
- Não há nada pra instalar nem compilar. É só servir os arquivos estáticos.

---

## Como rodar localmente

Requisito: qualquer servidor de arquivos estáticos. O mais simples, já incluso
no macOS e no Linux, é o Python 3. Na raiz do projeto:

```bash
python3 -m http.server 4599
```

Depois abra no navegador:

```
http://localhost:4599
```

Para parar o servidor: `Ctrl + C` no terminal.

### Alternativas

- **Node:** `npx serve` ou `npx http-server -p 4599`
- **PHP:** `php -S localhost:4599`
- **VS Code:** extensão *Live Server* (botão "Go Live")

A porta `4599` é só a convenção do projeto — qualquer porta livre serve.

> Para uma espiada rápida dá pra abrir o `index.html` direto no navegador
> (`file://`), mas prefira o servidor local: reproduz a produção com fidelidade
> (tipos MIME corretos, caminhos e cache).

---

## Estrutura

```
index.html                 página única, 15 seções
assets/css/
  base.css                 @layer, tokens, fontes, reset, tipografia, layout
  components.css           botões, navegação, elementos repetidos, estados
  sections.css             particularidades de cada seção
assets/js/
  main.js                  comportamentos de interface (revelação, menu, etc.)
  tracking.js              eventos de medição (dataLayer) nos CTAs de WhatsApp
assets/fonts/              Cinzel, Cormorant Garamond, IBM Plex Sans (woff2)
assets/images/             imagens em .webp (+ originais .jpg/.png)
docs/                      documentação do projeto (fora da publicação)
CLAUDE.md                  regras e fonte da verdade do projeto
```

Os três CSS são carregados em ordem fixa no HTML e a cascata é controlada por
`@layer` (ordem: `reset, tokens, base, layout, components, sections, utilities`).
Sem `@import`, sem `!important`, classes em kebab-case.

---

## Publicação (produção)

Site estático: basta enviar os arquivos para a pasta pública do servidor (na
Locaweb, `public_html`). Sobem apenas **`index.html` e a pasta `assets/`** —
`docs/`, `CLAUDE.md` e afins ficam fora do ar.

Notas de performance (o tráfego é pago, majoritariamente mobile):

- A imagem do hero **nunca** deve ser `lazy` — é o LCP, precisa ser descoberta cedo.
- Mantenha `width`/`height` explícitos nas imagens para evitar layout shift.
- Em produção, sirva sob **HTTPS** e com gzip/cache nos estáticos.

---

## Conversão e medição

Conversão única: **WhatsApp (11) 99718-8324**, com mensagem pré-preenchida
diferente por seção (para identificar a origem do lead). `assets/js/tracking.js`
dispara um evento no `dataLayer` a cada clique de CTA de WhatsApp, identificando
a seção de origem (`cta_section`). GA4 e Google Ads consomem esses eventos quando
as tags forem instaladas.

O clique no WhatsApp mede a ação no site, não comprova a conversa nem o
agendamento — fechar esse ciclo depende do retorno do atendimento ou do CRM.

---

## Conteúdo

A copy aprovada está em [`docs/copy-aprovada.md`](docs/copy-aprovada.md) e é a
**fonte da verdade**. Não altere textos sem aprovação. As decisões de projeto
ficam registradas em [`docs/decisoes.md`](docs/decisoes.md) e as convenções de
código e design em [`docs/convencoes.md`](docs/convencoes.md).
