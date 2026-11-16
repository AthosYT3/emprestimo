# Empréstimos

Tela preta com cinco campos: nome, quantidade emprestada, quanto a receber, porcentagem e data para receber. Informar o valor a receber calcula a porcentagem; informar a porcentagem calcula o valor a receber. A última dessas duas entradas editada é usada quando o principal muda. Juros são uma taxa total única, não mensal. O valor combinado é salvo em centavos para evitar perdas de arredondamento.

O resumo mostra total original emprestado, saldo total a receber e quantidade de empréstimos em aberto. Cada registro exibe o número de dias desde o cadastro, vencimento e saldo. Marcar recebido quita o saldo; Desfazer reverte essa marcação. Pagamentos anteriores são preservados.

Os registros existentes continuam na chave localStorage em-dia-v1. Dados são locais ao navegador e ao endereço, sem sincronização. Abra dist/index.html ou sirva dist com um servidor HTTP.

## Arquitetura

Aplicação estática: a Vercel entrega HTML, CSS e JavaScript; o navegador executa os cálculos e salva os empréstimos em `localStorage`. Não utiliza servidor de aplicação, funções serverless, banco de dados, dependências ou variáveis de ambiente.

```text
dist/
  index.html       # Página inicial e formulário
  style.css        # Interface responsiva
  app.js           # Cálculos, listagem e armazenamento local
vercel.json        # Configuração de hospedagem
.vercelignore      # Arquivos excluídos do upload pela CLI
.gitignore         # Configurações locais e segredos fora do Git
.openai/           # Configuração da hospedagem anterior (fora de dist)
```

A pasta `dist` é versionada e contém os arquivos prontos para publicação. Não há etapa de compilação. A página inicial está em `/`, com os arquivos `/style.css` e `/app.js`. Como a aplicação tem uma única página e não usa rotas de cliente, não precisa de redirecionamento geral para `index.html`.

## Hospedar na Vercel pelo GitHub

1. Na Vercel, selecione **Add New → Project** e importe `AthosYT3/emprestimo`.
2. Use a raiz do repositório como **Root Directory** (`.`); não selecione `dist` como raiz.
3. O arquivo `vercel.json` configura **Framework Preset: Other**, **Output Directory: dist** e comandos de instalação e build vazios.
4. Não é necessário cadastrar variáveis de ambiente. Clique em **Deploy**.
5. Mantenha `main` como branch de produção para publicar os próximos pushes pela integração do GitHub.

Depois do deploy, abra a URL fornecida pela Vercel. Confira que R$ 1.000 emprestados e R$ 1.200 a receber calculam 20%; altere a porcentagem para 15% e confira R$ 1.150 a receber.

Alternativa pela CLI oficial, executada na raiz do repositório:

```sh
npx vercel
npx vercel --prod
```

O primeiro comando vincula o projeto à sua conta e cria uma prévia; o segundo publica em produção. A pasta local `.vercel` não é enviada ao GitHub.

## Persistência dos dados

Os registros não são armazenados na Vercel. Eles ficam no navegador e no domínio em que foram cadastrados. URLs de prévia, domínio de produção e o endereço da hospedagem anterior têm armazenamentos separados. A troca de endereço não transfere registros automaticamente. Limpar os dados do navegador pode apagar os empréstimos. Sincronização entre dispositivos exige uma futura integração com autenticação e banco de dados.

Referência: [configuração oficial da Vercel](https://vercel.com/docs/project-configuration/vercel-json).
