# MongoDB - Aula 05 - Exercício
autor: Kennedy Sampaio

## 1. Importar as collections restaurantes e pokemons

C:\mongodb\bin>mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file C:\restaurantes.json
2015-12-03T23:55:30.611-0200    connected to: 127.0.0.1
2015-12-03T23:55:30.618-0200    dropping: be-mean.restaurantes
2015-12-03T23:55:33.545-0200    [##########..............] be-mean.restaurantes
5.2 MB/11.4 MB (45.5%)
2015-12-03T23:55:36.486-0200    [##########..............] be-mean.restaurantes
5.2 MB/11.4 MB (45.5%)
2015-12-03T23:55:39.486-0200    [##########..............] be-mean.restaurantes
5.2 MB/11.4 MB (45.5%)
2015-12-03T23:55:42.486-0200    [##########..............] be-mean.restaurantes
5.2 MB/11.4 MB (45.5%)
2015-12-03T23:55:45.486-0200    [##########..............] be-mean.restaurantes
5.2 MB/11.4 MB (45.5%)
2015-12-03T23:55:48.486-0200    [##########..............] be-mean.restaurantes
5.2 MB/11.4 MB (45.5%)
2015-12-03T23:55:51.486-0200    [##########..............] be-mean.restaurantes
5.2 MB/11.4 MB (45.5%)
2015-12-03T23:55:54.486-0200    [####################....] be-mean.restaurantes
9.8 MB/11.4 MB (86.2%)
2015-12-03T23:55:55.440-0200    imported 25359 documents

C:\mongodb\bin>mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file C:\pokemons.json
2015-12-05T00:06:40.356-0200    connected to: 127.0.0.1
2015-12-05T00:06:40.362-0200    dropping: be-mean.pokemons
2015-12-05T00:06:41.450-0200    imported 610 documents

## 2. Distinct por `cuisine` na collection restaurantes

>db.restaurantes.distinct('cuisine')
{
    "0" : "Bakery",
    "1" : "Hamburgers",
    "2" : "Irish",
    "3" : "American ",
    "4" : "Jewish/Kosher",
    "5" : "Delicatessen",
    "6" : "Ice Cream, Gelato, Yogurt, Ices",
    "7" : "Chinese",
    "8" : "Other",
    "9" : "Chicken",
    "10" : "Turkish",
    "11" : "Caribbean",
    "12" : "Donuts",
    "13" : "Sandwiches/Salads/Mixed Buffet",
    "14" : "Bagels/Pretzels",
    "15" : "Continental",
    "16" : "Pizza",
    "17" : "Italian",
    "18" : "Steak",
    "19" : "Polish",
    "20" : "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
    "21" : "German",
    "22" : "French",
    "23" : "Pizza/Italian",
    "24" : "Mexican",
    "25" : "Spanish",
    "26" : "Café/Coffee/Tea",
    "27" : "Tex-Mex",
    "28" : "Pancakes/Waffles",
    "29" : "Soul Food",
    "30" : "Seafood",
    "31" : "Hotdogs",
    "32" : "Greek",
    "33" : "Not Listed/Not Applicable",
    "34" : "African",
    "35" : "Japanese",
    "36" : "Indian",
    "37" : "Armenian",
    "38" : "Thai",
    "39" : "Chinese/Cuban",
    "40" : "Mediterranean",
    "41" : "Korean",
    "42" : "Bottled beverages, including water, sodas, juices, etc.",
    "43" : "Russian",
    "44" : "Eastern European",
    "45" : "Middle Eastern",
    "46" : "Asian",
    "47" : "Ethiopian",
    "48" : "Vegetarian",
    "49" : "Barbecue",
    "50" : "Egyptian",
    "51" : "English",
    "52" : "Sandwiches",
    "53" : "Portuguese",
    "54" : "Indonesian",
    "55" : "Chinese/Japanese",
    "56" : "Filipino",
    "57" : "Juice, Smoothies, Fruit Salads",
    "58" : "Brazilian",
    "59" : "Afghan",
    "60" : "Vietnamese/Cambodian/Malaysia",
    "61" : "CafÃ©/Coffee/Tea",
    "62" : "Soups & Sandwiches",
    "63" : "Tapas",
    "64" : "Moroccan",
    "65" : "Pakistani",
    "66" : "Peruvian",
    "67" : "Bangladeshi",
    "68" : "Czech",
    "69" : "Salads",
    "70" : "Creole",
    "71" : "Fruits/Vegetables",
    "72" : "Iranian",
    "73" : "Cajun",
    "74" : "Scandinavian",
    "75" : "Polynesian",
    "76" : "Soups",
    "77" : "Australian",
    "78" : "Hotdogs/Pretzels",
    "79" : "Southwestern",
    "80" : "Nuts/Confectionary",
    "81" : "Hawaiian",
    "82" : "Creole/Cajun",
    "83" : "Californian",
    "84" : "Chilean"
}


## 3. Distinct por `types` na pokemons

>db.pokemons.distinct('types')
{
    "0" : "fire",
    "1" : "normal",
    "2" : "water",
    "3" : "bug",
    "4" : "flying",
    "5" : "poison",
    "6" : "electric",
    "7" : "steel",
    "8" : "ice",
    "9" : "ghost",
    "10" : "fighting",
    "11" : "psychic",
    "12" : "grass",
    "13" : "ground",
    "14" : "fairy",
    "15" : "rock",
    "16" : "dark",
    "17" : "dragon"
}


## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

>db.pokemons.find().limit (3).skip(5 * 5)
/* 1 */
{
    "_id" : ObjectId("564b1daf25337263280d0492"),
    "attack" : 80.0000000000000000,
    "created" : "2013-11-03T15:05:41.402119",
    "defense" : 50.0000000000000000,
    "height" : "8",
    "hp" : 70.0000000000000000,
    "name" : "Machop",
    "speed" : 35.0000000000000000,
    "types" : [ 
        "fighting"
    ]
}

/* 2 */
{
    "_id" : ObjectId("564b1daf25337263280d0493"),
    "attack" : 100.0000000000000000,
    "created" : "2013-11-03T15:05:41.404294",
    "defense" : 70.0000000000000000,
    "height" : "15",
    "hp" : 80.0000000000000000,
    "name" : "Machoke",
    "speed" : 45.0000000000000000,
    "types" : [ 
        "fighting"
    ]
}

/* 3 */
{
    "_id" : ObjectId("564b1daf25337263280d0494"),
    "attack" : 130.0000000000000000,
    "created" : "2013-11-03T15:05:41.406521",
    "defense" : 80.0000000000000000,
    "height" : "16",
    "hp" : 90.0000000000000000,
    "name" : "Machamp",
    "speed" : 55.0000000000000000,
    "types" : [ 
        "fighting"
    ]
}

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

## 6. Realizar 3 counts na pokemons.

