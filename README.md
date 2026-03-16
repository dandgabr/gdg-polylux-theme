# Tema GDG para Polylux (Typst)

Este diretório contém um tema de apresentação para Typst usando Polylux, com identidade visual inspirada no Google Developer Groups.

## Arquivos

- `gdg-polylux.typ`: tema reutilizável (layout, tipografia, seção, header/footer, wrappers de slide).
- `slides.typ`: exemplo funcional de apresentação usando o tema.

## Como usar

1. Importe o tema no seu arquivo de slides:

```typst
#import "gdg-polylux.typ": *
```

1. Aplique o tema uma única vez no topo do documento:

```typst
#show: theme.with(
  aspect-ratio: "16-9",
  footer: [Seu evento · 2026],
)
```

1. Estruture o conteúdo com seções e slides:

```typst
= Minha Seção

#slide[
== Título do slide
Conteúdo...
]
```

## API exportada

- `theme(...)`: configura o documento inteiro.
- `slide[...]`: slide padrão com header e footer automáticos.
- `title-slide[...]`: slide de abertura (sem header/footer).
- `focus-slide[...]`: slide de destaque visual (fundo sólido).
- `centered-slide[...]`: conteúdo centralizado (transição/encerramento).

## Convenções do tema

- `= Título` (heading nível 1) gera automaticamente uma capa de seção.
- `== Título` (heading nível 2) é usado como título de conteúdo do slide.
- O rodapé mostra texto configurado em `footer` e paginação `atual/total`.

## Personalização rápida

No `gdg-polylux.typ`, você pode ajustar:

- Paleta (`gdg-blue`, `gdg-red`, `gdg-yellow`, `gdg-green`, `gdg-grey`).
- Fonte Roboto: baixe em https://fonts.google.com/specimen/Roboto e instale no sistema para garantir a renderização correta no Typst.
- Tipografia global (`set text(font: "Roboto", ...)`).
- Espaçamentos de header/footer no `set page(...)` do `gdg-slide`.

## Sugestão de fluxo para novos decks

1. Copie `slides.typ` para um novo arquivo (ex.: `minha-talk.typ`).
2. Mantenha os imports e o bloco `#show: theme.with(...)`.
3. Troque seções e conteúdos, preservando a estrutura base.
4. Use `focus-slide` apenas para mensagens realmente importantes.
