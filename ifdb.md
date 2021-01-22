## mongoimport -d imdb -c imdb_movies --type json --file movies.json –jsonArray C:\Users\Youcode\Desktop\movies.json
## db.films.find({"year":{$eq:2010}}).pretty();

db.films.find({"year":{$eq:2009}}).count(); => 229

db.films.find({year:2008},{_id:-1,cast:-1,genres:-1}).pretty();

db.films.find({title:{$regex:/^A/}}).pretty();

db.films.find({cast:"Timothy Gibbs",year:2011}).pretty()

db.films.find({genres:"Thriller",year:2011}).pretty()

db.films.find({genres:"Thriller",year:2016}).sort({title:-1}).pretty()

`` db.films.bulkWrite(
]
  {  insertOne : 
     {
         "document" :  { 
             "title" : "benj testa",
             "year" : "2020", 
             "cast" : [
                         "Tom Schiling" , 
                         "Elyas M’Barek",
                     ], 
             "genres" : [
                         "Crime",
                         "Drama"
                     ]
         }
     }
 },

 {  insertOne : 
     {
         "document" :  { 
             "title" : "belg ben",
             "year" : "2020", 
             "cast" : [
                         "Tom Schiling" , 
                         "Elyas M’Barek",
                     ], 
             "genres" : [
                         "Crime",
                         "Drama"
                     ]
         }
     }
 },
]
);
``

db.films.deleteMany({year:{$lt:2000}})

db.films.updateMany({}, {$set: {"rating": []}})

db.films.updateMany({_id:ObjectId("60084a39dd80d2427818b6df"),_id:ObjectId("60084a39dd80d2427818b6dd")}, {$set: {rating:[ { by: "moi", rating: 4 }, {by:"collaborateur", rating: 5} ]}})

db.films.updateMany({}, {$set: {"ar":""}})

db.films.updateMany({},{$rename:{"ar":"averageRating"}})
15.db.films.updateOne({_id:ObjectId("600a9bdc486faa09846928f8")}, {$set: {"views": [12344]}});/
db.films.updateOne({_id:ObjectId("600a9bdc486faa09846928f9")}, {$set: {"views": [111222]}});
16.db.films.updateMany({_id:ObjectId("600a9bdc486faa09846928f8"),_id:ObjectId("600a9bdc486faa09846928f9")},{$set:{"views": "[a,b,c]"}});
