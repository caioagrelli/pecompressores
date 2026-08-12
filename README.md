# Landing page — assistência técnica industrial

> **Protótipo de demonstração.** Peça de portfólio desenvolvida de forma independente,
> sem encomenda de terceiros. Os dados exibidos são ilustrativos e servem apenas para
> demonstrar o layout em um cenário realista. Nenhuma empresa citada encomendou,
> revisou ou aprovou este trabalho.

Landing page para um negócio B2B de manutenção industrial — peças, service, locação e
consultoria. O público é gestor de manutenção, muitas vezes chegando ao site com uma
máquina parada e a produção travada. Cada decisão de layout parte disso.

🔗 <https://caioagrelli.github.io/pecompressores/>

## Sobre o projeto

Página estática de **arquivo único** (`index.html`). Sem build, sem framework e sem
dependências externas: CSS e JavaScript são inline e todas as imagens estão embutidas
em base64. A página carrega de uma requisição só, funciona offline depois do primeiro
acesso e não faz nenhuma chamada a terceiros.

## O que tem dentro

- **Hero** com simulação do custo de uma hora de linha parada e mapa de cobertura
  animado — litoral e capitais em coordenadas geográficas reais
- **Mural de marcas** em carrossel contínuo
- **Catálogo de 14 itens** com filtro por categoria e botão de orçamento que abre o
  WhatsApp com a mensagem já montada
- **Carrossel de setores** industriais
- **Formulário** que monta a mensagem e encaminha para o WhatsApp
- **FAQ** em `<details>` nativo

## Decisões técnicas

**Arquivo único e base64.** São 14 ilustrações de produto, 6 logos, o mapa de cobertura
e a marca. Embutir tudo evita 20+ requisições e mantém o deploy trivial — é um arquivo
para copiar.

**Ícones como máscara CSS.** Os glifos são aplicados via `mask` com
`background-color: currentColor`, então herdam a cor do elemento pai e funcionam em
qualquer fundo sem precisar de variantes.

**Favicon adaptativo.** SVG com `prefers-color-scheme`: escuro em abas de tema claro,
branco em abas de tema escuro. Sem moldura.

**Sem back-end.** O formulário não envia nada para servidor nenhum — monta a mensagem e
abre o WhatsApp.

## Acessibilidade

- HTML semântico, cada seção com `aria-labelledby`
- Contraste **WCAG AA** verificado par a par em toda a paleta
- Navegação por teclado, foco visível e alvos de toque de no mínimo 44 px
- Carrosséis pausam no hover e param por completo com `prefers-reduced-motion`
- Conteúdo duplicado dos carrosséis marcado com `aria-hidden` e fora da ordem de foco
- Todas as imagens com `alt` e dimensões declaradas

A verificação roda no CI a cada pull request.

## Estrutura

```
index.html                      o site inteiro
.github/workflows/deploy.yml    publicação automática no GitHub Pages
.github/workflows/verificacao.yml   checagem de acessibilidade e integridade
CLAUDE.md                       contexto para assistentes de IA
SECURITY.md                     política de segurança
LICENSE                         MIT
```

## Desenvolvimento

Não há etapa de build. Abra `index.html` no navegador ou sirva a pasta:

```bash
python3 -m http.server 8000
```

## Publicação

Todo push na branch `main` dispara o workflow e publica no GitHub Pages.
Em **Settings → Pages**, defina **Source: GitHub Actions**.

## O que falta para virar produção

Como protótipo, a página tem lacunas propositais — tudo que dependeria de informação
real do cliente ficou de fora em vez de ser inventado:

- [ ] Prazo real de atendimento, por região
- [ ] CNPJ e dados cadastrais
- [ ] Depoimentos com nome, cargo e empresa
- [ ] Fotos reais de produto e equipe, no lugar das ilustrações
- [ ] Autorização de uso das marcas de fabricante exibidas

## Licença

MIT — veja [LICENSE](LICENSE). A licença cobre o código; marcas de terceiros que
apareçam na demonstração pertencem aos respectivos titulares.

Autor: **Caio Agrelli** · caiooagrelli@hotmail.com
