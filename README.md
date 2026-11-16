# Empréstimos

Tela preta com cinco campos: nome, quantidade emprestada, quanto a receber, porcentagem e data para receber. Informar o valor a receber calcula a porcentagem; informar a porcentagem calcula o valor a receber. A última dessas duas entradas editada é usada quando o principal muda. Juros são uma taxa total única, não mensal. O valor combinado é salvo em centavos para evitar perdas de arredondamento.

O resumo mostra total original emprestado, saldo total a receber e quantidade de empréstimos em aberto. Cada registro exibe o número de dias desde o cadastro, vencimento e saldo. Marcar recebido quita o saldo; Desfazer reverte essa marcação. Pagamentos anteriores são preservados.

Os registros existentes continuam na chave localStorage em-dia-v1. Dados são locais ao navegador e ao endereço, sem sincronização. Abra dist/index.html ou sirva dist com um servidor HTTP.
