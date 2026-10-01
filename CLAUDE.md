# CLAUDE.md — Site João Tufanini

Este arquivo é lido automaticamente a cada mensagem. É a fonte da verdade do projeto.
A copy aprovada está em `docs/copy-aprovada.md` e não muda sem aprovação explícita.

---

## O que estamos construindo

Uma landing page de conversão, de página única, 15 seções. Cliente real.
Objetivo: um público executivo exigente entrar em contato pelo WhatsApp para
agendar um diagnóstico estratégico. É a única conversão da página.

## Regra de ouro

Esta página não pode parecer gerada por IA. O público é C-level e rejeita
qualquer coisa que pareça template, amadora ou motivacional. Profissionalismo
e sobriedade acima de tudo. Quando estiver em dúvida entre "chamativo" e
"sóbrio", escolha sóbrio.

## Cliente

João Tufanini, psicólogo, CRP 06/72.409, 22 anos de atuação clínica.
CEO da Clínica Íntegra. Pós em Criminologia e Investigação Criminal.
Graduate Dale Carnegie, Leadership Training for Managers, 1990.
Mentor de pilotos e equipes de rally profissional.
Especialista em NR-1 e riscos psicossociais.

## Oferta desta página

Mentoria estratégica de alta performance para CEOs e executivos, usando Gestalt
aplicada ao ambiente corporativo. **Não é terapia de consultório — é ferramenta
de gestão.** Essa distinção é o eixo da página e aparece na seção 4.

**Oferta-âncora: uma só, o líder no centro.** Mentoria em Gestalt aplicada à
liderança de alta performance. O comprador e o foco são sempre o líder. A
modalidade de entrega — o líder individualmente ou junto com a equipe dele — é
definida na conversa de diagnóstico e não compete no hero. Não estruturar dois
níveis na página. Todos os CTAs levam a agendar o diagnóstico.

Diagnóstico estratégico: primeira conversa de cerca de 30 minutos, online, para
entender o momento do líder e apresentar o método. É a porta de entrada da
mentoria. Preço final a definir. Agendado pelo WhatsApp.

## Público

Fundador, sócio ou C-level de empresa média a grande brasileira, 38 a 55 anos,
com autonomia de compra. Já contratou coach, mentoria ou consultoria. Tem
resistência declarada à palavra "terapia". Escaneia rápido, decide rápido.

## Tráfego

Google Ads, majoritariamente mobile. Termos: mentoria para líderes, mentoria
para CEOs, consultoria em liderança, desenvolvimento de lideranças, alta
performance corporativa, NR-1, riscos psicossociais, burnout empresarial.
A página corresponde à promessa desses termos.

## Conversão

Destino único: WhatsApp (11) 99718-8324, com mensagem pré-preenchida diferente
por seção para identificar a origem do lead.
Atendimento: [PREENCHER]
Medição existente: nenhuma tag instalada ainda. `assets/js/tracking.js` dispara um
evento de conversão no clique de cada CTA de WhatsApp, identificando a seção de
origem (`cta_section`). GA4 e Google Ads entram como tags depois, consumindo esses
eventos via `dataLayer`.

## Identidade visual

Linguagem consolidada no Instagram e LinkedIn do cliente:

- Fundo azul-marinho muito escuro a quase preto, faixa `#050B18` a `#0A1428`
- Azul elétrico como única cor de acento, faixa `#2E88F5` a `#4A9FFF`
- Fotografia corporativa noturna, iluminação cinematográfica, alto contraste
- Sans-serif condensada e pesada em títulos, caixa alta
- Nenhum tom quente na marca: sem laranja, vermelho, dourado ou verde

**Risco a resolver:** título condensado enorme com corpo muito pequeno funciona
numa peça social quadrada mas prejudica a leitura de uma página longa no celular.
Preservar o contraste tipográfico sem transformar o corpo de texto em legenda.

## Stack e restrições

- HTML, CSS e JS puros. Sem framework, sem build step, sem Node em produção.
- Locaweb, servidor compartilhado Linux. Plano: [PREENCHER]
- Destino: [PREENCHER — substitui site atual, subdomínio ou subpasta]
- Zero bibliotecas de interface. O navegador nativo dá conta de tudo aqui.
- Bibliotecas externas só via CDN e só se justificarem o peso em KB.

## Arquitetura de arquivos

```
index.html
assets/css/base.css          @layer, normalização, variáveis, fontes, estrutura
assets/css/components.css    botões, navegação, elementos repetidos, estados
assets/css/sections.css      particularidades de cada seção
assets/js/main.js            comportamentos de interface
assets/js/tracking.js        eventos de medição
assets/images/
assets/fonts/
docs/                        fora da publicação
```

Três CSS referenciados no HTML em ordem fixa. Sem `@import`. Cascata controlada
com `@layer`. Sem `!important`. Classes em kebab-case, nomeadas por função e não
por aparência.

## As 15 seções

1. hero
2. cenarios — identificação com a dor
3. prejuizo — dados financeiros do burnout e da má comunicação
4. diferenca — o que a Gestalt corporativa não é
5. metodo — o que é Gestalt aplicada a negócios
6. entregavel — o que a equipe aprende
7. metodologia — sigilo, acolhimento, foco prático e os três pilares
8. depoimentos
9. sobre — quem é João Tufanini
10. publicacoes
11. parceiros
12. linkedin
13. conversao — CTA em destaque
14. faq
15. contato — última chamada e rodapé

## Imagens

Entram só no final do projeto. Construir com placeholders que reservem proporção
e dimensões finais, com `data-attribute` indicando o arquivo previsto e as
dimensões mínimas, para que a troca não cause layout shift.

| Uso | Proporção | Mínimo | Quantidade |
|---|---|---|---|
| hero | 4:5 vertical | 1200×1500 | 1 |
| sobre | 4:5 vertical | 1000×1250 | 1 |
| publicações | 16:10 | 800×500 | 4 |
| parceiros | altura fixa, largura variável | PNG transparente | 5 |

## Performance é requisito, não etapa final

- Fontes com preconnect e display swap, só os pesos usados
- A imagem do hero precisa ser descoberta cedo pelo navegador. Nunca lazy nela.
- width e height explícitos em toda imagem
- Alvos, medidos em mobile e desktop separadamente: LCP até 2,5s, INP até 200ms, CLS até 0,1

## Conversão tem limite de medição

O clique no WhatsApp mede a ação no site, não comprova conversa nem agendamento.
Fechar esse ciclo exige retorno do atendimento ou CRM. Registrar isso, não ignorar.

## Vícios de IA a evitar

- Uma palavra do título em cor diferente do resto
- Rótulo em caixa alta com letter-spacing acima de cada heading
- Numeração 01/02/03 em conteúdo que não é sequência
- Seta anexada ao texto de botões e links
- Metadados unidos por ponto médio
- Mesmo border-radius em tudo, independente da hierarquia
- Mesma sombra cinza suave debaixo de cada card
- Gradiente usado como decoração
- Preto tingido (#0B0B0B, #111) no lugar da cor da marca
- Fonte monoespaçada em rótulos pequenos
- Animação de entrada idêntica em toda seção

## Critério de aceitação de cada seção

Antes de considerar uma seção pronta:

- Mobile e desktop validados em 360, 390, 768, 1024, 1440 e 1920
- Componentes compartilhados reutilizados, não recriados
- Nenhuma regra nova afetando seção anterior
- Teclado, foco visível, contraste 4.5:1, hierarquia de heading sem pular nível
- CTA funcionando com JavaScript desativado
- Placeholder de imagem com proporção travada
- Uma entrada em `docs/decisoes.md` e um commit

## Fluxo de trabalho

- `docs/decisoes.md` registra cada etapa concluída, com o que e por quê. Consultar antes de cada seção nova para não se contradizer.
- `docs/convencoes.md` guarda as convenções de código e design.
- Um commit por etapa. É o mecanismo de recuperação.
- Correções cirúrgicas e curtas, nunca refazer seção inteira por um detalhe.
