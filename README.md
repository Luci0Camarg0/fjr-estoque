# Estoque FJR Solutions

Estoque de mantas (rolos de 1,20 × 12 m) e baldes de tinta. Site: https://luci0camarg0.github.io/fjr-estoque/

## Como usar

- **Mantas** e **Baldes de tinta**: cada aba mostra as cores/tintas. Clique numa para ver um ícone por rolo ou balde: **Lacrada** (100%, com o selo) ou **Aberta** (quanto já foi usado e quanto resta).
- Clique num rolo ou balde para registrar quanto foi usado, corrigir o que resta ou marcar que acabou.
- **Novo tapete** (dentro da cor): digite a medida (ex.: 1,00 × 0,60). O site escolhe a manta, mostra no desenho onde cortar e, ao confirmar, calcula sozinho os pedaços que sobram. Pedaços que sobraram são usados antes de avançar no rolo ou abrir uma manta lacrada.
- Medidas sempre como **comprimento × largura**. O tapete pode ser girado ("Girar o tapete"). Um corte errado se desfaz em **Cortes feitos**.
- **Editar** (dentro da cor) muda nome, cor, foto e o tamanho padrão do rolo/balde.

## Arquivos

- `index.html`: o site.
- `config.js`: configuração do banco de dados (Firebase).
- `img/`: fotos das mantas e a logo.
- `firestore.rules`: regras de acesso do banco de dados.

## Banco de dados compartilhado (Firebase, grátis)

Sem isso o site fica em **modo demonstração**: cada navegador guarda os próprios dados.

1. Entre em https://console.firebase.google.com com uma conta Google e clique em **Criar um projeto** (ex.: `fjr-estoque`). O Google Analytics pode ficar desligado.
2. Abra **Criação > Firestore Database > Criar banco de dados**. Local `southamerica-east1 (São Paulo)`, **modo de produção**.
3. Na aba **Regras**, apague tudo, cole o conteúdo do arquivo `firestore.rules` e clique em **Publicar**.
4. Abra **Configurações do projeto** (engrenagem) > **Seus apps** > ícone **</>** (Web), dê um nome e clique em **Registrar app**. Copie o objeto `firebaseConfig`.
5. No GitHub, abra o `config.js`, clique no lápis, troque `window.FJR_FIREBASE = null;` por `window.FJR_FIREBASE = { ...o objeto copiado... };` e clique em **Commit changes**.

## Segurança

Por enquanto não há login: **qualquer pessoa com o link pode ver e alterar o estoque**. Não divulgue o link fora da equipe. Para exigir login no futuro, ative **Authentication > E-mail/senha** no Firebase e troque a linha de `write` no `firestore.rules`.
