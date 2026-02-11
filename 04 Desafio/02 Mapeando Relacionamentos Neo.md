# Desafio
Você foi contratado como programador em uma equipe de desenvolvimento que está integrando um sistema de gerenciamento de amizades com a base de dados gráfica Neo4j. Sua missão é criar um componente inteligente para determinar rapidamente o status de conexão entre pares de usuários.

Sua tarefa é construir uma função que, dada uma lista de usuários cadastrados e pares de relacionamentos declarados como amizades, responda se um usuário está diretamente conectado a outro (se são amigos diretos). Para cada consulta da equipe, informe se existe uma ligação direta entre os usuários especificados. Utilize estruturas de dados básicas para registrar e consultar essas conexões de maneira eficiente, sem a necessidade de integrações externas ou bibliotecas avançadas.

## Entrada
A entrada será composta por três linhas.
A primeira linha traz os nomes dos usuários separados por espaço.
A segunda linha lista todos os pares de amizades diretas, onde cada par é formado por dois nomes separados por traço, e pares diferentes são separados por espaço.
A terceira linha traz o par da consulta: dois nomes, separados por espaço, indicando os usuários a serem analisados.

## Saída
Imprima 'Conectados' se o primeiro usuário da consulta tem amizade direta com o segundo.
Imprima 'Nao conectados' caso contrário.

# Exemplos

A tabela abaixo apresenta exemplos de entrada e saída:

| **Entrada**    | **Saída**     |
|----------------|---------------|
| Ana Beto Carla | Ana-Beto Beto-Carla |
| Ana Beto       | Conectados    |
| Joao Lia Vini  | Joao-Vini Joao-Lia |
| Lia Vini       | Nao conectados |
| Lucas Mara     | Lucas-Mara    |
| Mara Lucas     | Conectados    |
