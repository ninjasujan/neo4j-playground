# neo4j-playground

neo4j is agraph database, helpful to represent complex relaionship between nodes.

Cypher is Neo4j's graph query language that lets you retrieve data from the graph.

**Create Node**

```
CREATE(sujan:STUDENT {name: "sujan", DOB: "1999-03-19", course: "MCA", GPA: 9})

CREATE(college:COLLEGE {name: "MIT", location: "udipi", university: "MAHE"})

CREATE(college:COLLEGE {name: "MIT", location: "udipi", university: "MAHE"})
```

**Create relationship**

```
MATCH (sujan:STUDENT {name: "sujan"})
MATCH (vinayaka:STUDENT {name: "vinayaka"})
CREATE (sujan)-[class_mate:CLASS_MATE]->(vinayaka)
```

```
MATCH (sujan:STUDENT {name: "sujan"})
MATCH (col:COLLEGE {name: "MIT"})
CREATE (sujan)-[studies_in:STUDIES]->(col)
```

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

**Delete Node by ID**

```
MATCH (p:COLLEGE) where ID(p) IN [33]
OPTIONAL MATCH (p)-[r]-()
DELETE r,p
```

**Query on relationship**

```
MATCH (player:PLAYER) -[:PLAYS_FOR]-> (team:TEAM)
WHERE team.name = "LA Lakers"
RETURN player, team;
```

**Return all student who enrolled for secific course**

```
MATCH (stud:STUDENT) -[:ENROLLED]-> (course:COURSE)
WHERE course.name = "Bio Tech"
RETURN stud;
```

**Return all student who studying in college MIT**

```
MATCH (stud:STUDENT) -[:STUDIES]-> (college:COLLEGE {name: "MIT"})
RETURN stud, college;
```

**Attribute query on relationship**

```
MATCH (player:PLAYER) -[contract:PLAYS_FOR]-> (team:TEAM)
WHERE contract.salary > 4000000
RETURN player, team;
```

**Retriew salary of all teammates**

```
MATCH (lebron:PLAYER {name: "LeBron James"}) -[team:TEAMMATES]-> (players:PLAYER)
MATCH (players) -[contract:PLAYS_FOR]-> (teamM:TEAM)
WHERE contract.salary >=4000000
RETURN players;
```

### Graph Database Modeling.

Hyperedge -
