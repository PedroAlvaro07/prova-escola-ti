## Spec - sistema de Inscrição de aulas

Implemente somente o que está nesta spec. Os nomes dos campos e das rotas devem ser usados exatamente como estão escritos aqui.

# Regras de Negocio



# Entidades
- bilhete: placa (string, maiusculo, ex: "ABC1D23"), 

# Casos de Uso:
 
- UC1 (abrir Bilhete):
    - Rota: POST /bilhetes
    - Entrada: campo "placa" é um campo obrigatório que contem a placa do vaiculo com 7 caracteres em alfanumérico sem em maiusculo; 
    - Resposta de Sucesso: Cadastrar um bilhete com o campa "placa" válido retorna status 201 com o corpo {"id": 1, "placa": "ABC1D23", "entrada": "<ISO-8601 com fuso -03:00>", "status": "aberto"}.
    - Erros: Campo obrigatorio mal informado retorna erro status 400.
    - Criterios de Aceite:
        - Ao cadastrar um bilhete com o campo "placa" informado corretamente retorna status 201
        - Ao cadastrar um bilhete com o campo "placa" informado de maneira incorreta

# Fora de escopo

Não implementar: autenticação, paginação, editar ou apagar aulas, e rotas ou campos que não estejam nesta spec.