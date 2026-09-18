# Site — Projeto Atuar Semeando Amor

Site institucional estático, arquivo único, sem dependências externas.

## Arquivos

| Arquivo | O que é | Mexer? |
|---|---|---|
| `index.html` | O site inteiro (HTML + CSS + JS + imagens embutidas) | Sim |
| `_headers` | Cabeçalhos de segurança lidos pela Cloudflare | Raramente |
| `noticias.json` | As notícias do site | **Sim, toda semana** |
| `robots.txt` | Instruções para o Google | Ao ter domínio |
| `README.md` | Este arquivo | — |

O site é **autocontido**: as imagens estão embutidas dentro do HTML em base64.
Não existe pasta de imagens. Abrir `index.html` com dois cliques já mostra o site
funcionando, mesmo sem internet.

---

## PARTE 1 — Colocar no ar (~15 minutos)

### Passo 1 — Conta no GitHub

1. Acesse `github.com` e crie uma conta gratuita (ou entre na sua).
2. Confirme o e-mail.

### Passo 2 — Criar o repositório

1. Clique no `+` no canto superior direito → **New repository**.
2. **Repository name:** `site-projeto-atuar`
3. **Visibility:** Public (Private também funciona na Cloudflare, mas Public
   facilita se outra pessoa precisar ajudar depois).
4. NÃO marque "Add a README file" — você já tem um.
5. Clique em **Create repository**.

### Passo 3 — Subir os arquivos

1. Na tela que abrir, clique no link **uploading an existing file**.
2. Arraste os 4 arquivos (`index.html`, `_headers`, `robots.txt`, `README.md`).
3. Em "Commit changes", escreva `Primeira versão do site`.
4. Clique em **Commit changes**.

> **Crítico:** o `index.html` precisa ficar na raiz do repositório, não dentro
> de uma pasta. Depois do upload, confira se você vê `index.html` listado
> direto na página principal do repositório.

### Passo 4 — Conta na Cloudflare

1. Acesse `dash.cloudflare.com/sign-up`.
2. Crie a conta com e-mail e senha. Não pede cartão de crédito.
3. Confirme o e-mail.

### Passo 5 — Conectar e publicar

1. No painel da Cloudflare, menu lateral esquerdo: **Workers & Pages**.
2. Clique em **Create application**.
3. **ATENÇÃO — é onde todo mundo erra:** na tela que abrir, NÃO clique no botão
   grande "Connect GitHub" (isso cria um *Worker*, que é outra coisa).
   Procure o texto pequeno no rodapé da caixa: **"Looking to deploy Pages?
   Get started"** e clique nele.
4. Escolha **Import an existing Git repository** → **Get started**.
5. Clique em **Connect GitHub** e autorize o acesso ao repositório
   `site-projeto-atuar`.
6. Selecione o repositório → **Begin setup**.
7. Preencha exatamente assim:

   | Campo | Valor |
   |---|---|
   | Project name | `projeto-atuar` |
   | Production branch | `main` |
   | Framework preset | **None** |
   | Build command | *(deixe em branco)* |
   | Build output directory | *(deixe em branco)* |

8. Clique em **Save and Deploy**.

Em cerca de 1 minuto o site está no ar em `projeto-atuar.pages.dev`, já com
HTTPS e CDN global.

---

## PARTE 2 — Domínio próprio (opcional)

### Passo 6 — Registrar o domínio

1. Acesse `registro.br`.
2. Pesquise por `projetoatuar.org.br` (ou o nome que preferir).
3. **Confira os requisitos de documentação.** Domínios `.org.br` normalmente
   exigem CNPJ de entidade sem fins lucrativos. Se o projeto ainda não é
   formalizado, use `.com.br`, que aceita CPF.
4. Registre e pague (aproximadamente R$40/ano).

### Passo 7 — Apontar o domínio

1. Na Cloudflare, dentro do projeto: aba **Custom domains**.
2. **Set up a custom domain** → digite o domínio → **Continue**.
3. A Cloudflare mostra os registros DNS a configurar.
4. No painel do Registro.br, em **DNS**, troque os servidores DNS pelos que a
   Cloudflare indicar.
5. A propagação leva de 15 minutos a algumas horas.

### Passo 8 — Google

1. Edite `robots.txt` e troque `SEU-DOMINIO-AQUI` pelo domínio real.
2. Cadastre o site no **Google Search Console** (`search.google.com/search-console`)
   para ele começar a aparecer nas buscas.

---

## PARTE 3 — Editar o site depois

Para qualquer mudança de texto:

1. No GitHub, abra o repositório e clique em `index.html`.
2. Clique no ícone de **lápis** (Edit this file).
3. Use `Ctrl+F` para achar o trecho, edite, e clique em **Commit changes**.
4. A Cloudflare republica sozinha em ~1 minuto.

### Onde estão as coisas no arquivo

| O que mudar | Procure por |
|---|---|
| Chave PIX | `projetoatuarsemeandoamor` |
| Números de impacto | `class="num"` |
| Textos das ações | `<article class="card` |
| Depoimentos | `<blockquote>` |
| Notícias | *(não é aqui — é no `noticias.json`)* |
| Cores | `:root{` (no topo, dentro do `<style>`) |

### Paleta de cores

| Nome | Código | Onde aparece |
|---|---|---|
| Verde | `#16a34a` | Botões, destaques |
| Verde escuro | `#0f7a37` | Hover, títulos pequenos |
| Verde médio | `#22c55e` | Degradês |
| Tinta | `#12263f` | Todo o texto |
| Creme | `#fbfaf6` | Fundo da página |
| Areia | `#f3f1ea` | Seções alternadas |

---

---

## PARTE 4 — Publicar uma notícia

As notícias ficam no arquivo `noticias.json`. Você **não precisa mexer no HTML**
para publicar uma — só editar esse arquivo.

### Como publicar

1. No GitHub, abra o repositório e clique em `noticias.json`.
2. Clique no ícone de **lápis**.
3. Copie o bloco abaixo e cole logo depois de `"noticias": [`:

```json
    {
      "titulo": "Mutirão do Direito ao Banho atende 40 pessoas",
      "data": "2026-09-20",
      "categoria": "Direito ao Banho",
      "resumo": "Neste sábado a equipe montou a estrutura na Praça Firmina Santana e ofereceu banho quente, roupas limpas e kit de higiene.",
      "imagem": "",
      "link": ""
    },
```

4. **Commit changes.** Em ~1 minuto a notícia está no ar.

> Repare na **vírgula** no final do bloco. Todo item tem vírgula depois do `}`,
> menos o último da lista. Se errar isso, a lista de notícias não carrega.
> Para conferir antes de salvar, cole o conteúdo em `jsonlint.com`.

### Os campos

| Campo | Obrigatório | Observação |
|---|---|---|
| `titulo` | Sim | Curto e direto |
| `data` | Sim | Formato `AAAA-MM-DD` — é o que ordena a lista |
| `resumo` | Sim | 2 a 3 linhas |
| `categoria` | Não | Vira a etiqueta verde. Ex: `Abordagem Noturna` |
| `imagem` | Não | Deixe `""` para usar o fundo verde padrão |
| `link` | Não | Se preenchido, aparece o botão "Ler mais" |

### Como funciona a exibição

- A notícia com a **data mais recente** vira o card grande em destaque.
- As demais viram cards menores, em ordem decrescente de data.
- A ordem dentro do arquivo não importa — quem manda é a data.
- Com lista vazia, aparece "Em breve, as novidades do projeto aparecem aqui."

### Usando fotos

1. No repositório, crie a pasta `img` (**Add file → Create new file**, digite
   `img/.gitkeep` e salve).
2. Entre na pasta e use **Add file → Upload files** para subir as fotos.
3. No `noticias.json`, referencie assim: `"imagem": "img/mutirao-setembro.jpg"`

Redimensione as fotos para no máximo 1200px de largura antes de subir — foto de
celular tem 4000px e deixa o site lento.

### Abrindo o site no seu computador

Ao abrir `index.html` com dois cliques, as notícias **não aparecem** — o
navegador bloqueia a leitura do `.json` em arquivo local. Isso é normal e não é
erro. No site publicado funciona.

Para testar localmente, abra o terminal na pasta do projeto e rode:

```
python -m http.server 8000
```

Depois acesse `http://localhost:8000` no navegador.

---

## Quando migrar para algo maior

O `noticias.json` resolve bem até cerca de 30 notícias. A limitação real: as
notícias são montadas pelo navegador, então **o Google indexa mal** o conteúdo
delas, e cada notícia não tem endereço próprio para compartilhar.

Se a aba de notícias virar peça central da comunicação, o caminho é migrar para
um gerador de site estático — **Astro** ou **Eleventy**. Você escreve cada
notícia em Markdown, e no build cada uma vira uma página HTML de verdade, com
URL própria e indexação perfeita. A Cloudflare Pages roda o build sozinha a cada
`git push`. O custo é ter Node.js instalado e uma estrutura de projeto no lugar
do arquivo único.

Não faça essa migração agora. Faça quando o volume justificar.

## Pendências antes de divulgar

- [x] ~~Confirmar a chave PIX.~~ Confirmada e aplicada:
      `projetoatuarsemeandoamor@gmail.com`. É a mesma dos cartazes da campanha.
- [ ] **Apagar as duas notícias de exemplo** do `noticias.json` e publicar a
      primeira real.
- [ ] **Conferir os números.** 150+ encaminhamentos, 200+ pessoas/ano e 98% de
      satisfação vieram do site anterior. "4 frentes de atuação" foi contado a
      partir das ações listadas.
- [ ] **Trocar os links das redes sociais.** No rodapé, os quatro ícones
      (FB, IG, YT, TT) apontam para `#contato`. Substitua pelos endereços reais.
- [ ] **Revisar os depoimentos.** Confirmar se Jaqueline e Renato autorizam o
      uso dos nomes.
- [ ] **Benefício fiscal.** O texto de dedução no Imposto de Renda só se aplica
      a doações para entidade formalizada e qualificada. Confirme a situação
      jurídica do projeto antes de manter essa promessa no ar.

---

## Quando for integrar pagamento

A Cloudflare Pages suporta **Pages Functions** — basta criar uma pasta
`functions/` no repositório e cada arquivo `.js` vira um endpoint de backend.

Três regras que não podem ser quebradas:

1. **Chave secreta do gateway só no servidor**, como *secret* no painel da
   Cloudflare, lida via `context.env.NOME_DA_CHAVE`. Nunca no HTML.
2. **Validar o pagamento no backend.** O frontend pode ser manipulado — quem
   confirma "foi pago, valor certo" é a Function conversando com o gateway.
3. **Webhook com verificação de assinatura**, senão qualquer um envia uma
   confirmação falsa de pagamento.
