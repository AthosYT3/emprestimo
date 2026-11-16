# Em dia

Controle simples de empréstimos em português, sem dependências. Abra `dist/index.html` no navegador ou sirva a pasta `dist` com um servidor HTTP estático.

Cadastre nome, telefone, valor, juros totais, data, vencimento e observações. Registre pagamentos parciais e consulte o histórico. O saldo considera uma taxa única de juros sobre o principal; não há juros mensais ou multas automáticas. Valores são armazenados em centavos.

Os registros ficam no localStorage do navegador, sem sincronização entre dispositivos. Use Exportar backup e Importar para guardar e transferir seus dados. A importação substitui os registros após confirmação. Abrir o arquivo local e usar o endereço publicado são armazenamentos separados.
