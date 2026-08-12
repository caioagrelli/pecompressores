## O que muda

<!-- Descreva em uma ou duas frases. Se corrige um problema, diga qual. -->

Closes #

## Tipo

- [ ] Correção de bug
- [ ] Conteúdo (texto, preço, horário, dados da empresa)
- [ ] Visual / layout
- [ ] Acessibilidade
- [ ] Performance
- [ ] Documentação

## Checklist

Marque o que se aplica. O que não se aplica, risque.

**Arquitetura**
- [ ] A mudança está em `index.html` — não adicionei build, framework nem dependência
- [ ] Não adicionei recurso externo além de `wa.me`, `google.com/maps` e `instagram.com`

**Conteúdo**
- [ ] Nenhum dado inventado — preço, prazo, depoimento, cliente ou marca sem confirmação
- [ ] Nenhum placeholder visível (`PREENCHER`, `SUBSTITUIR`, texto de exemplo)

**Acessibilidade**
- [ ] Contraste WCAG AA conferido nos pares que mexi
- [ ] Alvos clicáveis com no mínimo 44 px
- [ ] Imagens novas com `alt`, `loading="lazy"`, `width` e `height`
- [ ] `target="_blank"` acompanhado de `rel="noopener noreferrer"`
- [ ] Seção nova com `aria-labelledby` apontando para um id existente
- [ ] Animação nova respeita `prefers-reduced-motion`

**Testado em**
- [ ] 390 px (celular)
- [ ] 768 px (tablet)
- [ ] 1200 px (desktop)
- [ ] Sem rolagem horizontal em nenhum dos três

## Antes e depois

<!-- Cole imagens se a mudança for visual. -->

## Observações

<!-- Algo que o revisor precise saber: decisão de trade-off, pendência, risco. -->
