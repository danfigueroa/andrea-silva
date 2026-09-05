# Andréa Silva — Direito Previdenciário

Landing page estática, sem build e sem dependências. Importada do projeto
Claude Design *"Landing page para advogada Andrea Silva"*
(`Landing Andrea Silva.dc.html`).

```
index.html    marcação e conteúdo
styles.css    design tokens + layout
main.js       revelação no scroll + simulador "Tenho direito?"
assets/       fotos
```

## Rodar

Qualquer servidor estático:

```sh
python3 -m http.server 8000   # http://localhost:8000
```

## O que precisa ser preenchido antes de publicar

A página está com os mesmos placeholders do design. Todos são texto simples:

| Onde | Placeholder |
| --- | --- |
| `<body data-whatsapp>` e os `href="https://wa.me/…"` | `5500000000000` |
| Rodapé | telefone `(00) 00000-0000`, e-mail |

O número do WhatsApp aparece em `data-whatsapp` (fonte da verdade, usada pelo
JS) e nos `href` estáticos, que servem de fallback caso o JS não carregue —
troque nos dois com um find-and-replace de `5500000000000`.

## Fotos que faltam

Três slots ficaram como placeholder tracejado, iguais aos `<image-slot>` do
design. Para preencher, troque a `<div class="photo-slot">` por uma `<img>`:

- **Instagram** — posts 2, 3 e 4 (proporção 4:5)

## Simulador

Três perguntas em `main.js` (`QUESTIONS`), com títulos por área (`TITLES`) e
textos por situação no INSS (`TEXTS`). O resultado monta um link `wa.me` com as
três respostas na mensagem, para a conversa já começar com o caso descrito.

## Notas de implementação

- O template do design usava o runtime do Claude Design (`x-dc`, `sc-for`,
  `sc-if`, `support.js`). Aqui as listas — áreas de atuação e passos — são HTML
  estático, então aparecem para buscadores e sem JavaScript.
- Sem JS a página inteira continua legível: as animações de entrada ficam
  desligadas, os links de WhatsApp funcionam, e o simulador exibe um `noscript`
  apontando para o WhatsApp.
- No mobile (< 760px) os links de navegação do header saem, mantendo marca e
  CTA — o header do design quebrava em três linhas e comia metade da tela.
  As seções seguem acessíveis pelo scroll e pelo rodapé.
- `prefers-reduced-motion` desliga revelação, pulso do botão e scroll suave.
