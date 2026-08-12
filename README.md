# PE Compressores

Landing page da **Pernambuco Peças para Compressores** — peças, manutenção, locação e
consultoria em compressores parafuso multimarca em Pernambuco e no entorno.

🔗 <https://caioagrelli.github.io/pecompressores/>

## Sobre o projeto

Página estática de **arquivo único** (`index.html`). Sem build, sem framework e sem
dependências externas: CSS e JavaScript são inline e todas as imagens estão embutidas
em base64. Isso significa que a página carrega de uma requisição só, funciona offline
depois do primeiro acesso e não faz nenhuma chamada a terceiros.

## O que tem dentro

- **Hero** com simulação do custo de uma hora de linha parada e mapa de cobertura animado
  (litoral e capitais em coordenadas geográficas reais)
- **Mural de marcas** atendidas em carrossel contínuo
- **Catálogo de 14 itens** — peças, insumos e serviços — com filtro por categoria e
  botão de orçamento que abre o WhatsApp com a mensagem já montada
- **Carrossel de setores** industriais atendidos
- **Avaliações** do Google
- **Formulário** de orçamento que monta a mensagem e encaminha para o WhatsApp
- **FAQ** em `<details>` nativo

## Decisões técnicas

**Arquivo único e base64.** O site tem 14 ilustrações de produto, 6 logos de marcas,
o mapa de cobertura e a logo da empresa. Embutir tudo evita 20+ requisições e mantém o
deploy trivial — é um arquivo para copiar.

**Ícones como máscara CSS.** O glifo do WhatsApp e o contorno de Pernambuco são
aplicados via `mask` com `background-color: currentColor`, então herdam a cor do
elemento pai e funcionam em qualquer fundo sem precisar de variantes.

**Favicon adaptativo.** SVG com `prefers-color-scheme`: escuro em abas de tema claro,
branco em abas de tema escuro. Sem moldura.

**Sem back-end.** O formulário não envia nada para servidor nenhum — ele monta a
mensagem e abre o WhatsApp. Nenhum dado do visitante trafega ou é armazenado.

## Acessibilidade

- HTML semântico, cada seção com `aria-labelledby`
- Contraste **WCAG AA** verificado par a par em toda a paleta
- Navegação por teclado, foco visível e alvos de toque de no mínimo 44 px
- Carrosséis pausam no hover e param por completo com `prefers-reduced-motion`
- Conteúdo duplicado dos carrosséis marcado com `aria-hidden` e fora da ordem de foco
- Todas as imagens com `alt`, `width` e `height`

## Estrutura

```
index.html                      o site inteiro
.github/workflows/deploy.yml    publicação automática no GitHub Pages
CLAUDE.md                       contexto para assistentes de IA
SECURITY.md                     política de segurança
LICENSE                         licença
```

## Desenvolvimento

Não há etapa de build. Abra `index.html` no navegador ou sirva a pasta:

```bash
python3 -m http.server 8000
```

## Publicação

Todo push na branch `main` dispara o workflow e publica no GitHub Pages.
Em **Settings → Pages**, defina **Source: GitHub Actions**.

## Pendências

Itens que dependem de informação da empresa antes de rodar tráfego pago:

- [ ] **Prazo real de atendimento** para máquina parada, por região — hoje a página fala
      em "atendimento emergencial" sem número
- [ ] **CNPJ** no rodapé
- [ ] **Depoimentos de clientes** com nome, cargo e empresa
- [ ] **Fotos reais** das peças e da equipe em campo, no lugar das ilustrações
- [ ] **Logos da Atlas Copco e da Ingersoll Rand** — hoje aparecem só como texto
- [ ] Confirmar autorização de uso das marcas de fabricante exibidas no mural
