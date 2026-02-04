# Modelagem de Dados em Grafos de um Serviço de Streaming

Desafio New4J: Modelo de Grafo para Serviço de Filmes e Séries
1. Modelo de Grafo – Diagrama ou Esboço

O modelo de grafo proposto para o serviço inclui as seguintes entidades e conexões:

### Entidades (Nós)
User: Representa os usuários.
Movie: Representa filmes.
Serie: Representa séries.
Genre: Representa gêneros (ex: Ação, Comédia, Drama).
Actor: Representa atores.
Director: Representa diretores.
Relacionamentos (Conexões)

WATCHED: Relaciona um usuário a um filme ou série, com uma propriedade rating (nota de avaliação).
ACTED_IN: Relaciona um ator a um filme ou série.
DIRECTED: Relaciona um diretor a um filme ou série.
IN_GENRE: Relaciona um filme ou série a um gênero.

Esboço do Modelo de Grafo
(User) --[WATCHED {rating}]--> (Movie)
(User) --[WATCHED {rating}]--> (Serie)
(Movie) --[IN_GENRE]--> (Genre)
(Serie) --[IN_GENRE]--> (Genre)
(Actor) --[ACTED_IN]--> (Movie)
(Actor) --[ACTED_IN]--> (Serie)
(Director) --[DIRECTED]--> (Movie)
(Director) --[DIRECTED]--> (Serie)

### 2. Script Cypher
Criação de Constraints

O script abaixo cria as constraints para garantir a unicidade dos IDs dos nós no banco de dados:
// Criação de constraints para garantir unicidade
CREATE CONSTRAINT ON (u:User) ASSERT u.id IS UNIQUE;
CREATE CONSTRAINT ON (m:Movie) ASSERT m.id IS UNIQUE;
CREATE CONSTRAINT ON (s:Serie) ASSERT s.id IS UNIQUE;
CREATE CONSTRAINT ON (g:Genre) ASSERT g.name IS UNIQUE;
CREATE CONSTRAINT ON (a:Actor) ASSERT a.id IS UNIQUE;
CREATE CONSTRAINT ON (d:Director) ASSERT d.id IS UNIQUE;

### População do Grafo

O script abaixo popula o grafo com 3 usuários, 3 filmes/séries, 3 gêneros, 3 atores e 3 diretores. Para expandir para 15 registros por categoria, basta replicar as linhas conforme necessário.
// Criando usuários
CREATE (u1:User {id: 1, name: 'Alice'})
CREATE (u2:User {id: 2, name: 'Bob'})
CREATE (u3:User {id: 3, name: 'Charlie'})

// Criando filmes/séries
CREATE (m1:Movie {id: 1, title: 'Avengers: Endgame', year: 2019})
CREATE (m2:Movie {id: 2, title: 'The Matrix', year: 1999})
CREATE (s1:Serie {id: 3, title: 'Breaking Bad', year: 2008})

// Criando gêneros
CREATE (g1:Genre {name: 'Action'})
CREATE (g2:Genre {name: 'Sci-Fi'})
CREATE (g3:Genre {name: 'Drama'})

// Criando atores
CREATE (a1:Actor {id: 1, name: 'Robert Downey Jr.'})
CREATE (a2:Actor {id: 2, name: 'Keanu Reeves'})
CREATE (a3:Actor {id: 3, name: 'Bryan Cranston'})

// Criando diretores
CREATE (d1:Director {id: 1, name: 'Anthony Russo'})
CREATE (d2:Director {id: 2, name: 'Wachowski Sisters'})
CREATE (d3:Director {id: 3, name: 'Vince Gilligan'})

// Criando relacionamentos

// Users e Movies/Series
CREATE (u1)-[:WATCHED {rating: 5}]->(m1)
CREATE (u2)-[:WATCHED {rating: 4}]->(m2)
CREATE (u3)-[:WATCHED {rating: 5}]->(s1)

// Movie/Serie e Gênero
CREATE (m1)-[:IN_GENRE]->(g1)
CREATE (m2)-[:IN_GENRE]->(g2)
CREATE (s1)-[:IN_GENRE]->(g3)

// Actors e Movies/Series
CREATE (a1)-[:ACTED_IN]->(m1)
CREATE (a2)-[:ACTED_IN]->(m2)
CREATE (a3)-[:ACTED_IN]->(s1)

// Directors e Movies/Series
CREATE (d1)-[:DIRECTED]->(m1)
CREATE (d2)-[:DIRECTED]->(m2)
CREATE (d3)-[:DIRECTED]->(s1)
