# CLAUDE.md

Contexto para assistentes de IA que forem trabalhar neste repositório.

## O que é

Landing page da Pernambuco Peças para Compressores (PE Compressores), Recife/PE.
B2B industrial: peças, manutenção, locação e consultoria em compressores parafuso
multimarca. O público é gestor de manutenção de indústria — muitas vezes chegando ao
site com uma máquina parada e a produção travada.

## Regra principal

**Tudo vive em `index.html`.** Arquivo único, sem build, sem framework, sem
dependências externas. CSS num único `<style>`, JavaScript num único `<script>` no fim
do body, imagens em base64. Antes de propor qualquer biblioteca, CDN ou etapa de build,
pergunte — a restrição é deliberada.

## Design system

Paleta **azul, branco e preto**. Nenhuma cor fora dessas famílias; os cinzas são
azulados de propósito.

```
--ink:       #000000   preto — blocos principais (hero, serviços, contato, rodapé)
--page:      #060C22   azul escuro — fundo da página
--surface:   #0C1533   azul escuro — cards
--surface-2: #111C42   azul escuro — cards internos
--navy:      #0E2FA0   azul escuro sólido — hover
--blue:      #1440D6   ação primária
--sky:       #5C9BFF   acento claro, ícones, destaques
--white:     #FFFFFF   títulos e texto de botão
--text:      #C4CFE8   corpo sobre escuro
--muted:     #8B99BC   secundário sobre escuro
```

Tipografia geométrica (Poppins → Inter → system-ui), cantos de 24 px nos cards e
pílula nos botões.

## Invariantes — não quebre

1. **Contraste WCAG AA** em todos os pares texto/fundo. Ao mexer em cor, recalcule.
2. **Nada de rolagem horizontal.** Os carrosséis usam trilhas mais largas que a tela;
   o `.marquee` precisa de `overflow:hidden`, e há `overflow-x:clip` no html e no body
   como rede de segurança. Já quebrou uma vez.
3. **Alvos de toque ≥ 44 px** em qualquer coisa clicável.
4. **`prefers-reduced-motion`** desliga todas as animações.
5. **Toda `<img>`** precisa de `alt`, `loading="lazy"`, `width` e `height`.
6. **Todo `target="_blank"`** precisa de `rel="noopener noreferrer"`.
7. **Cada `<section>`** precisa de `aria-labelledby` apontando para um id existente.
8. A cópia duplicada das trilhas de carrossel fica `aria-hidden` e com `tabindex="-1"`
   nos links, para não duplicar conteúdo no leitor de tela nem na navegação por teclado.

## Honestidade do conteúdo

Este é um site comercial que vai receber tráfego pago. **Não invente fato nenhum.**

- Não crie depoimentos, nomes de clientes ou logos de empresas atendidas
- Não adicione marcas de compressor à lista sem confirmação — a empresa atende
  Atlas Copco, Ingersoll Rand, Schulz, Chicago Pneumatic, Kaeser, Metalplan, Mattei
  e Sullair
- Não invente preço, prazo de atendimento nem número de anos de mercado
- Se falta um dado, deixe o item de fora e registre em "Pendências" no README —
  nunca publique `PREENCHER` ou texto de exemplo no ar

A página já teve depoimentos-placeholder visíveis em produção. Foi corrigido.

## Detalhes de implementação

**Mapa de cobertura** (`.coverage`, no hero): SVG com litoral e capitais em coordenadas
geográficas reais, projetadas de lon/lat para o viewBox 820×740. Recife é o ponto branco
com ondas de radar. No celular vai para o rodapé do hero e os rótulos somem — em 390 px
eles brigam com o texto. O contorno oeste é estilizado, não é fronteira real.

**Ícones por máscara CSS**: WhatsApp e contorno de Pernambuco usam
`mask: url(data:image/png…)` com `background-color: currentColor`, herdando a cor do pai.

**Formulário**: sem back-end. Monta a mensagem com os campos e abre `wa.me`.

**Filtro do catálogo**: os 14 cards nascem visíveis no HTML e o JS aplica a categoria
"Peças" ao carregar. Se o JS falhar, o visitante vê o catálogo inteiro em vez de uma
seção vazia. Mantenha esse comportamento.

## Como verificar uma alteração

Não existe suíte de testes. Antes de dar por pronto, confira no arquivo:

- tags balanceadas e âncoras `href="#id"` apontando para ids existentes
- nenhum recurso externo além de `wa.me`, `google.com/maps` e `instagram.com`
- contraste recalculado se mexeu em cor
- comportamento em 390 px, 768 px e 1200 px
- nenhum placeholder (`PREENCHER`, `SUBSTITUIR`, texto de exemplo) visível
