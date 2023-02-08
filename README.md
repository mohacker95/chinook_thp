a) Niveau facile

Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
 reponse 
 max = Album.count

Qui est l'auteur de la chanson "White Room" ?
 reponse
 auteur= Track.find_by(title:'White Room').artist
 

Quelle chanson dure exactement 188133 milliseconds ?
reponse 
Track.find_by(duration:188133).title


Quel groupe a sorti l'album "Use Your Illusion II" ?
reponse 
Album.find_by(title: 'Use Your Illusion II').artist

---------------------------------------------------------------------------------------------------------

b) Niveau Moyen

Combien y a t'il d'albums dont le titre contient "Great" ? 
reponse 
Album.where("title like ?", "%great%").count


Supprime tous les albums dont le nom contient "music"
reponse 
Album.where("title like?", "%music%").destroy_all


Combien y a t'il d'albums écrits par AC/DC ?
reponse 
Album.where("artist like?", "%AC/DC%").count

Combien de chanson durent exactement 158589 millisecondes ?
reponse 
Track.where("duration like?","%158589%").count
-------------------------------------------------------------------------------------------------------
c) Niveau Difficile

puts en console tous les titres de AC/DC.
reponse
Album.where(artist:"AC/DC").each do|album|puts album.title end

puts en console tous les titres de l'album "Let There Be Rock".
reponse
Track.where(album:"Let There Be Rock").each do |track|puts track.title end 

Calcule le prix total de cet album ainsi que sa durée totale.
reponse 
Track.where(album:"Let There Be Rock").sum(:price)
Track.where(album:"Let There Be Rock").sum(:duration)

Calcule le coût de l'intégralité de la discographie de "Deep Purple".
reponse
Track.where(artist:"Deep Purple").sum(:price)

Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
reponse
Track.where(artist:"Eric Clapton").each do |track|track.update(artist:"Britney Spears")end 
