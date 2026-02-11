# Desafio
Na cidade digital de Neopolis, cientistas utilizam o Neo4J para conectar memórias não estruturadas armazenadas em grandes bancos de vetores. As memórias, que vieram de sessões antigas de GenAI, são salvas em uma longa sequência de palavras. Quando é preciso buscar informações, a IA de Neopolis precisa identificar quais palavras aparecem mais de uma vez nessas memórias — são os chamados “vetores-chave”.

Sua missão é ajudar a IA a identificar rapidamente as palavras que aparecem múltiplas vezes na sequência recebida. Escreva um programa que receba uma única linha contendo várias palavras separadas por espaço, e retorne uma string com todas as palavras repetidas na ordem em que aparecem pela primeira vez repetidas. Se nenhuma palavra se repetir, exiba apenas “NENHUMA”.

# Entrada
Uma única linha com diversas palavras separadas por espaço, representando os fragmentos de memórias armazenados.

# Saída
Uma única linha com cada palavra repetida uma única vez, separadas por espaço, na ordem em que aparecem, ou “NENHUMA” caso nenhuma palavra se repita.



# Exemplos

A tabela abaixo apresenta exemplos de entrada e saída:

| **Entrada**                      | **Saída**             |
|-----------------------------------|-----------------------|
| astro dados mapa astro codigo dados | astro dados           |
| net grafo vetor net vetor grafo net | net vetor grafo       |
| genai banco registro memoria      | NENHUMA               |

---
## Modelo base:

```python
# Entrada: uma linha contendo palavras separadas por espaço.
palavras = input().strip().split()

# Lista que vai guardar as palavras repetidas (sem duplicar).
saida = []

for palavra in palavras:
    # TODO: se a palavra aparece mais de uma vez e ainda não está em saida, adicione-a.
    pass  # Dica: use "palavras.count(palavra) > 1" e verifique se não está em saida com "not in".

# Saída das palavras repetidas na ordem da primeira aparição.
if saida:
    print(' '.join(saida))
else:
    print("NENHUMA")
```
---
# Resolução do Problema: 
## Vetores Da Memoria Digital

Esse desafio é interessante, pois precisa de uma solução eficiente para identificar palavras repetidas em uma sequência de palavras e garantir que o formato da saída esteja correto. Vamos completar o código usando a estrutura fornecida, adicionando as verificações necessárias para identificar as palavras que aparecem mais de uma vez.

Estratégia:
Contagem das palavras: Usaremos a função count() para verificar quantas vezes cada palavra aparece.

Armazenamento sem duplicação: Para evitar duplicar palavras na saída, usaremos uma lista (saida) que armazena as palavras na ordem em que aparecem pela primeira vez como repetidas.

Código:
```python
# Entrada: uma linha contendo palavras separadas por espaço.
palavras = input().strip().split()

# Lista que vai guardar as palavras repetidas (sem duplicar).
saida = []

# Itera sobre as palavras na sequência
for palavra in palavras:
    # Se a palavra aparece mais de uma vez e ainda não está em 'saida', adiciona ela.
    if palavras.count(palavra) > 1 and palavra not in saida:
        saida.append(palavra)

# Saída das palavras repetidas na ordem da primeira aparição.
if saida:
    print(' '.join(saida))
else:
    print("NENHUMA")
```
---

# Explicação do Código:

## 1. **Leitura da entrada**:

   * `palavras = input().strip().split()` lê a linha de entrada, remove espaços extras no início e no fim, e depois divide a linha em uma lista de palavras usando o espaço como separador.

## 2. **Lista `saida`**:

   * A lista `saida` é inicializada vazia e será usada para armazenar as palavras que aparecem mais de uma vez, mas **sem duplicação** na saída.

## 3. **Iteração sobre as palavras**:

   * O laço `for palavra in palavras:` percorre cada palavra na lista `palavras`.
   * Dentro do loop, a expressão `palavras.count(palavra)` conta quantas vezes a palavra aparece na lista.
   * Se a palavra aparece **mais de uma vez** e ainda não foi adicionada à lista `saida` (`palavra not in saida`), ela é adicionada à lista `saida`.

## 4. **Saída**:

   * Se houver palavras repetidas, a linha `print(' '.join(saida))` imprime as palavras repetidas, separadas por espaço.
   * Caso contrário, se não houver nenhuma palavra repetida, a linha `print("NENHUMA")` é executada.

### Exemplos de entrada e saída:

#### Exemplo 1:
**Entrada**:
```
astro dados mapa astro codigo dados
```
**Saída**:
```
astro dados
```
#### Exemplo 2:
**Entrada**:
```
net grafo vetor net vetor grafo net
```
**Saída**:
```
net vetor grafo
```
#### Exemplo 3:
**Entrada**:
```
genai banco registro memoria
```

**Saída**:
```
NENHUMA
```

## Considerações:

* A função `count()` tem complexidade **O(n)**, onde `n` é o número de palavras na lista. Isso significa que, para cada palavra, o código percorre toda a lista para contar suas ocorrências, o que pode não ser o método mais eficiente para listas muito grandes.
* No entanto, para entradas de tamanho razoável, esse método é simples e eficaz.

