# Como contribuir

## Fluxo obrigatório

A branch `main` é protegida. **Ninguém commita direto nela** — nem quem tem permissão
de administrador. Toda mudança entra por pull request.

```bash
git checkout main && git pull
git checkout -b tipo/descricao-curta      # ex.: fix/rolagem-horizontal
# edite, teste
git commit -m "fix: descrição do que mudou"
git push -u origin tipo/descricao-curta
```

Depois abra o PR no GitHub, preencha o template e peça revisão. Só faça merge quando:

- pelo menos **1 aprovação** de revisor
- o workflow de deploy tiver passado
- as conversas do review estiverem resolvidas

Prefixos de branch: `fix/`, `feat/`, `content/`, `a11y/`, `docs/`, `perf/`.

## Mensagens de commit

Padrão [Conventional Commits](https://www.conventionalcommits.org/pt-br/):

```
fix: corrige rolagem horizontal no carrossel de marcas
feat: adiciona filtro de categoria no catálogo
content: atualiza horário de atendimento
a11y: aumenta contraste do texto secundário
docs: adiciona política de segurança
```

## Antes de abrir o PR

Não há suíte de testes. A verificação é manual, e estes são os pontos que já quebraram
antes:

1. **Rolagem horizontal.** Abra em 390 px e tente arrastar para o lado. Não pode mexer.
2. **Contraste.** Se mexeu em cor, recalcule os pares texto/fundo. Mínimo AA (4,5:1
   para texto normal, 3:1 para texto grande).
3. **Sem placeholder no ar.** Procure por `PREENCHER`, `SUBSTITUIR` e texto de exemplo.
4. **Âncoras.** Todo `href="#id"` precisa de um `id` correspondente.
5. **Imagens.** `alt`, `loading="lazy"`, `width` e `height` em todas.
6. **Três larguras:** 390 px, 768 px e 1200 px.

## Regras que não se negociam

**Arquivo único.** Tudo vive em `index.html`. Sem build, sem framework, sem CDN, sem
`package.json`. A restrição é deliberada: o deploy é copiar um arquivo, e a página não
depende de nada que possa sair do ar. Se achar que precisa quebrar isso, abra uma issue
antes de escrever código.

**Nada de dado inventado.** Este site recebe tráfego pago e vende serviço industrial.
Não crie depoimento, nome de cliente, preço, prazo de atendimento ou marca atendida sem
alguém da empresa confirmar. Se falta informação, deixe o item de fora e registre em
"Pendências" no README. Publicar `[Nome do cliente]` no ar é pior que não ter a seção.

**Marcas de fabricante.** Não acrescente logo de fabricante ao mural sem confirmar
autorização de uso. Exibir marca de quem não autorizou é risco real para a empresa.

## Contexto para IA

Se você usa assistente de código, aponte ele para o `CLAUDE.md` na raiz — está tudo lá:
paleta, invariantes, decisões de arquitetura e o que não pode ser quebrado.
