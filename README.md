# neo4j-playground

neo4j is agraph database, helpful to represent complex relaionship between nodes.

Cypher is Neo4j's graph query language that lets you retrieve data from the graph

**Return all Node**

```
Match (n) return n
```

**Return all team node**

```
MATCH (n:TEAM) RETURN n
```

**Return all player name**

```
MATCH (n:PLAYER) RETURN n.name

```

**Return player by specific name**

```
MATCH (player:PLAYER)
WHERE player.name = "LeBron James"
RETURN n
```

**Relational operator**

```
MATCH (player:PLAYER)
WHERE player.height >=2 RETURN player
```

**Pagination**

```
MATCH (player:PLAYER)
WHERE player.height >=2 RETURN player
SKIP 0
LIMIT 5
```

**Sort order**

```
MATCH (player:PLAYER)
WHERE player.height >=2 RETURN player
ORDER BY player.height DESC
```

**Match multi node filter**

```
MATCH (player:PLAYER), (coach:COACH)
RETURN player, coach
```
