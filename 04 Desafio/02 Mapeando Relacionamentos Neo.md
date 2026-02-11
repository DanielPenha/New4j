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

---
## Modelo base:
```Python
# Leitura da lista de usuários
usuarios = input().strip().split()

# Inicialização das amizades
amizades = {usuario: set() for usuario in usuarios}

# Leitura dos pares de amizades diretas (ex: "A-B")
for par in input().strip().split():
    a, b = par.split('-')
    amizades[a].add(b)
    amizades[b].add(a)

# Leitura dos dois usuários para consulta
usuario1, usuario2 = input().strip().split()

# TODO: Verifique se existe uma cadeia de amizades (direta ou indireta) entre usuario1 e usuario2
# Imprima 'Conectados' se existir conexão entre eles, senão imprima 'Nao conectados'
# Dica: Considere usar algum algoritmo de busca (vale a pena estudar) para percorrer os amigos e amigos dos amigos
```
---
# Resolução do Problema: 
## Mapeando Relacionamentos Neo

Esse desafio envolve determinar se dois usuários estão diretamente conectados (ou seja, se são amigos diretos) em um sistema de amizades, que pode ser modelado como um grafo simples onde os nós são os usuários e as arestas são as amizades.

Vamos completar o código utilizando uma estrutura de dicionário de conjuntos (set) para armazenar as amizades diretas e uma busca simples para verificar se existe uma ligação direta entre os dois usuários consultados.

Aqui está o código completo para resolver o desafio:

## Código:
```python
# Leitura da lista de usuários
usuarios = input().strip().split()

# Inicialização das amizades
amizades = {usuario: set() for usuario in usuarios}

# Leitura dos pares de amizades diretas (ex: "A-B")
for par in input().strip().split():
    a, b = par.split('-')
    amizades[a].add(b)
    amizades[b].add(a)

# Leitura dos dois usuários para consulta
usuario1, usuario2 = input().strip().split()

# Verifique se existe uma amizade direta entre os dois usuários
if usuario2 in amizades[usuario1]:
    print('Conectados')
else:
    print('Nao conectados')
```

# Explicação do código:

## 1. Leitura da lista de usuários:

A linha usuarios = input().strip().split() lê a entrada contendo os nomes dos usuários e os separa em uma lista.

## 2. Inicialização do dicionário de amizades:

A linha amizades = {usuario: set() for usuario in usuarios} cria um dicionário onde cada chave é o nome de um usuário e o valor associado é um conjunto (set) que armazenará os amigos diretos desse usuário.

### 3. Leitura dos pares de amizades diretas:

A linha for par in input().strip().split() percorre a entrada que contém os pares de amizades. Para cada par (como "Ana-Beto"), os nomes dos usuários são extraídos usando a, b = par.split('-'), e em seguida adicionamos b à lista de amigos de a e a à lista de amigos de b. Isso garante que o relacionamento de amizade seja bidirecional.

## 4. Leitura dos usuários a serem consultados:

A linha usuario1, usuario2 = input().strip().split() lê os dois nomes dos usuários que precisam ser analisados para saber se são amigos diretos.

## 5. Verificação de amizade direta:

O código verifica se usuario2 está presente no conjunto de amigos de usuario1 com if usuario2 in amizades[usuario1]. Se sim, imprime 'Conectados'; caso contrário, imprime 'Nao conectados'.

### Exemplos de entrada e saída:
#### Exemplo 1:
Entrada:
Ana Beto Carla
Ana-Beto Beto-Carla
Ana Beto

Saída:
Conectados

#### Exemplo 2:
Entrada:
Joao Lia Vini
Joao-Vini Joao-Lia
Lia Vini

Saída:
Nao conectados

#### Exemplo 3:
Entrada:
Lucas Mara
Lucas-Mara
Mara Lucas

Saída:
Conectados

## Considerações:

O código trata a verificação de amizade direta, ou seja, a consulta é apenas sobre conexões imediatas, sem considerar amizades indiretas (por exemplo, amigos de amigos).

O uso de conjuntos (sets) permite que as verificações de amizade sejam feitas de forma eficiente, com complexidade média de O(1) para cada busca de amizade.
