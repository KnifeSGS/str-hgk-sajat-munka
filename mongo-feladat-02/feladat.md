>1. Készíts el egy „directors” listát, amelyben filmrendezőket fogunk tárolni!
>2. Ments el benne 3 „rendező” dokumentumot az insertOne() parancs segítségével:

db.directors.insertOne({_id: 1, name: "Steven Spielberg", birthYear: 1946, movies: []})
db.directors.insertOne({_id: 3, name: "James Cameron", birthYear: 1954, movies: []})
db.directors.insertOne({_id: 2, name: "Clint Eastwood", birthYear: 1954, movies: []})

>3. Frissítsd a rendezők dokumentumait, helyezd el a „movies” listájukba a megfelelő filmek id-jait

function pushMovies(directorName){ 
  var movieIds = db.movies.find({director: directorName}, {_id:1}).toArray()
  for (i=0; i < movieIds.length; i++) { 
    db.directors.update({name: directorName}, {$push: {movies: movieIds[i]._id}}) }}

pushMovies("Steven Spielberg")
pushMovies("James Cameron")
pushMovies("Clint Eastwood")

>4. Ha frissítetted a rendezőket, ellenőrzés gyanánt kérdezd le a dokumentumokat a „directors” listából (használd a pretty() metódust a szebb megjelenítéshez)!

db.directors.find().pretty()

