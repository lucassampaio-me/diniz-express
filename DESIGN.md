# DESIGN.md — Diniz Express Landing Page

> Design system para uso no Claude Artifacts / Claude Design.
> Escopo: landing page única com objetivo de conversão via WhatsApp.

---

## 1. Identidade e Direção Visual

**Conceito:** "Urban Precision" — a brutalidade urbana da marca original filtrada por uma estrutura tipográfica limpa e espaçamento premium. Não é suavizar a marca — é elevar a densidade sem perder a contundência.

**Referências visuais principais:**
- DNA existente: peças gráficas da Diniz Express (azul marinho, bold, urbano)
- Elevação: Logix (estrutura limpa, seções bem separadas, tipografia hierárquica) + RapidHaul (cards com espaçamento generoso, contraste alto)
- Evitar: estética genérica de logística (stock photo de caminhão + gradiente azul sem personalidade)

**O que deve ser INESQUECÍVEL:** o contraste entre a força tipográfica pesada dos headlines e a limpeza cirúrgica do espaçamento. A marca soa confiável, não barata.

---

## 2. Sistema de Cores

```css
:root {
  /* Primárias */
  --color-navy:        #0B1E36;   /* fundo escuro, hero, footer */
  --color-blue:        #1565C0;   /* cor primária da marca */
  --color-blue-light:  #1E88E5;   /* hover, destaques interativos */
  --color-blue-glow:   #2979FF;   /* acentos no logo, glows */

  /* Neutras */
  --color-white:       #FFFFFF;
  --color-off-white:   #F5F7FA;   /* fundo de seções claras */
  --color-gray-light:  #E8ECF0;   /* bordas, divisores */
  --color-gray-mid:    #8A9BB0;   /* texto secundário */
  --color-gray-dark:   #2C3E50;   /* texto em fundo claro */

  /* Acento / Urgência */
  --color-alert:       #D32F2F;   /* taxa de cancelamento, alertas */
  --color-whatsapp:    #25D366;   /* botões WhatsApp exclusivamente */

  /* Gradiente de marca */
  --gradient-hero: linear-gradient(160deg, #0B1E36 0%, #0D2B4E 60%, #0F3460 100%);
  --gradient-blue: linear-gradient(135deg, #1565C0, #2979FF);
}
```

**Regras de uso:**
- `--color-navy` é o fundo dominante do Hero e Footer
- Seções intermediárias alternam entre `--color-off-white` e `--color-white` para respiração
- `--color-whatsapp` aparece **exclusivamente** nos CTAs de WhatsApp — nunca como cor decorativa
- `--color-alert` apenas para taxa de cancelamento / avisos críticos

---

## 3. Tipografia

```css
/* Google Fonts: Barlow Condensed (display) + Barlow (body) */
@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@600;700;800;900&family=Barlow:wght@400;500;600&display=swap');

:root {
  --font-display: 'Barlow Condensed', sans-serif;  /* headlines, seção títulos */
  --font-body:    'Barlow', sans-serif;             /* corpo, labels, UI */
}
```

**Escala tipográfica:**

| Token          | Fonte            | Peso | Tamanho  | Uso                          |
|----------------|------------------|------|----------|------------------------------|
| `--t-hero`     | Barlow Condensed | 900  | 64–80px  | Headline do Hero             |
| `--t-h2`       | Barlow Condensed | 800  | 40–52px  | Títulos de seção             |
| `--t-h3`       | Barlow Condensed | 700  | 28–32px  | Subtítulos, cards de serviço |
| `--t-lead`     | Barlow           | 500  | 18–20px  | Subheadlines, leads          |
| `--t-body`     | Barlow           | 400  | 16px     | Corpo de texto               |
| `--t-small`    | Barlow           | 400  | 14px     | Labels, legendas, meta       |
| `--t-cta`      | Barlow Condensed | 700  | 18px     | Texto de botões              |

**Regras:**
- Headlines em `uppercase` com `letter-spacing: -0.02em` — cria a tensão correta
- Nunca usar Barlow Condensed em peso abaixo de 600 para texto visível
- Line-height de corpo: `1.65` | Headlines: `1.0–1.1`

---

## 4. Espaçamento e Grid

```css
:root {
  --space-xs:   4px;
  --space-sm:   8px;
  --space-md:   16px;
  --space-lg:   24px;
  --space-xl:   40px;
  --space-2xl:  64px;
  --space-3xl:  96px;
  --space-4xl:  128px;

  --container:  1140px;
  --container-narrow: 720px;

  --radius-sm:  4px;
  --radius-md:  8px;
  --radius-lg:  16px;
  --radius-pill: 100px;
}
```

**Grid:** 12 colunas, gutter de 24px. Em mobile: 4 colunas, gutter 16px.

**Regra de seções:** padding vertical mínimo de `--space-3xl` (96px) em desktop. Seções escuras e claras se alternam para criar ritmo visual sem elementos decorativos desnecessários.

---

## 5. Componentes

### 5.1 Botões

**CTA WhatsApp (primário):**
```css
.btn-whatsapp {
  background: var(--color-whatsapp);
  color: #000;
  font: 700 18px/1 var(--font-display);
  text-transform: uppercase;
  letter-spacing: 0.04em;
  padding: 18px 32px;
  border-radius: var(--radius-pill);
  display: inline-flex;
  align-items: center;
  gap: 10px;
  box-shadow: 0 4px 24px rgba(37, 211, 102, 0.35);
  transition: transform 0.2s, box-shadow 0.2s;
}
.btn-whatsapp:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(37, 211, 102, 0.5);
}
```

**Secundário (outline):**
```css
.btn-outline {
  border: 2px solid var(--color-blue-light);
  color: var(--color-blue-light);
  background: transparent;
  font: 700 16px/1 var(--font-display);
  text-transform: uppercase;
  padding: 14px 28px;
  border-radius: var(--radius-pill);
  transition: background 0.2s, color 0.2s;
}
.btn-outline:hover {
  background: var(--color-blue-light);
  color: white;
}
```

### 5.2 Cards de Serviço

Estrutura: ícone do veículo + nome do serviço + faixa de preço + linha de capacidade/cobertura. Fundo `--color-white` com borda `1px solid --color-gray-light` e sombra sutil. Hover: borda azul + elevação de sombra.

```css
.service-card {
  background: var(--color-white);
  border: 1px solid var(--color-gray-light);
  border-radius: var(--radius-lg);
  padding: var(--space-xl);
  transition: border-color 0.2s, box-shadow 0.2s, transform 0.2s;
}
.service-card:hover {
  border-color: var(--color-blue);
  box-shadow: 0 8px 32px rgba(21, 101, 192, 0.12);
  transform: translateY(-4px);
}
```

### 5.3 Badge / Tag

```css
.badge {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  background: rgba(21, 101, 192, 0.1);
  color: var(--color-blue-light);
  font: 600 13px/1 var(--font-body);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  padding: 6px 14px;
  border-radius: var(--radius-pill);
  border: 1px solid rgba(21, 101, 192, 0.2);
}
```
Usado antes de títulos de seção (ex: "NOSSOS SERVIÇOS", "POR QUE DINIZ").

### 5.4 Divisor de Seção

Linha `1px solid --color-gray-light` com padding vertical. Nunca usar `<hr>` estilizado; usar div com border-top.

### 5.5 Item de Benefício

Ícone SVG (24px, `--color-blue`) + título em `--t-h3` + descrição em `--t-body`. Layout em grid 2-col no desktop.

### 5.6 Accordion (FAQ)

Fundo `--color-off-white`, borda inferior `--color-gray-light`. Título em Barlow 600 16px. Animação de abertura com `max-height` transition. Ícone `+` / `−` em `--color-blue`.

### 5.7 Sticky WhatsApp Button

Posição `fixed` bottom-right, 60px, ícone WhatsApp branco, fundo `--color-whatsapp`, `z-index: 100`. Pulse animation de 2s para chamar atenção sem irritar.

---

## 6. Estrutura de Seções

### Ordem e fundo:

| # | Seção         | Fundo              | Notas                                         |
|---|---------------|--------------------|-----------------------------------------------|
| 1 | Hero          | `--gradient-hero`  | Full viewport height, texto branco            |
| 2 | Problema      | `--color-off-white`| Tom direto, lista de pain points              |
| 3 | Solução       | `--color-white`    | Cards de serviço (4 veículos)                 |
| 4 | Benefícios    | `--color-navy`     | Grid 2-col, ícones azuis, texto branco        |
| 5 | Prova Social  | `--color-off-white`| Estrelas Google + depoimentos                 |
| 6 | Tabela Preços | `--color-white`    | Tabela limpa, preços em destaque azul         |
| 7 | FAQ           | `--color-off-white`| Accordions                                    |
| 8 | CTA Final     | `--gradient-hero`  | Grande headline + botão WhatsApp centralizado |
| 9 | Footer        | `--color-navy`     | Minimalista: logo + contato + legalização     |

### Hero:
- Headline em `--t-hero`, uppercase, branco, 2–3 linhas máximo
- Subheadline em `--t-lead`, `--color-gray-mid`
- Badge de legalização (ex: "✓ Legalizado pela Prefeitura de SP") acima do headline
- CTA WhatsApp centralizado ou alinhado à esquerda
- Background: `--gradient-hero` com overlay sutil de ruído (noise texture 5% opacity) para profundidade

### Tabela de Preços:
- Não replicar o visual das peças gráficas (tabela de preços das peças existentes é densa demais para web)
- Usar cards lado a lado: ícone do veículo, nome, preço base em destaque, linha de cobertura
- Preços em `--t-h3` bold, cor `--color-blue`

---

## 7. Iconografia

- Estilo: outline fino (1.5px stroke), monocrômico
- Biblioteca recomendada: Lucide Icons ou Phosphor Icons
- Tamanhos: 20px (inline), 32px (cards), 48px (feature sections)
- Cor padrão: `--color-blue` em fundos claros, `white` em fundos escuros
- Ícone WhatsApp: sempre SVG oficial, nunca substituir por genérico

---

## 8. Imagens e Fotografia

**Diretrizes:**
- Não usar stock photo genérico de motoboy sem contexto
- Preferência: fotos reais da operação (quando disponíveis) ou renders fotorrealistas dos veículos da frota (como nas peças existentes)
- Hero: pode usar o gradiente escuro puro + logo — mais premium que foto ruim
- Veículos nos cards: render branco sobre fundo limpo (mesmo estilo das peças gráficas)
- Sem fotomontagem de baixa qualidade; se não houver foto boa, apostar em composição tipográfica

---

## 9. Animações e Interações

- **Page load:** staggered fade-in de baixo para cima nos elementos do Hero (delay de 0.1s entre cada)
- **Scroll reveal:** fade + translateY(20px) → posição normal, acionado por IntersectionObserver
- **Hover em cards:** `transform: translateY(-4px)` + sombra, 200ms ease-out
- **Botão WhatsApp sticky:** pulse keyframe de 2s, infinite, scale 1 → 1.08 → 1
- **FAQ accordion:** max-height 0 → auto com transition 300ms ease

Nenhuma animação deve durar mais que 400ms. Sem parallax — prejudica performance mobile.

---

## 10. Responsividade

| Breakpoint | Largura    | Comportamento                                  |
|------------|------------|------------------------------------------------|
| Mobile     | < 640px    | 1 coluna, font-size do hero cai para 40px      |
| Tablet     | 640–1024px | 2 colunas nos cards, hero mantém               |
| Desktop    | > 1024px   | Layout completo conforme especificado          |

**Mobile first:** botão WhatsApp é o elemento mais visível em qualquer tamanho. Em mobile, hero CTA ocupa 100% da largura do container.

---

## 11. Tom Visual por Seção

| Seção      | Temperatura | Intenção                                      |
|------------|-------------|-----------------------------------------------|
| Hero       | Fria/Noturna | Autoridade, presença, confiança               |
| Problema   | Neutra       | Identificação com a dor do cliente            |
| Solução    | Limpa/Diurna | Clareza, objetividade, profissionalismo       |
| Benefícios | Fria/Noturna | Solidez, diferenciação, segurança             |
| Prova Social | Neutra    | Credibilidade, humanização                    |
| Preços     | Limpa/Diurna | Transparência, sem truques                   |
| CTA Final  | Fria/Noturna | Urgência controlada, ação direta              |

---

## 12. Checklist de Qualidade

Antes de finalizar qualquer implementação, verificar:

- [ ] Contraste de texto passa WCAG AA em todos os fundos
- [ ] Botão WhatsApp visível e funcional em mobile sem precisar rolar
- [ ] Número `(11) 98741-1445` linkado com `https://wa.me/5511987411445`
- [ ] Nenhuma animação em `prefers-reduced-motion`
- [ ] Font display swap para evitar FOUT
- [ ] Imagens com `alt` descritivo
- [ ] Accordion FAQ acessível via teclado
- [ ] Sticky WhatsApp button com aria-label

---

*Diniz Express — Vila Formosa, Zona Leste de São Paulo.*
*Atendimento: 08h às 21h | Todos os dias | (11) 98741-1445*
