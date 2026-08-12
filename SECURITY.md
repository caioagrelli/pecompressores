# Política de Segurança

## Escopo

Este repositório contém uma página estática de arquivo único (`index.html`), publicada
no GitHub Pages como **protótipo de demonstração**. Não há back-end, banco de dados,
autenticação nem processamento de dados no servidor.

## Como a demonstração trata dados

O formulário **não envia nada para servidor nenhum**. Ele monta uma mensagem de texto
com os campos preenchidos e abre o WhatsApp. Nenhum dado é armazenado, transmitido para
terceiros ou registrado em log por esta aplicação.

A partir do momento em que a conversa segue no WhatsApp, valem os termos da Meta.

A página não usa cookies, `localStorage`, analytics nem pixel de rastreamento.

## Versões suportadas

| Versão | Suporte |
| --- | --- |
| `main` | ✅ |
| Outras branches | ❌ |

Apenas o conteúdo publicado a partir da branch `main` recebe correções.

## Reportando uma vulnerabilidade

Se encontrar um problema de segurança, **não abra uma issue pública.**

Escreva para **caiooagrelli@hotmail.com** com:

- descrição do problema e do impacto possível
- passos para reproduzir
- navegador e versão, se for relevante
- qualquer prova de conceito que ajude a entender

Retorno esperado em até **5 dias úteis**. Se a falha for confirmada, informo o prazo de
correção e aviso quando estiver corrigida. Peço que aguarde a correção antes de
divulgar publicamente.

## Fora de escopo

Os itens abaixo não são tratados como vulnerabilidade neste projeto:

- Ausência de cabeçalhos de segurança controlados pelo GitHub Pages (a hospedagem é de
  terceiro e não permite configuração de cabeçalho)
- Ausência de `Content-Security-Policy` restritiva — o CSS e o JS são inline por decisão
  de arquitetura
- Relatórios automatizados de scanner sem prova de exploração
- Ataques que exijam acesso físico à máquina ou engenharia social
- Vulnerabilidades em serviços de terceiros linkados na página (WhatsApp, Google Maps,
  Instagram)

## Dependências

O projeto **não tem dependências**. Não há `package.json`, nem CDN, nem biblioteca
externa. Os únicos recursos de terceiros são links de saída — nenhum deles carrega
código na página.

As GitHub Actions usadas no workflow de publicação são oficiais da própria GitHub e
estão fixadas por versão maior.
