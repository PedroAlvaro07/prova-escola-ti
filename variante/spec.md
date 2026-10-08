## Spec - sistema de Inscrição de aulas

Implemente somente o que está nesta spec. Os nomes dos campos e das rotas devem ser usados exatamente como estão escritos aqui.

# Regras de Negocio
- RN1: 

# Entidades
- bilhete: placa (string, maiusculo, ex: "ABC1D23"), status (string, assume somente os vlaores "aberto" ou "fechado"), entrada (dateTime, formato <ISO-8601 com fuso -03:00>), saida (dateTime, formato <ISO-8601 com fuso -03:00>), valor_centavos(int, valor numérico com o calculo do valor dos centavos)

# Casos de Uso:
 
- UC1 (abrir Bilhete):
    - Rota: POST /bilhetes
    - Entrada: campo "placa" é um campo obrigatório que contem a placa do vaiculo com 7 caracteres em alfanumérico sem em maiusculo; posssui campo entrada opcional que pode ser informado, caso seja, deve ser no formato "entrada": "<ISO-8601 com fuso -03:00> 
    - Resposta de Sucesso: Cadastrar um bilhete com o campa "placa" válido retorna status 201 com o corpo {"id": 1, "placa": "ABC1D23", "entrada": "<ISO-8601 com fuso -03:00>", "status": "aberto"}.
    - Erros: Campo obrigatorio mal informado retorna erro status 400.
    - Criterios de Aceite:
        - Ao cadastrar um bilhete com o campo "placa" informado corretamente retorna status 201.
        - Ao cadastrar um bilhete com o campo "placa" e campo " entrada com valores válidops retorna status 201.
        - Ao cadastrar um bilhete com o campo "placa" informado de maneira incorreta retorna erro com status 400.
        - Ao cadastrar um bilhete com o campo "placa" com um valor que já exista retorna erro com status 409.
        - Ao cadastrar um bilhete com o campo "entrada" com um valor invalido retorna erro com status 400.

- UC2 (Encerar Bilhete):
    - Rota: POST /bilhetes/{id}/encerramento
    - Entrada: Sem corpo, informar somente o id fo bilhete no corpo da url
    - Resposta de Sucesso: informado o id na url retorna status 200.
    - Erros: id informado de maneira indevida retorna erro 400.
    - Criterios de Aceite:
        - Ao informar o id do bilhete no corpo da url retorna status 200.
        - Ao Não informar o id do bilhete no corpo da url retorna erro status 400.
        - Ao informar um id já encerrado no corpo da url retorna erro status 409.

- UC3 (Listar Ativos):
    - Rota: GET /bilhetes/ativos
    - Entrada: Sem corpo, informar somente url
    - Resposta de Sucesso: status 200 com array de bilhetes com status aberto.
    - Erros: retorna erro status 404.
    - Criterios de Aceite:
        - Ao informar a Url corretamente retorna status 200 com array de bilhetes 

# Fora de escopo

Não implementar: autenticação, paginação, editar ou apagar aulas, e rotas ou campos que não estejam nesta spec.