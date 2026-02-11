# Desafio
Em um laboratório futurista, cientistas utilizam um banco de dados Neo4J para armazenar conexões entre conceitos extraídos por uma inteligência artificial generativa. Cada conceito é representado como uma string de palavras separadas por vírgula, formando um vetor de palavras não estruturadas. Para treinar o mecanismo de busca semântica, é necessário calcular o grau de similaridade entre dois desses vetores, baseando-se no número de elementos comuns.

Sua tarefa é: dado dois vetores de palavras (cada um representado por uma string de palavras separadas por vírgula), encontre quantas palavras aparecem em ambos. A ordem das palavras não importa, e cada palavra deve ser considerada apenas uma vez, independentemente de quantas vezes apareça em um vetor.

# Entrada
A entrada consiste de duas linhas. Cada linha contém uma string com várias palavras (sem espaços), separadas apenas por vírgula, representando os dois vetores. Todas as palavras são formadas por letras minúsculas, sem espaços ou outros separadores.

# Saída
Imprima um único número inteiro indicando quantas palavras aparecem em ambos os vetores.

# Exemplos

A tabela abaixo apresenta exemplos de entrada e saída:

| **Entrada**                      | **Saída**             |
|-----------------------------------|-----------------------|
| node,ai,graph,vector              |                       |
| graph,neo4j,vector,llm            | 2                     |
| embedding,gpt,cypher              |                       |
| vector,graph,database             | 0                     |
| data,model,neo,genai              |                       |
| genai,data,ai,neo                 | 3                     |

---
## Modelo base:
```python
# Leitura das duas linhas de entrada, separadas por vírgulas
linha1 = input().strip()
linha2 = input().strip()

# Criação dos conjuntos (remove duplicatas automaticamente)
conjunto1 = set(linha1.split(','))
conjunto2 = set(linha2.split(','))

# TODO: Calcule quantas palavras estão em ambos os conjuntos
# Dica: use a interseção entre conjuntos

# Saída: quantidade de palavras em comum
# print(qtd_comum)
```

---
# Resolução do Problema: 
## Vetores no Grafo Generativo

Vamos resolver esse desafio calculando a **interseção** entre dois conjuntos de palavras. A interseção entre dois conjuntos nos dará as palavras que aparecem em ambos os vetores de palavras, e podemos contar quantas palavras são compartilhadas.

## Estratégia:

1. **Entrada**: Recebemos duas linhas de palavras separadas por vírgula. Cada linha é um vetor.
2. **Conversão para conjuntos**: Usaremos conjuntos para eliminar duplicatas automaticamente e para realizar a operação de interseção.
3. **Interseção**: A interseção de dois conjuntos nos dará as palavras comuns.
4. **Contagem**: O tamanho da interseção nos dará o número de palavras em comum.

## Código:

```python
# Leitura das duas linhas de entrada, separadas por vírgulas
linha1 = input().strip()
linha2 = input().strip()

# Criação dos conjuntos (remove duplicatas automaticamente)
conjunto1 = set(linha1.split(','))
conjunto2 = set(linha2.split(','))

# Calculando a interseção dos conjuntos (palavras comuns)
comum = conjunto1.intersection(conjunto2)

# Saída: quantidade de palavras em comum
print(len(comum))
```

### Explicação:

1. **Leitura da entrada**:
   * `linha1 = input().strip()` e `linha2 = input().strip()` leem as duas linhas de entrada, que contêm as palavras separadas por vírgula.

2. **Conversão para conjuntos**:
   * `conjunto1 = set(linha1.split(','))` converte a primeira linha em um conjunto de palavras, separando-as pela vírgula. Isso remove automaticamente quaisquer duplicatas.
   * O mesmo é feito para `linha2`.

3. **Interseção de conjuntos**:
   * A operação `conjunto1.intersection(conjunto2)` retorna um novo conjunto contendo as palavras que aparecem em ambos os conjuntos. Se uma palavra aparecer nas duas listas de entrada, ela estará na interseção.

4. **Resultado**:
   * A função `len(comum)` calcula o tamanho da interseção, ou seja, o número de palavras comuns entre os dois vetores.
   * O valor é impresso como a resposta.

### Exemplos de entrada e saída:
#### Exemplo 1:
**Entrada**:
```
node,ai,graph,vector
graph,neo4j,vector,llm
```
**Saída**:
```
2
```
#### Exemplo 2:
**Entrada**:
```
embedding,gpt,cypher
vector,graph,database
```
**Saída**:
```
0
```
#### Exemplo 3:
**Entrada**:
```
data,model,neo,genai
genai,data,ai,neo
```
**Saída**:
```
3
```

### Considerações:
* Usar conjuntos facilita o cálculo da interseção de maneira eficiente.
* A função `split(',')` converte a string de palavras separadas por vírgula em uma lista, e o `set()` remove quaisquer duplicatas dessa lista automaticamente.
* A operação de interseção é realizada de maneira eficiente e de fácil compreensão com a função `intersection()`.
