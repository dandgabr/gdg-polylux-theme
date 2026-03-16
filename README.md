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
- `gdg-qrcode-style`: preset de estilo para QR Code com as cores do tema.
- `gdg-qr-code(...)`: helper pronto para gerar QR Code via cades.
- `gdg-codly-style`: preset de estilo para blocos de código com codly.

## QR Code com cades

O tema já expõe um preset para QR Code usando a paleta GDG e um helper pronto.

Exemplo com helper:

```typst
#gdg-qr-code("https://gdg.community.dev", width: 2.8cm)
```

Exemplo com chamada direta da biblioteca cades:

```typst
#import "@preview/cades:0.3.1": qr-code

#qr-code(
  "https://gdg.community.dev",
  width: 2.8cm,
  ..gdg-qrcode-style,
)
```

## Código com codly

O tema inicializa o codly automaticamente dentro de `theme`, então blocos de código
já aparecem com estilo visual alinhado ao GDG.

Exemplo simples:

````typst
```ts
const event = "DevFest";
console.log(`Bem-vindo ao ${event}`);
```
````

Se quiser reaplicar/ajustar o preset manualmente:

```typst
#import "@preview/codly:1.3.0": codly

#codly(..gdg-codly-style)
```

## Convenções do tema

- `= Título` (heading nível 1) gera automaticamente uma capa de seção.
- `== Título` (heading nível 2) é usado como título de conteúdo do slide.
- O rodapé mostra texto configurado em `footer` e paginação `atual/total`.

## Personalização rápida

No `gdg-polylux.typ`, você pode ajustar:

- Paleta (`gdg-blue`, `gdg-red`, `gdg-yellow`, `gdg-green`, `gdg-grey`).
- Fonte Roboto: baixe em [Google Fonts](https://fonts.google.com/specimen/Roboto) e instale no sistema para garantir a renderização correta no Typst.
- Tipografia global (`set text(font: "Roboto", ...)`).
- Espaçamentos de header/footer no `set page(...)` do `gdg-slide`.

## Sugestão de fluxo para novos decks

1. Copie `slides.typ` para um novo arquivo (ex.: `minha-talk.typ`).
2. Mantenha os imports e o bloco `#show: theme.with(...)`.
3. Troque seções e conteúdos, preservando a estrutura base.
4. Use `focus-slide` apenas para mensagens realmente importantes.
