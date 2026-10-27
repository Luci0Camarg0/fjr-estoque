# Mantas FJR Solutions

Catálogo e controle de estoque das mantas: rolos de 1,20 × 12 m, pedidos de corte e sobras.

## Arquivos

- `index.html`: o site.
- `config.js`: onde fica a configuração do banco de dados (Firebase).
- `img/`: fotos das mantas e a logo.
- `firestore.rules`: regras de acesso do banco de dados.

## 1. Colocar o site no ar (GitHub Pages, grátis)

1. Entre em https://github.com e crie uma conta, se ainda não tiver.
2. Clique em **New repository**, dê o nome `fjr-estoque`, marque **Public** e clique em **Create repository**.
3. Na página do repositório, clique em **uploading an existing file** e arraste **todo o conteúdo desta pasta** (o `index.html`, o `config.js`, a pasta `img` etc.). Clique em **Commit changes**.
4. Vá em **Settings > Pages**. Em **Branch**, escolha `main` e `/ (root)` e clique em **Save**.
5. Depois de 1 ou 2 minutos, o site fica em `https://SEU-USUARIO.github.io/fjr-estoque/`.

Até fazer o passo 2, o site funciona em **modo demonstração**: cada navegador guarda os próprios dados.

## 2. Banco de dados compartilhado (Firebase, grátis)

Serve para a equipe toda ver o mesmo estoque e para só quem tem login poder editar.

1. Entre em https://console.firebase.google.com com uma conta Google e clique em **Criar projeto** (ex.: `fjr-estoque`). O Google Analytics pode ficar desligado.
2. No menu, abra **Firestore Database > Criar banco de dados**. Escolha a região `southamerica-east1 (São Paulo)` e o **modo de produção**.
3. Na aba **Regras** do Firestore, apague tudo, cole o conteúdo do arquivo `firestore.rules` e clique em **Publicar**.
4. No menu, abra **Authentication > Começar > E-mail/senha**, ative e salve. Na aba **Usuários**, clique em **Adicionar usuário** para cada pessoa da equipe (e-mail e senha).
5. Abra **Configurações do projeto** (engrenagem) > **Seus apps** > ícone **</>** (Web). Dê um nome e clique em **Registrar app**. Copie o objeto `firebaseConfig`.
6. No `config.js`, troque `window.FJR_FIREBASE = null;` pelo objeto copiado, assim:
   ```js
   window.FJR_FIREBASE = { apiKey: "...", authDomain: "...", projectId: "...", storageBucket: "...", messagingSenderId: "...", appId: "..." };
   ```
   No GitHub, abra o `config.js`, clique no lápis, cole e clique em **Commit changes**.
7. Em **Authentication > Configurações > Domínios autorizados**, adicione `SEU-USUARIO.github.io`.

Pronto: abra o site, clique em **Entrar** com um dos usuários criados e o catálogo das 18 cores é montado sozinho.

## Quem vê o quê

- Qualquer pessoa com o link vê o catálogo, os rolos e as sobras.
- Pedidos (com nome de cliente) só aparecem para quem entrou com login.
- Só quem entrou com login cria pedidos, adiciona rolos ou edita produtos.
