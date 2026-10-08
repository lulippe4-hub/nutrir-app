# Nutrir — App pessoal de nutrição

App de diário alimentar, registro de macros, plano de receitas e evolução de peso.
100% client-side: HTML + CSS + JS em um único arquivo (`index.html`), sem backend.

## ⚠️ Importante sobre os dados

Este app guarda tudo no `localStorage` **do navegador onde ele é aberto**.
Publicar no GitHub Pages dá um link próprio e estável — **não** sincroniza dados
entre aparelhos. Se abrir no celular e no notebook, são dois históricos
separados. Veja a seção "Próximo passo: sincronizar entre aparelhos" no fim
deste arquivo se isso virar um problema real pra você.

## Passo 1 — subir o código pro GitHub (sem precisar instalar nada)

1. Crie um repositório novo em https://github.com/new
   - Nome sugerido: `nutrir-app`
   - Pode deixar **Public** (o código é só HTML/CSS/JS, nada sensível —
     seus dados pessoais nunca saem do seu navegador e nunca vão pro repo)
2. Na página do repositório recém-criado, clique em **"uploading an existing file"**
   e arraste `index.html`, `vercel.json` e `README.md` (não precisa instalar
   `git` nem usar terminal)
3. Clique em **Commit changes**

## Passo 2 — conectar o repositório ao Vercel

1. Crie uma conta em https://vercel.com (dá pra entrar direto com sua conta
   do GitHub, sem precisar criar senha nova)
2. Clique em **Add New → Project**
3. Escolha **Import Git Repository** e selecione o `nutrir-app`
4. Na tela de configuração: Framework Preset = **Other** (ele detecta
   sozinho que é estático por causa do `vercel.json`). Não precisa mudar
   mais nada.
5. Clique em **Deploy**
6. Em ~30 segundos o app estará em:
   `https://nutrir-app-SEUUSUARIO.vercel.app` (ou o nome que você escolher
   na tela de import)
7. No celular, abra esse link e use **"Adicionar à tela de início"**
   (iOS Safari ou Android Chrome) para ele virar um atalho tipo app.

## Atualizando depois de uma mudança

Sempre que eu (ou você) alterar o `index.html`, repita o upload pela
interface web do GitHub (botão "Add file → Upload files", substituindo o
arquivo). O Vercel detecta o novo commit sozinho e republica automaticamente
— não precisa voltar no Vercel pra nada.

## Alternativa sem conta nova: GitHub Pages

Se preferir não criar conta no Vercel agora, dá pra usar só o GitHub Pages:
**Settings → Pages → Source: Deploy from a branch → `main` / `(root)` → Save**.
Fica em `https://SEU-USUARIO.github.io/nutrir-app/`. Funciona igualmente bem
pra esse app estático — só não tem a parte de função serverless citada abaixo.

## Próximo passo: sincronizar entre aparelhos

Duas rotas possíveis, em ordem de recomendação:

1. **Capacidade `db` do Claude Artifacts** — já diponível nesta conversa,
   zero configuração, privado por usuário. Me peça quando quiser migrar.
2. **Backend real (ex: Supabase)** — grátis até certo volume, dá autenticação
   de verdade e um banco Postgres por trás. Mais trabalho de implementação,
   mas é o caminho "profissional" se este app crescer.

Evite usar a API do GitHub como banco de dados (gravando um JSON no repo a
cada ação do app): exigiria expor um token de acesso dentro do código
JavaScript que roda no seu navegador — qualquer pessoa que abrir o
"Ver código-fonte" da página veria o token. Funciona como exercício de
aprendizado, mas não é seguro para uso real.
