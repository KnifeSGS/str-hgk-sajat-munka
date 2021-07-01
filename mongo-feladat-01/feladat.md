1. Készíts egy videoStore nevű MongoDB adatbázist!
2. Hozz létre benne egy movies listát!

use videoStore

3. Ments el benne 10 új filmet (save()) a következő mezőkkel:

db.movies.save({title: "Schindler listája", category: "háborús", director: "Steven Spielberg"} )
db.movies.save({title: "A cápa", category: "horror", director: "Steven Spielberg"} )
db.movies.save({title: "Az elveszett frigyláda fosztogatói", category: "akció", director: "Steven Spielberg"} )
db.movies.save({title: "Jurassic Park", category: "kaland", director: "Steven Spielberg"} )
db.movies.save({title: "Avatar", category: "sci-fi", director: "James Cameron"} )
db.movies.save({title: "Titanic", category: "romantikus", director: "James Cameron"} )
db.movies.save({title: "Terminátor", category: "sci-fi", director: "James Cameron"} )
db.movies.save({title: "Levelek Ivo Dzsimáról", category: "filmdráma", director: "Clint Eastwood"} )
db.movies.save({title: "Millió dolláros bébi", category: "filmdráma", director: "Clint Eastwood"} )
db.movies.save({title: "Űrcowboyok", category: "vígjáték", director: "Clint Eastwood"} )

4. Frissítsd a listádat (updateMany), mindenki kapjon egy „ratings” mezőt, amely egy üres listát tartalmaz (1-5 ig lehet benne tárolni a szavazatokat)!

db.movies.updateMany({}, {$set: {ratings: []}} )

5. Adj 3 különböző filmre legalább 2 különböző szavazatot (használd a $push operátort)!

db.movies.updateOne({title: "Schindler listája"}, {$push: {rating: 5}})
db.movies.updateOne({title: "A cápa"}, {$push: {rating: 3}})
db.movies.updateOne({title: "Avatar"}, {$push: {rating: 4}})

6. Adj hozzá minden filmhez egy „releaseYear” (megjelenés éve) mezőt: kezdetnek állíts be egy tetszőleges évet minden filmnek (pl.: 2000)!

db.movies.updateMany({}, {$set: {releaseYear: 2000}} )

7. Írd át category típusonként csupa nagybetűre a kategóriákat (pl.: action ==> ACTION legyen mindenhol). Használd az updateMany parancsot!

db.movies.updateMany({}, [{$set: {category: {$toUpper: "$category"}}}] )