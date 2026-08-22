# Como publicar o acervo

Guia passo a passo. Não é preciso saber programar — só seguir na ordem.

O resultado final é um endereço na internet, tipo `seuusuario.github.io/acervo`,
que abre no celular e no computador, com busca em todos os fichamentos ao mesmo
tempo. É gratuito e não tem limite prático de espaço.

---

## Antes de começar

Você precisa de:

- Uma conta no GitHub (gratuita — github.com)
- Esta pasta `acervo-site` no seu computador

---

## Passo 1 — Criar o repositório

1. Entre no GitHub e clique em **New repository** (botão verde, canto superior).
2. Em **Repository name**, escreva `acervo`.
3. Deixe marcado **Public**. *(Repositório privado também funciona, mas o
   GitHub Pages gratuito só publica site a partir de repositório público.)*
4. **Não marque** nenhuma das caixas de "Add a README", ".gitignore" ou "license" —
   esses arquivos já existem aqui e marcar criaria conflito.
5. Clique em **Create repository**.

## Passo 2 — Enviar os arquivos

Na tela que aparece depois de criar, procure o link **uploading an existing file**.

1. Clique nele.
2. Arraste **todo o conteúdo** da pasta `acervo-site` para a área de upload —
   `mkdocs.yml`, `requirements.txt`, a pasta `docs` inteira e a pasta `.github`.
3. Clique em **Commit changes**.

!!! Atenção com a pasta `.github`
    Pastas que começam com ponto ficam ocultas em alguns sistemas. No Windows,
    ative "Itens ocultos" na aba Exibir do Explorador de Arquivos. No Mac, use
    `Cmd + Shift + .` no Finder. Se essa pasta não subir, a publicação automática
    não funciona.

## Passo 3 — Ligar a publicação

1. No repositório, clique na aba **Settings**.
2. No menu da esquerda, clique em **Pages**.
3. Em **Source**, escolha **GitHub Actions**.
4. Pronto. Não precisa salvar nada além disso.

## Passo 4 — Esperar e abrir

Vá na aba **Actions**. Vai aparecer um processo chamado "Publicar acervo" rodando.
Leva de 1 a 3 minutos na primeira vez.

Quando ficar com um ✓ verde, seu site está no ar em:

```
https://SEUUSUARIO.github.io/acervo
```

*(troque `SEUUSUARIO` pelo seu nome de usuário do GitHub)*

---

## Adicionar uma obra fichada

Sempre que houver um fichamento novo:

1. No GitHub, entre na pasta `docs/fichamentos`.
2. Clique em **Add file → Upload files** e envie o `.md` da obra.
3. Edite `mkdocs.yml` (clique no arquivo, depois no ícone de lápis) e acrescente
   uma linha na seção `nav`, dentro de "Fichamentos":

   ```yaml
     - Fichamentos:
         - fichamentos/index.md
         - Modelo de fichamento: fichamentos/modelo.md
         - Schoenfeld 2017 — Volume: fichamentos/schoenfeld-2017-volume.md   # linha nova
   ```

4. Edite `docs/index.md` para atualizar o índice: obra na tabela 1, temas no mapa
   temático 2, divergências novas na tabela 3.
5. Commit. O site se republica sozinho em cerca de 2 minutos.

---

## Ver o site no seu computador antes de publicar

Opcional, mas útil se quiser conferir antes de subir. Precisa do Python instalado.

```bash
pip install -r requirements.txt
mkdocs serve
```

Abra `http://127.0.0.1:8000` no navegador. Ele atualiza sozinho a cada vez que
você salva um arquivo. Para parar, `Ctrl + C` no terminal.

---

## O que cada arquivo faz

| Arquivo | Função |
|---|---|
| `mkdocs.yml` | Configuração do site — menu, tema, extensões. É onde se registra cada fichamento novo. |
| `requirements.txt` | Lista dos programas que o GitHub instala para montar o site. Não precisa mexer. |
| `.github/workflows/deploy.yml` | Instrução de publicação automática. Não precisa mexer. |
| `docs/index.md` | A página inicial — o índice do acervo. |
| `docs/metodo.md` | O protocolo de fichamento. |
| `docs/referencias.md` | O mapa de obras recomendadas ainda não fichadas. |
| `docs/fichamentos/` | Uma página por obra fichada. |
| `docs/stylesheets/extra.css` | A identidade visual — cores, tipografia, carimbos. |

---

## Marcadores prontos para usar nos fichamentos

Cole direto no markdown:

```html
<span class="obra">OBRA</span>
<span class="comentario">COMENTÁRIO</span>
<span class="nao-encontrado">NÃO ENCONTRADO</span>
```

E no índice, para o mapa temático:

```html
<span class="st-lacuna">lacuna</span>
<span class="st-superficial">superficial</span>
<span class="st-profundo">profundo</span>
```

---

## Se algo der errado

**A publicação falhou (✗ vermelho na aba Actions).** Clique no processo que falhou
e leia a última linha em vermelho. Quase sempre é um arquivo listado no `nav` do
`mkdocs.yml` que não existe na pasta `docs` — nome digitado diferente, ou o arquivo
não foi enviado.

**O site abriu sem cores nem formatação.** Falta a pasta `docs/stylesheets`. Envie-a
de novo.

**O menu não mostra um fichamento novo.** Ele não foi acrescentado ao `nav` do
`mkdocs.yml`.
