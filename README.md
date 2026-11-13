# negocio-no-chatgpt â€” ficha do negÃ³cio para a IA

[![Seu negÃ³cio no ChatGPT](guia/assets/banner.jpg)](https://inematds.github.io/negocio-no-chatgpt/guia/)

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

ðŸŽ¬ VÃ­deo: https://www.youtube.com/watch?v=YUlRfOmXK1c Â· Short: https://youtube.com/shorts/oSKT2cQBAQw

Quando alguÃ©m perguntar ao ChatGPT onde comprar o que vocÃª vende, o seu negÃ³cio pode aparecer. A ficha do negÃ³cio para a IA deixa tudo pronto em 10 minutos.

## O que Ã©

Desde 10/11/2026 o ChatGPT tem, em teste, um cadastro oficial para negÃ³cios. Mas no Brasil a loja fÃ­sica e o restaurante ainda nÃ£o conseguem se cadastrar, e mesmo quem consegue sÃ³ aparece se a IA entender o negÃ³cio. O **negocio-no-chatgpt** Ã© um kit grÃ¡tis para o dono de negÃ³cio que quer ser encontrado pela IA: ele monta a **ficha do negÃ³cio para a IA** (o texto pronto e o bloco de dados que vai no site) e dÃ¡ uma nota ao seu site com a lista do que corrigir. TambÃ©m traz o passo a passo do cadastro, sÃ³ com o que a OpenAI confirmou. Precisa sÃ³ de um computador com Python, que Ã© grÃ¡tis.

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/negocio-no-chatgpt/guia/**

## O recurso e o Brasil

**Businesses in ChatGPT** estÃ¡ em beta desde 10/11/2026. No **Business Hub**, negÃ³cios elegÃ­veis podem reivindicar e verificar a ficha, atualizar informaÃ§Ãµes e conectar um feed de produtos. Os fatos usados aqui vÃªm exclusivamente de [FONTES.md](FONTES.md).

**Brasil:** lojas fÃ­sicas e restaurantes ainda sÃ³ podem reivindicar fichas existentes nos EUA. NegÃ³cios online podem tentar; depende das checagens da OpenAI. O Business Agent ainda Ã© sÃ³ para e-commerce e serviÃ§os online elegÃ­veis nos EUA. NÃ£o hÃ¡ lista de paÃ­ses publicada. Cadastro nÃ£o garante vendas ou posiÃ§Ã£o.

Kit pÃºblico INEMA, pequeno, em Python 3, sÃ³ com biblioteca padrÃ£o: sem pip, sem conta de API.

## InstalaÃ§Ã£o

Tenha Python 3 instalado (Git Ã© opcional: dÃ¡ para [baixar o ZIP](https://github.com/inematds/negocio-no-chatgpt/archive/refs/heads/main.zip)). NÃ£o hÃ¡ dependÃªncias para instalar. **No Windows, troque `python3` por `py`** em todos os comandos.

```bash
git clone https://github.com/inematds/negocio-no-chatgpt
cd negocio-no-chatgpt
```

## Prepare a ficha

```bash
python3 ficha.py
```

Responda uma pergunta por vez. No tipo, vale o nÃºmero ou o nome (1 loja fÃ­sica, 2 restaurante, 3 serviÃ§o local, 4 loja virtual, 5 serviÃ§o online) e sinÃ´nimos comuns como â€œpadariaâ€; resposta que nÃ£o serve (tipo, telefone, e-mail, site) Ã© perguntada de novo, sem perder o resto. O mÃ©todo **ficha do negÃ³cio para a IA** produz `ficha.md`, `jsonld.html`, `jsonld.json` e `checklist.md` em `minha-ficha/`. Revise antes de publicar. O script nunca usa rede.

Para usar um arquivo com as mesmas chaves das perguntas, copie e edite [respostas.json](exemplos/padaria/respostas.json). Produtos/serviÃ§os sÃ£o uma lista; perguntas frequentes sÃ£o atÃ© cinco objetos com `pergunta` e `resposta`. Os nomes exatos das chaves estÃ£o no exemplo. Somente `nome`, `o_que_vende`, `tipo` e pelo menos um entre `cidade` e `site` sÃ£o obrigatÃ³rios. Telefone, WhatsApp, e-mail e site sÃ£o validados quando preenchidos.

```bash
python3 ficha.py --de exemplos/padaria/respostas.json --saida exemplos/padaria/minha-ficha
```

SaÃ­da real:

```text
ficha do negÃ³cio para a IA gerada em exemplos/padaria/minha-ficha/
Arquivos: ficha.md, jsonld.html, jsonld.json, checklist.md
```

Cole os textos de `ficha.md` no site, nos perfis e nos campos correspondentes do Business Hub, se elegÃ­vel. Cole `jsonld.html` no `<head>` do site; `jsonld.json` contÃ©m os mesmos dados em JSON puro. Siga `checklist.md` e o [passo a passo do cadastro](CADASTRO.md).

HorÃ¡rios reconhecidos: `seg-sex 9h-18h, sÃ¡b 9h-13h`, `ter 9h30-18h`, `dom 09:00-12:00`. Separe perÃ­odos por vÃ­rgula ou ponto e vÃ­rgula. Se algum trecho nÃ£o for reconhecido, o campo `openingHours` inteiro Ã© omitido e o checklist avisa; o texto original continua na ficha. NÃ£o hÃ¡ adivinhaÃ§Ã£o de horÃ¡rio.

## Confira o site

```bash
python3 checar_site.py exemplos/sites/bom/index.html
python3 checar_site.py https://seu-site.com.br
python3 checar_site.py seu-site.html --robots caminho/robots.txt --llms caminho/llms.txt
python3 checar_site.py exemplos/sites/bom/index.html --json
```

Trecho da saÃ­da real do exemplo bom:

```text
ficha do negÃ³cio para a IA â€” nota: 100/100

OK
- OAI-SearchBot liberado nesta pÃ¡gina; sem meta noindex.
- JSON-LD vÃ¡lido com tipo de negÃ³cio.
- TÃ­tulo e descriÃ§Ã£o dentro dos tamanhos recomendados pelo kit.
- Contato e localizaÃ§Ã£o legÃ­veis no texto da pÃ¡gina.
- Texto visÃ­vel: 198 palavras (mÃ­nimo do kit: 150).
- llms.txt presente: opcional, sem garantia de efeito.

CORRIGIR
- Nenhum item.
```

O checador usa HTMLParser e lÃª HTML, sem executar JavaScript. Para arquivo local, procura `robots.txt` e `llms.txt` na mesma pasta, ou usa os caminhos indicados. Para URL, faz somente GET com urllib, timeout de 15 segundos por requisiÃ§Ã£o, atÃ© cinco redirecionamentos por recurso e leitura de no mÃ¡ximo 2 MB por recurso. Busca os arquivos auxiliares na origem da pÃ¡gina final. User-Agent: `negocio-no-chatgpt-checador/1.0`. Arquivos que atingem o limite de leitura remota sÃ£o recusados para evitar anÃ¡lise truncada.

A nota de 0 a 100 Ã© uma heurÃ­stica do kit: acesso 30, JSON-LD 20, tÃ­tulo/descriÃ§Ã£o 15, contato/localizaÃ§Ã£o 20, texto visÃ­vel 10 e llms.txt opcional 5. Os critÃ©rios de cada grupo precisam ser atendidos juntos. A ausÃªncia de robots.txt libera; falha ao consultÃ¡-lo Ã© informada como nÃ£o verificado. GPTBot e ChatGPT-User sÃ£o informativos e nÃ£o descontam pontos. Bloquear GPTBot (treino) nÃ£o tira o site da busca.

Para localizaÃ§Ã£o, use cidade do JSON-LD tambÃ©m no texto visÃ­vel, CEP ou um formato explÃ­cito como `Cidade: Joinville` ou `Joinville/SC`. O checador nÃ£o reconhece todas as cidades automaticamente. Reconhece tipos comuns de negÃ³cio listados no inÃ­cio do cÃ³digo; nÃ£o baixa o catÃ¡logo schema.org. NÃ£o verifica CSS externo, renderizaÃ§Ã£o de JavaScript ou liberaÃ§Ã£o de IPs no servidor/CDN. JSON-LD e llms.txt nÃ£o tÃªm efeito em posiÃ§Ã£o confirmado; llms.txt Ã© opcional e nÃ£o hÃ¡ garantia de efeito.

O programa retorna cÃ³digo 0 quando consegue ler a pÃ¡gina, mesmo com nota baixa, e 2 quando nÃ£o consegue. Em `--json`, os resultados e os erros sÃ£o JSON. Os dados dos exemplos sÃ£o todos inventados; nÃ£o use seus contatos como dados reais.

Isso deixa o site fÃ¡cil de ler para a IA. NÃ£o garante posiÃ§Ã£o: quem escolhe o que aparecer Ã© o ChatGPT.

## Testes sem rede

```bash
python3 testes/run.py
```

Os testes bloqueiam conexÃµes de rede e cobrem geraÃ§Ã£o, validaÃ§Ã£o, horÃ¡rios, HTML, robots.txt, limites de leitura e redirecionamento com respostas simuladas.

Guia completo: https://inematds.github.io/negocio-no-chatgpt/guia/

## Kits que combinam

- [site que vende](https://inematds.github.io/site-que-vende/guia/)
- [atendimento de leads](https://inematds.github.io/atende-leads/guia/)

LicenÃ§a MIT, 2026 INEMA. VersÃ£o 1.0.0.

**grÃ¡tis no inema.club, direto na internet**

---

Projeto adaptado da comunidade INEMA TDS - Marca Arckhe