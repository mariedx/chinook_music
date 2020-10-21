# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

-----------------------------
a) Niveau facile
Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
Album.count #347

Qui est l'auteur de la chanson "White Room" ?
Track.find_by(title: "White Room").artist #"Eric Clapton" 

Quelle chanson dure exactement 188133 milliseconds ?
Track.find_by(duration: 188133).title # "Perfect"

Quel groupe a sorti l'album "Use Your Illusion II" ?
Album.find_by(title: "Use Your Illusion II").artist #"Guns N Roses" 

-----------------------------
b) Niveau Moyen
Combien y a t'il d'albums dont le titre contient "Great" ? (indice)
Album.where("title like ?", "%Great%").count #13

Supprime tous les albums dont le nom contient "music".
Album.where("title like ?", "%music%").destroy_all #4 supprime

Combien y a t'il d'albums écrits par AC/DC ?
Album.where(artist: "AC/DC").count #2

Combien de chanson durent exactement 158589 millisecondes ?
Track.where(duration: 158589).count #0

-----------------------------
c) Niveau Difficile
Pour ces questions, tu vas devoir effectuer des boucles dans la console Rails. C'est peu commun mais c'est faisable, tout comme dans IRB.

puts en console tous les titres de AC/DC.
Track.where(artist: "AC/DC").map {|titre| puts titre.title} #marche aussi avec each! #18 songs
For Those About To Rock (We Salute You)
Put The Finger On You
Lets Get It Up
Inject The Venom
Snowballed
Evil Walks
C.O.D.
Breaking The Rules
Night Of The Long Knives
Spellbound
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie

puts en console tous les titres de l'album "Let There Be Rock".
Track.where(album: "Let There Be Rock").map {|titre| puts titre.title}
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie

Calcule le prix total de cet album ainsi que sa durée totale.
Track.where(album: "Let There Be Rock").sum(:price) #7.920000000000001
Track.where(album: "Let There Be Rock").sum(:duration) #2453259 


Calcule le coût de l'intégralité de la discographie de "Deep Purple".
Track.where(artist: "Deep Purple").sum(:price) #90.0899999999999 

Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
Track.where(artist: "Eric Clapton").each {|titre| titre.artist = "Britney Spears"} 