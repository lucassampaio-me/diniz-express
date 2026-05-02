# CLAUDE.md — Diniz Express Landing Page

## Projeto

Landing page de conversão para a **Diniz Express**, serviço de entregas com motoboy e utilitários na Zona Leste de São Paulo. Objetivo único: gerar contato via WhatsApp.

**Cliente:** Diniz Express  
**WhatsApp:** (11) 98741-1445 → `https://wa.me/5511987411445`  
**Endereço:** Vila Formosa, Zona Leste de São Paulo  
**Horário:** 08h às 21h, todos os dias

---

## Stack

- HTML5 semântico (`index.html`)
- **Tailwind CSS v4** via CLI — `css/input.css` → `css/output.css`
- JavaScript vanilla (`js/main.js`) — sem frameworks, sem bundler

---

## Estrutura

```
diniz-express/
├── CLAUDE.md            ← este arquivo
├── package.json         ← scripts de build/watch
├── index.html           ← página única
├── css/
│   ├── input.css        ← design tokens (@theme) + componentes (@layer)
│   └── output.css       ← gerado pelo CLI (não editar)
├── js/
│   └── main.js          ← accordion FAQ, scroll reveal, hero stagger
├── copy_diniz_express.md ← briefing de copy (fonte de conteúdo)
└── DESIGN.md            ← design system completo (fonte de estilos)
```

---

## Rodar localmente

```bash
# Instalar dependências (apenas CLI do Tailwind)
npm install

# Gerar CSS uma vez
npm run build

# Ou observar mudanças em tempo real
npm run watch
```

Depois abrir `index.html` no browser, ou:

```bash
npx serve .
```

---

## Referências

- **Copy:** `copy_diniz_express.md` — todos os textos da página
- **Design:** `DESIGN.md` — cores, tipografia, espaçamento, componentes, seções

---

## Checklist de qualidade (antes de publicar)

- [ ] CTA WhatsApp abre `wa.me/5511987411445` corretamente
- [ ] Contraste de texto passa WCAG AA em todos os fundos
- [ ] Botão WhatsApp sticky visível em mobile sem rolar
- [ ] FAQ acessível via teclado (Tab + Enter/Space)
- [ ] Sticky WhatsApp button tem `aria-label`
- [ ] Imagens/SVGs têm `alt` descritivo
- [ ] `prefers-reduced-motion` desativa animações
- [ ] Google Fonts carrega com `font-display: swap`
- [ ] Testar em 375px (mobile), 768px (tablet), 1280px (desktop)
