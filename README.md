# neo4j-movie-example

1. Download & unzip Neo4j 2.1.8 ([Linux version](https://neo4j.com/artifact.php?name=neo4j-community-2.1.8-unix.tar.gz)).
1. Download [Neo4j Shell Tools 2.1](http://dist.neo4j.org/jexp/shell/neo4j-shell-tools_2.1.zip) ([GitHub repository](https://github.com/jexp/neo4j-shell-tools/tree/2.1)) and unzip the JAR files to Neo4j's `lib` directory.
1. Start Neo4j Shell Tools with `bin/neo4j-shell`

## Steps to reproduce the GraphML file

1. Download & unzip the [Neo4j 2.1.6 movie database set](http://example-data.neo4j.org/files/cineasts_12k_movies_50k_actors_2.1.6.zip) from the [Neo4j Developer Pages](https://neo4j.com/developer/movie-database/), rename the directory to `graph.db` and movie it Neo4j's `data/databases` directory.
1. Start Neo4j with `bin/neo4j start`
1. Run the shell with `bin/neo4j-shell -path data/databases/graph.db/`
1. Export the GraphML file with `export-graphml -o movie-database.graphml -t`

## Steps to import the GraphML file

The vanilla `bin/shell` command only works with Neo4j 3.0.x. To obtain it, start in the [other releases](https://neo4j.com/download/other-releases/) page and do some URL hacking to get 3.0.6. Get the [shell-tools 3.0.1 zip](http://dist.neo4j.org/jexp/shell/neo4j-shell-tools_3.0.1.zip) and unzip it to the `lib` directory.

1. Start Neo4j with `bin/neo4j start`
1. Make sure that the `data/databases/graph.db` directory does not exists.
1. Run the shell with `bin/neo4j-shell`
  * If you have Neo4j 3.1.x+. It will throw a "connection refused" error. To work around this, use `bin/neo4j-shell -path data/databases/graph.db`
1. Import with `import-graphml -i "movie-database.graphml" -t`
