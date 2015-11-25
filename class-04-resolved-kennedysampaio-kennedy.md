# MongoDB - Aula 04 - Exercício
autor: Kennedy Sampaio

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
> var query = {name: /Bulbassauro/i}
> var mod = {$pushAll: {moves: ['pancadas de fúria', 'Aperto Protetor']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query)
{ "_id" : ObjectId("5647d0387b3985d25c9230c8"), "name" : "Bulbassauro", "descrip
tion" : "Chicote de trepadeira", "type" : "grama", "attack" : [ "investida", "ch
oque do trovão" ], "height" : 0.4, "moves" : [ "Choque do trovão", "pancadas de
fúria", "Aperto Protetor" ], "active" : false }

> var query = {name: /squirtle/i}
> var mod = {$pushAll: {moves: 'Placa de neom', 'Lamber para longe']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query)
{ "_id" : ObjectId("5647d0387b3985d25c9230ca"), "name" : "Squirtle", "descrip
tion" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : [ "investida", "hidro bomba" ],
"height" : 0.5, "attack: false, "active" : false "moves" : [ 'Placa de neom', 'Lamber para longe' ] }

> var query = {name: /charmander/i}
> var mod = {$pushAll: {moves: ['Bola elétrica', 'Ataque rápido']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query)
{ "_id" : ObjectId("5647d0387b3985d25c9230c9"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "
investida" ], "height" : 0.6, "active" : false, "moves" : [ "Bola elétrica", "At
aque rápido" ] }

> var query = {name: /pikachu/i}
> var mod = {$pushAll: {moves: ['Bola elétrica', 'Choque elétrico']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query)
{ "_id" : ObjectId("56476fd27b3985d25c9230c3"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" :
0.4, "defense" : 35, "moves" : [ "Bola elétrica", "Choque elétrico" ] }
{ "_id" : ObjectId("5651fcc1a302511cbfdf46ca"), "name" : "Pikachu", "description
" : "amarelinho fofinho", "type" : "Elétrico", "attack" : 90, "active" : false,
"height" : 0.5 }


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

> var query = {}
> var mod = {$push: {movies: 'Investida'}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 6, "nUpserted" : 0, "nModified" : 6 })
> db.pokemons.find(query)
{ "_id" : ObjectId("56476fd27b3985d25c9230c3"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" :
0.4, "defense" : 35, "moves" : [ "Bola elétrica", "Choque elétrico" ], "movies"
: [ "Investida" ] }
{ "_id" : ObjectId("564770ff7b3985d25c9230c4"), "name" : "Bulbassauro", "descrip
tion" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4
, "movies" : [ "Investida" ] }
{ "_id" : ObjectId("564770ff7b3985d25c9230c5"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52,
 "height" : 0.6, "movies" : [ "Investida" ] }
{ "_id" : ObjectId("564770ff7b3985d25c9230c6"), "name" : "Squirtle", "descriptio
n" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "heig
ht" : 0.5, "movies" : [ "Investida" ] }
{ "_id" : ObjectId("5647723e7b3985d25c9230c7"), "name" : "Caterpie", "descriptio
n" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "movies
" : [ "Investida" ] }
{ "_id" : ObjectId("5651fcc1a302511cbfdf46ca"), "name" : "Pikachu", "description
" : "amarelinho fofinho", "type" : "Elétrico", "attack" : 90, "active" : false,
"height" : 0.5, "movies" : [ "Investida" ] }

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

> var query = {name: /AindaNaoExitMon/i}
> var mod = {$setOnInsert: 
{name: 'AindaNaoExitMon', type: null, attack: null, 
defense: null, height: null, description: 'Sem maiores informações'}}
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 0 })
> db.pokemons.find(query)
{ "_id" : ObjectId("565200dba78977a49f35b6e5"), "name" : "AindaNaoExitMon", "des
cription" : "Sem maiores informações", "type" : null, "attack" : null, "active"
: null, "height" : null }

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

> var query = {moves: {$in: [/investida/i, /esfera elétrica/i]}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564770ff7b3985d25c9230c4"), "name" : "Bulbassauro", "descrip
tion" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4
, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("564770ff7b3985d25c9230c5"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52,
 "height" : 0.6, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("5647723e7b3985d25c9230c7"), "name" : "Caterpie", "descriptio
n" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "movies
" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("5651fcc1a302511cbfdf46ca"), "name" : "Pikachu", "description
" : "amarelinho fofinho", "type" : "Elétrico", "attack" : 90, "active" : false,
"height" : 0.5, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("56476fd27b3985d25c9230c3"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" :
0.4, "defense" : 35, "moves" : [ "Bola elétrica", "Choque elétrico", "Investida"
 ], "movies" : [ "Investida" ] }

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

> var query = {moves: {$all: [/investida/i , /Bola elétrica/i]}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56476fd27b3985d25c9230c3"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" :
0.4, "defense" : 35, "moves" : [ "Bola elétrica", "Choque elétrico", "Investida"
 ], "movies" : [ "Investida" ] }

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

> var query = {type: {$not: /elétrico/i}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564770ff7b3985d25c9230c4"), "name" : "Bulbassauro", "descrip
tion" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4
, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("564770ff7b3985d25c9230c5"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52,
 "height" : 0.6, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("564770ff7b3985d25c9230c6"), "name" : "Squirtle", "descriptio
n" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "heig
ht" : 0.5, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("5647723e7b3985d25c9230c7"), "name" : "Caterpie", "descriptio
n" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "movies
" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("56476fd27b3985d25c9230c3"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" :
0.4, "defense" : 35, "moves" : [ "Bola elétrica", "Choque elétrico", "Investida"
 ], "movies" : [ "Investida" ] }
{ "_id" : ObjectId("565200dba78977a49f35b6e5"), "name" : "AindaNaoExitMon", "des
cription" : "Sem maiores informações", "type" : null, "attack" : null, "active"
: null, "height" : null }

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

> var query = {$and: [{moves: {$in: ['Investida']}}, {attack: {$not: {$lte: 49}}
}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564770ff7b3985d25c9230c5"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52,
 "height" : 0.6, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("5651fcc1a302511cbfdf46ca"), "name" : "Pikachu", "description
" : "amarelinho fofinho", "type" : "Elétrico", "attack" : 90, "active" : false,
"height" : 0.5, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
{ "_id" : ObjectId("56476fd27b3985d25c9230c3"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" :
0.4, "defense" : 35, "moves" : [ "Bola elétrica", "Choque elétrico", "Investida"
 ], "movies" : [ "Investida" ] }


## Remova **todos** os pokemons do tipo água e com attack menor que 50.

> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564770ff7b3985d25c9230c6"), "name" : "Squirtle", "descriptio
n" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "heig
ht" : 0.5, "movies" : [ "Investida" ], "moves" : [ "Investida" ] }
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })
> db.pokemons.find(query)
>
