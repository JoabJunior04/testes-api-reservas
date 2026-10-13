# Testes de API — Reservas

Projeto de estudo de testes de API com Postman, utilizando a API pública Restful Booker.

## Objetivo

Praticar testes de cadastro, consulta, alteração, exclusão e autenticação, com verificações automáticas e análise de cenários negativos.

## Ferramentas utilizadas

- Postman
- JavaScript para as verificações dos testes
- GitHub para publicação e documentação

## Cenários testados

| Cenário | Verificação |
| --- | --- |
| Listar reservas | Código 200 e resposta em formato de lista |
| Cadastrar reserva | Código 200 e identificador numérico |
| Consultar reserva cadastrada | Código 200, nome, sobrenome e preço cadastrado |
| Gerar token | Código 200 e token preenchido |
| Alterar reserva | Código 200 e preço atualizado para 200 |
| Consultar após alteração | Confirmação dos dados e do preço atualizado |
| Excluir reserva | Código 201, conforme o comportamento desta API |
| Consultar após exclusão | Código 404 |
| Autenticar com senha incorreta | Mensagem de credenciais incorretas e ausência de token |
| Cadastrar sem nome | Comparação entre o critério proposto de 400 e o retorno observado de 500 |

## Como executar

1. Baixe o arquivo `testes-api-reservas.postman_collection.json` deste repositório.
2. Abra o Postman e clique em **Import**.
3. Selecione o arquivo baixado.
4. Abra a coleção **Testes de API — Reservas**.
5. Escolha **Run collection**.
6. Mantenha as dez requisições selecionadas na ordem da coleção.
7. Configure uma iteração e execute.
8. Confira os resultados dos testes.

Não é necessário preencher manualmente as variáveis `bookingid` e `token`: elas são definidas pelos scripts de cadastro e autenticação durante a execução.

## Resultados e observações

O fluxo de cadastro, consulta, autenticação, alteração e exclusão foi executado com sucesso em uma execução completa, com 14 verificações aprovadas.

O cenário de senha incorreta também teve suas duas verificações aprovadas. A API retornou código 200, mas informou `Bad credentials` e não forneceu um token. Esse cenário demonstra por que é necessário verificar o conteúdo da resposta, além do código HTTP.

### Cadastro sem o campo firstname

Ao enviar uma reserva sem o campo `firstname`, a API retornou:

- Código HTTP: **500 Internal Server Error**
- Corpo da resposta: `Internal Server Error`

Para este projeto, foi proposto o critério de **400 Bad Request**, acompanhado de uma mensagem clara sobre o campo ausente. Esse critério não foi confirmado como uma exigência da documentação da API.

O teste permanece falhando para tornar visível a diferença entre o critério proposto e o comportamento observado. Essa falha deve ser analisada ao executar a coleção.

## Limitações

A API é pública e compartilhada. Os dados podem ser alterados ou removidos por outros usuários, afetando os resultados.

Execute a coleção na ordem definida para criar uma nova reserva e utilizar seu identificador nas etapas seguintes.

## Aprendizados

- Utilização dos métodos GET, POST, PUT e DELETE.
- Leitura de respostas e códigos HTTP.
- Criação de verificações automáticas no Postman.
- Uso de variáveis de coleção.
- Testes de cenários positivos e negativos.
- Registro de resultados e observações de tratamento de erros.

## Referência

Documentação da API:

https://restful-booker.herokuapp.com/apidoc/index.html
