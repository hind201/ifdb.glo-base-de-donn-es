``` 1) mongoimport -d imdb -c imdb_movies --type json --file movies.json –jsonArray C:\Users\Youcode\Desktop\movies.json ``` 
``` 2) db.films.find({"year":{$eq:2010}}).pretty(); ``` 

``` 3) db.films.find({"year":{$eq:2009}}).count(); => 229 ``` 

``` 4) db.films.find({year:2008},{_id:-1,cast:-1,genres:-1}).pretty(); ``` 

``` 5) db.films.find({title:{$regex:/^A/}}).pretty(); ``` 

``` 6) db.films.find({cast:"Timothy Gibbs",year:2011}).pretty() ``` 

``` 7) db.films.find({genres:"Thriller",year:2011}).pretty() ``` 

``` 8) db.films.find({genres:"Thriller",year:2016}).sort({title:-1}).pretty() ``` 

``` 9) db.films.bulkWrite(
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
``` 

```  10) db.films.deleteMany({year:{$lt:2000}}) ``` 

```  11) db.films.updateMany({}, {$set: {"rating": []}}) ``` 

```  12) db.films.updateMany({_id:ObjectId("60084a39dd80d2427818b6df"),_id:ObjectId("60084a39dd80d2427818b6dd")}, {$set: {rating:[ { by: "moi", rating: 4 }, {by:"collaborateur", rating: 5} ]}}) ``` 

``` 13) db.films.updateMany({}, {$set: {"ar":""}}) ``` 

``` 14) db.films.updateMany({},{$rename:{"ar":"averageRating"}}) ``` 
``` 15) .db.films.updateOne({_id:ObjectId("600a9bdc486faa09846928f8")}, {$set: {"views": [12344]}});/ 
db.films.updateOne({_id:ObjectId("600a9bdc486faa09846928f9")}, {$set: {"views": [111222]}}); ``` 
``` 16) db.films.updateMany({_id:ObjectId("600a9bdc486faa09846928f8"),_id:ObjectId("600a9bdc486faa09846928f9")},{$set:{"views": "[a,b,c]"}}); ``` 
