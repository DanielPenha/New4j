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
