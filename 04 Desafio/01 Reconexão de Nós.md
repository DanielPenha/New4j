# Desafio
Em uma corporação moderna, analistas de dados usam Neo4j para mapear as relações entre pessoas, projetos e ideias. Recentemente, um incidente bagunçou parte das conexões da base: a ordem dos relacionamentos (representados por nomes de nós ligados por setas) ficou invertida! Seu papel é criar uma função que receba uma lista sequencial de nós conectados e reorganize a ordem dessas conexões, permitindo a visualização correta do caminho na rede Neo4j. Fazer isso de forma rápida é essencial para retomar operações inteligentes.

Implemente um programa que receba uma cadeia de nomes de nós separados por '->', representando o caminho entre eles em ordem invertida. Sua tarefa é imprimir esse caminho na ordem correta de conexão para facilitar futuras integrações inteligentes com o banco de dados. Utilize estruturas de dados básicas, como listas ou filas, conforme preferir. Atenção: preserve exatamente os nomes e o formato na saída.

## Entrada
Uma única linha contendo nomes de nós separados por '->', representando um caminho invertido. Todos os nomes são sequências não vazias de letras e digitos, sem espaços.

## Saída
Uma única linha contendo os mesmos nomes de nós, na ordem correta, separados por '->'. O formato deve ser idêntico ao de entrada, apenas invertendo a ordem dos nós.

Exemplos
A tabela abaixo apresenta exemplos de entrada e saída:


| Entrada       | Saída         |
|---------------|---------------|
| JULIA->MARK->RAFA | RAFA->MARK->JULIA |
| X5->N2        | N2->X5        |
| USUARIO1      | USUARIO1      |

---
## Modelo base:
```python
# Lê a linha de entrada representando um caminho entre nós (exemplo: A->B->C)
entrada = input().strip()

# Separa os nós usando o delimitador '->' para montar uma lista de nós
nos = entrada.split('->')

# TODO: Inverta a lista de nós para que o caminho fique na ordem correta do grafo
# Dica: Você pode utilizar slicing para inverter listas em Python
nos_invertidos = None

# Concatena os nós invertidos no formato esperado (usando '->' como separador)
print('->'.join(nos_invertidos))
```
---
# Resolução do Problema: 
## Inverter a sequência de nós

Esse desafio é interessante, e para resolvê-lo, você já tem uma boa estrutura de código no modelo que forneceu. O principal objetivo é inverter a sequência de nós para restaurar a ordem correta das conexões. Vamos completar o código seguindo as dicas e o raciocínio para manipulação de listas em Python.

## Código:

Aqui está a versão completa do código para resolver o problema:

```python
# Lê a linha de entrada representando um caminho entre nós (exemplo: A->B->C)
entrada = input().strip()

# Separa os nós usando o delimitador '->' para montar uma lista de nós
nos = entrada.split('->')

# Inverte a lista de nós para que o caminho fique na ordem correta do grafo
nos_invertidos = nos[::-1]

# Concatena os nós invertidos no formato esperado (usando '->' como separador)
print('->'.join(nos_invertidos))
```

## Explicação do Código:
### 1. Entrada:

O código começa lendo a entrada do usuário com a função input().strip().
input() lê a linha que o usuário digita.
strip() remove espaços extras no início e no fim da string, garantindo que a entrada seja limpa e sem espaços indesejados.

Exemplo de entrada:
Se o usuário digitar: JULIA->MARK->RAFA , o strip() vai remover os espaços em branco e deixar o valor como: JULIA->MARK->RAFA.

### 2. Separação dos nós:

A função split('->') é utilizada para separar a string com o caminho entre os nós, dividindo-a pelo delimitador '->'. Isso cria uma lista de nós, onde cada elemento é um nome de nó.
A expressão entrada.split('->') transforma a string de entrada em uma lista de elementos.

Exemplo:
Com a entrada JULIA->MARK->RAFA, o resultado de split('->') será:

['JULIA', 'MARK', 'RAFA']

### 3. Inversão da lista:

A expressão nos[::-1] é utilizada para inverter a lista de nós.
O slicing [::-1] é uma maneira simples e eficiente de inverter uma lista em Python.
Isso faz com que a lista fique na ordem inversa, de modo a restaurar a sequência correta dos nós.

Exemplo:
Para a lista ['JULIA', 'MARK', 'RAFA'], o resultado de nos[::-1] será:

['RAFA', 'MARK', 'JULIA']

### 4. Concatenação da lista invertida:

A função '->'.join(nos_invertidos) é usada para juntar os elementos da lista invertida de volta em uma string, com '->' entre os elementos.
O método join() faz essa concatenação de forma simples e eficiente.

Exemplo:
A lista ['RAFA', 'MARK', 'JULIA'] será convertida para a string:

RAFA->MARK->JULIA

### 5. Saída:

Por fim, a string resultante é impressa usando o comando print(). O valor final é a sequência de nós invertida no formato esperado.

Exemplo:
Se a entrada foi JULIA->MARK->RAFA, a saída será:

RAFA->MARK->JULIA

Exemplos de Entrada e Saída:

Exemplo 1:
Entrada: JULIA->MARK->RAFA
Saída: RAFA->MARK->JULIA

Exemplo 2:
Entrada: X5->N2
Saída: N2->X5

Exemplo 3:
Entrada: USUARIO1
Saída: USUARIO1
