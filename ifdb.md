   ## Importer le fichier json ci-joint dans votre base de données.
``` 1) mongoimport -d imdb -c imdb_movies --type json --file movies.json –jsonArray C:\Users\Youcode\Desktop\movies.json ``` 
   ## Afficher les films de l’année 2010
``` 2) db.films.find({"year":{$eq:2010}}).pretty(); ``` 
   ## Combien de film a été réalisé en 2009.
``` 3) db.films.find({"year":{$eq:2009}}).count(); => 229 ``` 
   ## Faites une requête pour récupérer des documents des films réalisés en 2008 en excluant les champs : _id, cast, genres.
``` 4) db.films.find({year:2008},{_id:-1,cast:-1,genres:-1}).pretty(); ``` 
   ## Afficher tous les films commençant par la lettre A.
``` 5) db.films.find({title:{$regex:/^A/}}).pretty(); ``` 
   ## Afficher les films où ‘Timothy Gibbs’ a joué en 2011
``` 6) db.films.find({cast:"Timothy Gibbs",year:2011}).pretty() ``` 
   ## Afficher les films de type ‘Thriller’ en 2011
``` 7) db.films.find({genres:"Thriller",year:2011}).pretty() ``` 
   ## Afficher les films de type ‘Thriller’ réalisés en 2016 par ordre alphabétique inverse de leurs ‘title’
``` 8) db.films.find({genres:"Thriller",year:2016}).sort({title:-1}).pretty() ``` 
   ## Insérer deux film de votre choix dans la base en utilisant un BulkWrite ( pour le champs ‘year’, il doit être 2020)
``` 
9) db.films.bulkWrite(]
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
  ## Supprimer tous les films réalisés avant 2000
```  10) db.films.deleteMany({year:{$lt:2000}}) ``` 
 ## Ajouter un champs rating qui sera de type array d’objets pour tous les documents
```  11) db.films.updateMany({}, {$set: {"rating": []}}) ``` 
 ## Faites vous et un collaborateur, les ratings (le rating est sur 5) de deux films de votre choix, comme suit : ratings: [ { by: "moi", rating: 4 }, {by:"collaborateur”, rating: 5} ]
```  12) db.films.updateMany({_id:ObjectId("60084a39dd80d2427818b6df"),_id:ObjectId("60084a39dd80d2427818b6dd")}, {$set: {rating:[ { by: "moi", rating: 4 }, {by:"collaborateur", rating: 5} ]}}) ``` 
 ## Créer un champ qui sera la moyenne de tous les ratings est appelé le : ar
``` 13) db.films.updateMany({}, {$set: {"ar":""}}) ``` 
 ## Renommer le champ créer précédémment à savoir : ar, pour devenir averageRating.
``` 14) db.films.updateMany({},{$rename:{"ar":"averageRating"}}) ``` 
 ## Créer un champs views qui sera un array qui contiendra des valeurs comme ci-après : ‘views ‘:[123444, 66855,78966]
``` 15) .db.films.updateOne({_id:ObjectId("600a9bdc486faa09846928f8")}, {$set: {"views": [12344]}}); ```
       ```  db.films.updateOne({_id:ObjectId("600a9bdc486faa09846928f9")}, {$set: {"views": [111222]}}); ``` 
 ## Faites une mise à jour des films que vous avez insérer en renseignant les valeurs pour le tableau views.
``` 16) db.films.updateMany({_id:ObjectId("600a9bdc486faa09846928f8"),_id:ObjectId("600a9bdc486faa09846928f9")},{$set:{"views": "[a,b,c]"}}); ``` 
