# Estoque FJR Solutions

Estoque de mantas (rolos de 1,20 × 12 m) e baldes de tinta. Site: https://fjrsolutions.web.app (cópia também em https://luci0camarg0.github.io/fjr-estoque/)

## Como usar

- **Mantas** e **Baldes de tinta**: cada aba mostra as cores/tintas. Clique numa para ver um ícone por rolo ou balde: **Lacrada** (100%, com o selo) ou **Aberta** (quanto já foi usado e quanto resta).
- Clique num rolo ou balde para registrar quanto foi usado, corrigir o que resta ou marcar que acabou.
- **Novo tapete** (dentro da cor): digite a medida (ex.: 1,00 × 0,60). O site escolhe a manta, mostra no desenho onde cortar e, ao confirmar, calcula sozinho os pedaços que sobram. Pedaços que sobraram são usados antes de avançar no rolo ou abrir uma manta lacrada.
- Medidas sempre como **comprimento × largura**. O tapete pode ser girado ("Girar o tapete"). Um corte errado se desfaz em **Cortes feitos**.
- **Aprovados**: artes aprovadas pelo cliente, prontas para a produção. Em **Adicionar arte**, escolha a imagem e preencha cliente, medidas, quantidade, cor do tapete e data. Ao terminar o tapete, abra a arte e clique em **Marcar como pronta**.
- **Editar** (dentro da cor) muda nome, cor, foto e o tamanho padrão do rolo/balde.

## Arquivos

- `index.html`: o site.
- `config.js`: configuração do banco de dados (Firebase).
- `img/`: fotos das mantas e a logo.
- `firestore.rules`: regras de acesso do banco de dados.

## Banco de dados (Firebase)

O estoque fica no Firebase, projeto `fjr-estoque` (Firestore em São Paulo): todo mundo que abre o site vê os mesmos dados, em tempo real.
A ligação está no `config.js`. Se o banco não responder, o site mostra "Sem conexão com o estoque" em vez de guardar dados só no aparelho.
As regras de acesso estão em `firestore.rules`. Para mudar, cole o arquivo em **Firestore Database > Regras** no console do Firebase e clique em **Publicar**.

## Segurança

Por enquanto não há login: **qualquer pessoa com o link pode ver e alterar o estoque**. Não divulgue o link fora da equipe. Para exigir login no futuro, ative **Authentication > E-mail/senha** no Firebase e troque a linha de `write` no `firestore.rules`.
