# Visualisation-v2.1.3
Version finale
<meta http-equiv='cache-control' content='no-cache'> 
<meta http-equiv='expires' content='0'> 
<meta http-equiv='pragma' content='no-cache'>

# Les meilleures audiences dans les salles de cinéma françaises
## *Cette présentation vise à montrer les scores d'audience réalisés par les 200 films les plus plébiscités dans les salles françaises, sur une période allant de 1945 à 2021*

**Sommaire**
- Avant-Propos
- I) Jeu de données utilisé
- II) Visualisations
  * A. Scatter plot des scores réalisés par les films les plus populaires au cinéma en France de 1945 à 2021
  * B. Pie charts présentant une répartition par année des plus gros succès et de leur chiffres au box office
  * C. Circle hierarchy - Vision globale des réalisateurs et des performances globales de leurs films
  * D. Le cinéma français à l'international avec Wikidata Query Service
- Conclusion

**Avant-Propos**

La France, tant au niveau de la production que de l'audience, est un des acteurs mondiaux les plus conséquents du marché du Cinéma :
> La France était en 2013 le deuxième exportateur de films au monde derrière les États-Unis et une étude réalisée en avril 2014 montre l'excellente image dont bénéficie le cinéma français à travers le monde, qui reste le cinéma le plus apprécié après le cinéma américain [...]
Avec 200 millions de billets vendus en 2012, et environ 213 millions attendus en 2015, la France est actuellement le troisième marché du cinéma mondial, que ce soit en termes d'entrées (derrière les États-Unis et l'Inde), ou en termes de revenus (derrière les États-Unis et le Japon). 
[<sub>Wikipédia</sub>](https://fr.wikipedia.org/wiki/Cin%C3%A9ma_fran%C3%A7ais#Audience_contemporaine)

Et pour cause, en 2020, 2041 salles de cinéma sont recensées sur l'ensemble du territoire français, comptabilisant un total de 6127 écrans, et 1 138 530 sièges[^1]. Bien que ces chiffres soient conséquents, il faut noter qu'ils sont en baisse considérable en comparaison des années précédentes, en raison de la crise sanitaire, comme il apparaît dans ces [tableaux](https://fr.wikipedia.org/wiki/Cin%C3%A9ma_fran%C3%A7ais#Exploitation) :

<table class="wikitable centre">
<caption>Exploitation cinématographique en France
</caption>
<tbody><tr>
<td>
</td>
<th scope="col"><a href="/wiki/2003_au_cin%C3%A9ma" title="2003 au cinéma">2003</a>
</th>
<th scope="col"><a href="/wiki/2004_au_cin%C3%A9ma" title="2004 au cinéma">2004</a>
</th>
<th scope="col"><a href="/wiki/2005_au_cin%C3%A9ma" title="2005 au cinéma">2005</a>
</th>
<th scope="col"><a href="/wiki/2006_au_cin%C3%A9ma" title="2006 au cinéma">2006</a>
</th>
<th scope="col"><a href="/wiki/2007_au_cin%C3%A9ma" title="2007 au cinéma">2007</a>
</th>
<th scope="col"><a href="/wiki/2008_au_cin%C3%A9ma" title="2008 au cinéma">2008</a>
</th>
<th scope="col"><a href="/wiki/2009_au_cin%C3%A9ma" title="2009 au cinéma">2009</a>
</th>
<th scope="col"><a href="/wiki/2010_au_cin%C3%A9ma" title="2010 au cinéma">2010</a>
</th>
<th scope="col"><a href="/wiki/2011_au_cin%C3%A9ma" title="2011 au cinéma">2011</a>
</th>
<th scope="col"><a href="/wiki/2012_au_cin%C3%A9ma" title="2012 au cinéma">2012</a>
</th></tr>
<tr>
<th scope="row">Nombre d'établissements
</th>
<td align="center">2&#160;130
</td>
<td align="center">2&#160;100
</td>
<td align="center">2&#160;076
</td>
<td align="center">2&#160;063
</td>
<td align="center">2&#160;054
</td>
<td align="center">2&#160;068
</td>
<td align="center">2&#160;065
</td>
<td align="center">2&#160;046
</td>
<td align="center">2&#160;032
</td>
<td align="center">2&#160;029
</td></tr>
<tr>
<th scope="row">Nombre de multiplexe (+8 salles)
</th>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">158
</td>
<td align="center">164
</td>
<td align="center">171
</td>
<td align="center">172
</td>
<td align="center">176
</td>
<td align="center">
</td></tr>
<tr>
<th scope="row">Nombre d'écrans actifs
</th>
<td align="center">5&#160;281
</td>
<td align="center">5&#160;276
</td>
<td align="center">5&#160;273
</td>
<td align="center">5&#160;283
</td>
<td align="center">5&#160;315
</td>
<td align="center">5&#160;389
</td>
<td align="center">5&#160;469
</td>
<td align="center">5&#160;464
</td>
<td align="center">5&#160;466
</td>
<td align="center">5&#160;502
</td></tr>
<tr>
<th scope="row">Nombre de fauteuils
</th>
<td align="center">1&#160;073&#160;000
</td>
<td align="center">1&#160;061&#160;669
</td>
<td align="center">1&#160;059&#160;264
</td>
<td align="center">1&#160;056&#160;868
</td>
<td align="center">1&#160;056&#160;072
</td>
<td align="center">1&#160;066&#160;593
</td>
<td align="center">1&#160;076&#160;984
</td>
<td align="center">1&#160;073&#160;681
</td>
<td align="center">1&#160;065&#160;803
</td>
<td align="center">1&#160;068&#160;903
</td></tr>
<tr>
<th scope="row">Nombre d'entrées (millions)
</th>
<td align="center">173,46
</td>
<td align="center">195,69
</td>
<td align="center">175,52
</td>
<td align="center">188,77
</td>
<td align="center">178,41
</td>
<td align="center">190,18
</td>
<td align="center">201,51
</td>
<td align="center">206,95
</td>
<td align="center">217,07
</td>
<td align="center">203,44
</td></tr>
<tr>
<th scope="row">Recette totale en salle
</th>
<td align="center">996,11&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;138,94&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;031,2&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;120,7&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;061,52&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;142,21&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;236,41&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;308,92&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;373,92&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;305,63&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td></tr>
<tr>
<th scope="row">Part de marché des films<br />français dans les recettes
</th>
<td align="center" valign="middle">34,9&#160;%
</td>
<td align="center" valign="middle">38,4&#160;%
</td>
<td align="center" valign="middle">36,5&#160;%
</td>
<td align="center" valign="middle">44,6&#160;%
</td>
<td align="center" valign="middle">36,5&#160;%
</td>
<td align="center" valign="middle">45,4&#160;%
</td>
<td align="center" valign="middle">36,8&#160;%
</td>
<td align="center" valign="middle">35,8&#160;%
</td>
<td align="center" valign="middle">40,9&#160;%
</td>
<td align="center" valign="middle">40,3&#160;%
</td></tr></tbody></table>

<table class="wikitable centre">
<tbody><tr>
<td>
</td>
<th scope="col"><a href="/wiki/2013_au_cin%C3%A9ma" title="2013 au cinéma">2013</a>
</th>
<th scope="col"><a href="/wiki/2014_au_cin%C3%A9ma" title="2014 au cinéma">2014</a>
</th>
<th scope="col"><a href="/wiki/2015_au_cin%C3%A9ma" title="2015 au cinéma">2015</a>
</th>
<th scope="col"><a href="/wiki/2016_au_cin%C3%A9ma" title="2016 au cinéma">2016</a>
</th>
<th scope="col"><a href="/wiki/2017_au_cin%C3%A9ma" title="2017 au cinéma">2017</a>
</th>
<th scope="col"><a href="/wiki/2018_au_cin%C3%A9ma" title="2018 au cinéma">2018</a>
</th>
<th scope="col"><a href="/wiki/2019_au_cin%C3%A9ma" title="2019 au cinéma">2019</a>
</th>
<th scope="col"><a href="/wiki/2020_au_cin%C3%A9ma" title="2020 au cinéma">2020</a>
</th></tr>
<tr>
<th scope="row">Nombre d'établissements
</th>
<td align="center">2&#160;026
</td>
<td align="center">2&#160;020
</td>
<td align="center">2&#160;033
</td>
<td align="center">2&#160;044
</td>
<td align="center">2&#160;046
</td>
<td align="center">2040
</td>
<td align="center">2045
</td>
<td align="center">2041
</td></tr>
<tr>
<th scope="row">Nombre de multiplexe (+8 salles)
</th>
<td align="center">188
</td>
<td align="center">191
</td>
<td align="center">203
</td>
<td align="center">209
</td>
<td align="center">219
</td>
<td align="center">226
</td>
<td align="center">232
</td>
<td align="center">233
</td></tr>
<tr>
<th scope="row">Nombre d'écrans actifs
</th>
<td align="center">5&#160;588
</td>
<td align="center">5&#160;653
</td>
<td align="center">5&#160;741
</td>
<td align="center">5&#160;842
</td>
<td align="center">5&#160;913
</td>
<td align="center">5982
</td>
<td align="center">6114
</td>
<td align="center">6127
</td></tr>
<tr>
<th scope="row">Nombre de fauteuils
</th>
<td align="center">1&#160;066&#160;840
</td>
<td align="center">1&#160;072&#160;407
</td>
<td align="center">1&#160;094&#160;703
</td>
<td align="center">1&#160;099&#160;526
</td>
<td align="center">1&#160;118&#160;916
</td>
<td align="center">1&#160;126&#160;162
</td>
<td align="center">1&#160;140&#160;999
</td>
<td align="center">1&#160;138&#160;530
</td></tr>
<tr>
<th scope="row">Nombre d'entrées (millions)
</th>
<td align="center">193,6
</td>
<td align="center">208,9
</td>
<td align="center">205,3
</td>
<td align="center">213,2
</td>
<td align="center">209,2
</td>
<td align="center">201,20
</td>
<td align="center">213.0
</td>
<td align="center">65;1
</td></tr>
<tr>
<th scope="row">Recette totale en salle
</th>
<td align="center">1&#160;250,87&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;332,73&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;331,3&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;388,6&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;380,6&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1336,73<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1447,4<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center"><abbr class="abbr" title="mégaeuro">M€</abbr>
</td></tr>
<tr>
<th scope="row">Part de marché des films<br />français dans les recettes
</th>
<td align="center" valign="middle">33,8&#160;%
</td>
<td align="center" valign="middle">44,5&#160;%
</td>
<td align="center" valign="middle">35,5&#160;%
</td>
<td align="center" valign="middle">35,8&#160;%
</td>
<td align="center" valign="middle">37,4&#160;%
</td>
<td align="center" valign="middle">39,3%
</td>
<td align="center" valign="middle">34,8&#160;%
</td>
<td align="center" valign="middle">44.9%
</td></tr></tbody></table>

En 1946, dans un soucis d'encadrer et de restaurer le cinéma français fortement impacté au crépuscule de la Seconde Guerre Mondiale, est fondé le Centre National du Cinéma et de l'image animée, dit CNC. Depuis 1968, suite à un arrêté imposant l’inventaire précis des collections bénéficiant de crédits publics, le CNC assure un suivi archivistique rigoureux des oeuvres et des données relatives au cinéma français. Ces données sont publiées depuis 2014 sur [la plateforme _opendata_ du gouvernement](https://www.data.gouv.fr/fr/).

**1) Jeu de données utilisé** 

Afin de pouvoir l'exploiter, j'ai dû procéder à un nettoyage de ce fichier xlsx car il ne s'accordait pas aux bonnes pratiques; des cellules étaient fusionnées, les données ne commencaient pas aux premières lignes du tableau, les valeurs numériques étaient décimales, ce qui faussait les visualisations. La plus grande difficulté que j'ai rencontré lors du _sanity check_ était la correction du format des valeurs dans la colonne "année de sortie". Elles étaient traitées comme des valeurs numériques décimales, il était donc impossible pour les outils de visualition de les traiter comme des dates. J'ai donc dû utiliser, sur OpenRefine, le langage GREL, pour arrondir les valeurs avec la fonction `value.round()` avant de convertir leur format en date grâce à la fonction `value.toDate()`, ce qui me retournait une date sous ce format : 
> [date 1998-01-01T00:00:00Z]

J'ai donc utilisé la fonction `value.datePart("year")` pour extraire et afficher uniquement l'année.

Voici le jeu de données tel qu'il était en accès libre :

<table width="600" height="450" frameborder ="0">
<thead>
  <tr>
    <th>Mis à jour le 22 juin 2022</th>
    <th></th>
    <th></th>
    <th></th>
    <th></th>
    <th></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Les plus grands succès du cinéma depuis 1945</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>rang</td>
    <td>titre</td>
    <td>réalisateur</td>
    <td>année de sortie</td>
    <td>nationalité1</td>
    <td>entrées (millions)2</td>
  </tr>
  <tr>
    <td>1.0</td>
    <td>Titanic</td>
    <td>J. Cameron</td>
    <td>1998.0</td>
    <td>US</td>
    <td>2.1798906E7</td>
  </tr>
  <tr>
    <td>2.0</td>
    <td>Bienvenue chez les Ch'tis</td>
    <td>D. Boon</td>
    <td>2008.0</td>
    <td>FR</td>
    <td>2.0444918E7</td>
  </tr>
  <tr>
    <td>3.0</td>
    <td>Intouchables</td>
    <td>E. Tolédano, O. Nakache</td>
    <td>2011.0</td>
    <td>FR</td>
    <td>1.9509835E7</td>
  </tr>
  <tr>
    <td>4.0</td>
    <td>La Grande Vadrouille</td>
    <td>G. Oury</td>
    <td>1966.0</td>
    <td>FR/GB</td>
    <td>1.7330139E7</td>
  </tr>
  <tr>
    <td>5.0</td>
    <td>Autant en emporte le vent</td>
    <td>V. Fleming</td>
    <td>1950.0</td>
    <td>US</td>
    <td>1.672816E7</td>
  </tr>
  <tr>
    <td>6.0</td>
    <td>Il était une fois dans l'Ouest</td>
    <td>S. Leone</td>
    <td>1969.0</td>
    <td>IT</td>
    <td>1.4891828E7</td>
  </tr>
  <tr>
    <td>7.0</td>
    <td>Le Livre de la jungle</td>
    <td>W. Reitherman</td>
    <td>1968.0</td>
    <td>US</td>
    <td>1.4798057E7</td>
  </tr>
  <tr>
    <td>8.0</td>
    <td>Avatar</td>
    <td>J. Cameron</td>
    <td>2009.0</td>
    <td>US</td>
    <td>1.4782116E7</td>
  </tr>
  <tr>
    <td>9.0</td>
    <td>Les 101 Dalmatiens</td>
    <td>W. Disney</td>
    <td>1961.0</td>
    <td>US</td>
    <td>1.4697525E7</td>
  </tr>
  <tr>
    <td>10.0</td>
    <td>Astérix et Obélix : mission Cléopâtre</td>
    <td>A. Chabat</td>
    <td>2002.0</td>
    <td>FR</td>
    <td>1.4408347E7</td>
  </tr>
  <tr>
    <td>11.0</td>
    <td>Les Dix Commandements</td>
    <td>C.B. DeMille</td>
    <td>1958.0</td>
    <td>US</td>
    <td>1.4237371E7</td>
  </tr>
  <tr>
    <td>12.0</td>
    <td>Ben Hur</td>
    <td>W. Wyler</td>
    <td>1960.0</td>
    <td>US</td>
    <td>1.385777E7</td>
  </tr>
  <tr>
    <td>13.0</td>
    <td>Les Visiteurs</td>
    <td>J.M. Poiré</td>
    <td>1993.0</td>
    <td>FR</td>
    <td>1.3673172E7</td>
  </tr>
  <tr>
    <td>14.0</td>
    <td>Le Pont de la rivière Kwai</td>
    <td>D. Lean</td>
    <td>1957.0</td>
    <td>GB</td>
    <td>1.3477151E7</td>
  </tr>
  <tr>
    <td>15.0</td>
    <td>Cendrillon</td>
    <td>W. Disney</td>
    <td>1950.0</td>
    <td>US</td>
    <td>1.3269623E7</td>
  </tr>
  <tr>
    <td>16.0</td>
    <td>Le Petit Monde de Don Camillo</td>
    <td>J. Duvivier</td>
    <td>1952.0</td>
    <td>IT/FR</td>
    <td>1.2791213E7</td>
  </tr>
  <tr>
    <td>17.0</td>
    <td>Les Aristochats</td>
    <td>W. Reitherman</td>
    <td>1971.0</td>
    <td>US</td>
    <td>1.2737882E7</td>
  </tr>
  <tr>
    <td>18.0</td>
    <td>Qu'est-ce qu'on a fait au bon dieu ?</td>
    <td>P. De Chauveron</td>
    <td>2014.0</td>
    <td>FR</td>
    <td>1.2356551E7</td>
  </tr>
  <tr>
    <td>19.0</td>
    <td>Le Jour le plus long</td>
    <td>Collectif</td>
    <td>1962.0</td>
    <td>US</td>
    <td>1.193055E7</td>
  </tr>
  <tr>
    <td>20.0</td>
    <td>Le Corniaud</td>
    <td>G. Oury</td>
    <td>1965.0</td>
    <td>FR/IT</td>
    <td>1.1744912E7</td>
  </tr>
  <tr>
    <td>21.0</td>
    <td>La Belle et le clochard</td>
    <td>W. Disney</td>
    <td>1955.0</td>
    <td>US</td>
    <td>1.1253225E7</td>
  </tr>
  <tr>
    <td>22.0</td>
    <td>Le Roi lion</td>
    <td>R. Aller, R. Minkoff</td>
    <td>1994.0</td>
    <td>US</td>
    <td>1.0747322E7</td>
  </tr>
  <tr>
    <td>23.0</td>
    <td>Bambi</td>
    <td>W. Disney</td>
    <td>1948.0</td>
    <td>US</td>
    <td>1.0715149E7</td>
  </tr>
  <tr>
    <td>24.0</td>
    <td>Star Wars : Episode 7, le reveil de la force</td>
    <td>J. J. Abrams</td>
    <td>2015.0</td>
    <td>US</td>
    <td>1.0345644E7</td>
  </tr>
  <tr>
    <td>25.0</td>
    <td>Taxi 2</td>
    <td>G. Krawczyk</td>
    <td>2000.0</td>
    <td>FR</td>
    <td>1.0302954E7</td>
  </tr>
  <tr>
    <td>26.0</td>
    <td>Trois hommes et un couffin</td>
    <td>C. Serreau</td>
    <td>1985.0</td>
    <td>FR</td>
    <td>1.0251813E7</td>
  </tr>
  <tr>
    <td>27.0</td>
    <td>Les Bronzés 3 - amis pour la vie</td>
    <td>P. Leconte</td>
    <td>2006.0</td>
    <td>FR</td>
    <td>1.0229483E7</td>
  </tr>
  <tr>
    <td>28.0</td>
    <td>Les Canons de Navarone</td>
    <td>J. Lee Thompson</td>
    <td>1961.0</td>
    <td>US</td>
    <td>1.0181324E7</td>
  </tr>
  <tr>
    <td>29.0</td>
    <td>La Guerre des boutons</td>
    <td>Y. Robert</td>
    <td>1962.0</td>
    <td>FR</td>
    <td>1.0052423E7</td>
  </tr>
  <tr>
    <td>30.0</td>
    <td>Les Misérables</td>
    <td>J.P. Le Chanois, J.P. Dreyfus</td>
    <td>1958.0</td>
    <td>FR/IT</td>
    <td>9969086.0</td>
  </tr>
  <tr>
    <td>31.0</td>
    <td>Le Roi Lion</td>
    <td>J. Favreau</td>
    <td>2019.0</td>
    <td>US</td>
    <td>9848728.0</td>
  </tr>
  <tr>
    <td>32.0</td>
    <td>E.T. l'extra-terrestre</td>
    <td>S. Spielberg</td>
    <td>1982.0</td>
    <td>US</td>
    <td>9847614.0</td>
  </tr>
  <tr>
    <td>33.0</td>
    <td>Docteur Jivago</td>
    <td>D. Lean</td>
    <td>1966.0</td>
    <td>US</td>
    <td>9817737.0</td>
  </tr>
  <tr>
    <td>34.0</td>
    <td>Vingt mille lieues sous les mers</td>
    <td>R. Fleischer</td>
    <td>1955.0</td>
    <td>US</td>
    <td>9628014.0</td>
  </tr>
  <tr>
    <td>35.0</td>
    <td>Harry Potter à l'école des sorciers</td>
    <td>C. Colombus</td>
    <td>2001.0</td>
    <td>US</td>
    <td>9545909.0</td>
  </tr>
  <tr>
    <td>36.0</td>
    <td>Sous le plus grand chapiteau du monde</td>
    <td>C.B. DeMille</td>
    <td>1953.0</td>
    <td>US</td>
    <td>9488114.0</td>
  </tr>
  <tr>
    <td>37.0</td>
    <td>Le Monde de Nemo</td>
    <td>A. Stanton, L. Unkrich</td>
    <td>2003.0</td>
    <td>US</td>
    <td>9446595.0</td>
  </tr>
  <tr>
    <td>38.0</td>
    <td>Le Dîner de cons</td>
    <td>F. Veber</td>
    <td>1998.0</td>
    <td>FR</td>
    <td>9249770.0</td>
  </tr>
  <tr>
    <td>39.0</td>
    <td>Le Grand Bleu</td>
    <td>L. Besson</td>
    <td>1988.0</td>
    <td>FR</td>
    <td>9200891.0</td>
  </tr>
  <tr>
    <td>40.0</td>
    <td>L'Ours</td>
    <td>J.J. Annaud</td>
    <td>1988.0</td>
    <td>FR</td>
    <td>9138948.0</td>
  </tr>
  <tr>
    <td>41.0</td>
    <td>Emmanuelle</td>
    <td>J. Jaeckin</td>
    <td>1974.0</td>
    <td>FR</td>
    <td>8894166.0</td>
  </tr>
  <tr>
    <td>42.0</td>
    <td>Harry Potter et la chambre des secrets</td>
    <td>C. Colombus</td>
    <td>2002.0</td>
    <td>US</td>
    <td>8862273.0</td>
  </tr>
  <tr>
    <td>43.0</td>
    <td>La Vache et le prisonnier</td>
    <td>H. Verneuil</td>
    <td>1959.0</td>
    <td>FR/IT</td>
    <td>8851261.0</td>
  </tr>
  <tr>
    <td>44.0</td>
    <td>West Side Story</td>
    <td>R. Wise, J. Robbins</td>
    <td>1962.0</td>
    <td>US</td>
    <td>8780013.0</td>
  </tr>
  <tr>
    <td>45.0</td>
    <td>Astérix et Obélix contre César</td>
    <td>C. Zidi</td>
    <td>1999.0</td>
    <td>FR/DE/IT</td>
    <td>8776587.0</td>
  </tr>
  <tr>
    <td>46.0</td>
    <td>La Grande Evasion</td>
    <td>R. Walsh</td>
    <td>1963.0</td>
    <td>US</td>
    <td>8757609.0</td>
  </tr>
  <tr>
    <td>47.0</td>
    <td>Le Bataillon du ciel</td>
    <td>A. Esway</td>
    <td>1947.0</td>
    <td>FR</td>
    <td>8649752.0</td>
  </tr>
  <tr>
    <td>48.0</td>
    <td>Le Fabuleux Destin d'Amélie Poulain</td>
    <td>J.P. Jeunet</td>
    <td>2001.0</td>
    <td>FR/DE</td>
    <td>8527435.0</td>
  </tr>
  <tr>
    <td>49.0</td>
    <td>Les Choristes</td>
    <td>C. Barratier</td>
    <td>2004.0</td>
    <td>FR/CH</td>
    <td>8469922.0</td>
  </tr>
  <tr>
    <td>50.0</td>
    <td>Le Dictateur</td>
    <td>C. Chaplin</td>
    <td>1945.0</td>
    <td>US</td>
    <td>8406911.0</td>
  </tr>
  <tr>
    <td>51.0</td>
    <td>Pour qui sonne le glas ?</td>
    <td>S. Wood</td>
    <td>1947.0</td>
    <td>US</td>
    <td>8274759.0</td>
  </tr>
  <tr>
    <td>52.0</td>
    <td>Rien à déclarer</td>
    <td>D. Boon</td>
    <td>2011.0</td>
    <td>FR/BE</td>
    <td>8140813.0</td>
  </tr>
  <tr>
    <td>53.0</td>
    <td>Violettes impériales</td>
    <td>R. Pottier</td>
    <td>1952.0</td>
    <td>FR/ES</td>
    <td>8125846.0</td>
  </tr>
  <tr>
    <td>54.0</td>
    <td>Les Couloirs du temps - les visiteurs 2</td>
    <td>J.M. Poiré</td>
    <td>1998.0</td>
    <td>FR</td>
    <td>8039466.0</td>
  </tr>
  <tr>
    <td>55.0</td>
    <td>Le Boulanger de Valorgue</td>
    <td>H. Verneuil</td>
    <td>1953.0</td>
    <td>FR</td>
    <td>7889091.0</td>
  </tr>
  <tr>
    <td>56.0</td>
    <td>Un Indien dans la ville</td>
    <td>H. Palud</td>
    <td>1994.0</td>
    <td>FR</td>
    <td>7887974.0</td>
  </tr>
  <tr>
    <td>57.0</td>
    <td>Pinocchio</td>
    <td>W. Disney</td>
    <td>1946.0</td>
    <td>US</td>
    <td>7854113.0</td>
  </tr>
  <tr>
    <td>58.0</td>
    <td>L'Âge de glace 3 - le temps des dinosaures</td>
    <td>C. Saldanha</td>
    <td>2009.0</td>
    <td>US</td>
    <td>7836584.0</td>
  </tr>
  <tr>
    <td>59.0</td>
    <td>Star Wars : épisode 1 - la menace fantôme</td>
    <td>G. Lucas</td>
    <td>1999.0</td>
    <td>US</td>
    <td>7835365.0</td>
  </tr>
  <tr>
    <td>60.0</td>
    <td>Tarzan</td>
    <td>C. Buck, K. Lima</td>
    <td>1999.0</td>
    <td>US</td>
    <td>7822887.0</td>
  </tr>
  <tr>
    <td>61.0</td>
    <td>Le Gendarme de Saint-Tropez</td>
    <td>J. Girault</td>
    <td>1964.0</td>
    <td>FR/IT</td>
    <td>7811393.0</td>
  </tr>
  <tr>
    <td>62.0</td>
    <td>Le Comte de Monte Cristo</td>
    <td>R. Vernay</td>
    <td>1955.0</td>
    <td>FR/IT</td>
    <td>7780963.0</td>
  </tr>
  <tr>
    <td>63.0</td>
    <td>Sixième Sens</td>
    <td>M. Night Shyamalan</td>
    <td>2000.0</td>
    <td>US</td>
    <td>7743424.0</td>
  </tr>
  <tr>
    <td>64.0</td>
    <td>Ratatouille</td>
    <td>B. Bird, J. Pinkava</td>
    <td>2007.0</td>
    <td>US</td>
    <td>7727621.0</td>
  </tr>
  <tr>
    <td>65.0</td>
    <td>Le Cinquième Elément</td>
    <td>L. Besson</td>
    <td>1997.0</td>
    <td>FR</td>
    <td>7713105.0</td>
  </tr>
  <tr>
    <td>66.0</td>
    <td>Harry Potter et la coupe de feu</td>
    <td>M. Newell</td>
    <td>2005.0</td>
    <td>GB</td>
    <td>7712423.0</td>
  </tr>
  <tr>
    <td>67.0</td>
    <td>la famille Bélier</td>
    <td>É. Lartigau</td>
    <td>2014.0</td>
    <td>FR</td>
    <td>7704036.0</td>
  </tr>
  <tr>
    <td>68.0</td>
    <td>Orange mécanique</td>
    <td>S. Kubrick</td>
    <td>1972.0</td>
    <td>GB</td>
    <td>7629804.0</td>
  </tr>
  <tr>
    <td>69.0</td>
    <td>La Reine des neiges 2</td>
    <td>C. Buck, J. Lee</td>
    <td>2019.0</td>
    <td>US</td>
    <td>7527360.0</td>
  </tr>
  <tr>
    <td>70.0</td>
    <td>Les Bidasses en folie</td>
    <td>C. Zidi</td>
    <td>1971.0</td>
    <td>FR</td>
    <td>7460911.0</td>
  </tr>
  <tr>
    <td>71.0</td>
    <td>Le Retour de Don Camillo</td>
    <td>J. Duvivier</td>
    <td>1953.0</td>
    <td>IT/FR</td>
    <td>7425550.0</td>
  </tr>
  <tr>
    <td>72.0</td>
    <td>Le Seigneur des anneaux - le retour du roi</td>
    <td>P. Jackson</td>
    <td>2003.0</td>
    <td>NZ</td>
    <td>7423673.0</td>
  </tr>
  <tr>
    <td>73.0</td>
    <td>La Vérité si je mens 2</td>
    <td>T. Gilou</td>
    <td>2001.0</td>
    <td>FR</td>
    <td>7407982.0</td>
  </tr>
  <tr>
    <td>74.0</td>
    <td>Jour de fête</td>
    <td>J. Tati</td>
    <td>1949.0</td>
    <td>FR</td>
    <td>7402939.0</td>
  </tr>
  <tr>
    <td>75.0</td>
    <td>Aladdin</td>
    <td>J. Musker</td>
    <td>1993.0</td>
    <td>US</td>
    <td>7353322.0</td>
  </tr>
  <tr>
    <td>76.0</td>
    <td>Les Aventures de Peter Pan</td>
    <td>W. Disney</td>
    <td>1953.0</td>
    <td>US</td>
    <td>7347176.0</td>
  </tr>
  <tr>
    <td>77.0</td>
    <td>Les Aventures de Rabbi Jacob</td>
    <td>G. Oury</td>
    <td>1973.0</td>
    <td>FR/IT</td>
    <td>7307118.0</td>
  </tr>
  <tr>
    <td>78.0</td>
    <td>Danse avec les loups</td>
    <td>K. Costner</td>
    <td>1991.0</td>
    <td>US</td>
    <td>7281824.0</td>
  </tr>
  <tr>
    <td>79.0</td>
    <td>Les Aventures de Bernard et Bianca</td>
    <td>Collectif</td>
    <td>1977.0</td>
    <td>US</td>
    <td>7242381.0</td>
  </tr>
  <tr>
    <td>80.0</td>
    <td>Jean de Florette</td>
    <td>C. Berri</td>
    <td>1986.0</td>
    <td>FR</td>
    <td>7225184.0</td>
  </tr>
  <tr>
    <td>81.0</td>
    <td>Star Wars : épisode 3 - la revanche des Sith</td>
    <td>G. Lucas</td>
    <td>2005.0</td>
    <td>US</td>
    <td>7205953.0</td>
  </tr>
  <tr>
    <td>82.0</td>
    <td>Harry Potter et le prisonnier d'Azkaban</td>
    <td>A. Cuaron</td>
    <td>2004.0</td>
    <td>GB</td>
    <td>7152904.0</td>
  </tr>
  <tr>
    <td>83.0</td>
    <td>Shrek 2</td>
    <td>A. Adamson, V. Jenson</td>
    <td>2004.0</td>
    <td>US</td>
    <td>7142658.0</td>
  </tr>
  <tr>
    <td>84.0</td>
    <td>Le Seigneur des anneaux - les deux tours</td>
    <td>P. Jackson</td>
    <td>2002.0</td>
    <td>NZ</td>
    <td>7128603.0</td>
  </tr>
  <tr>
    <td>85.0</td>
    <td>Samson et Dalila</td>
    <td>C.B. DeMille</td>
    <td>1951.0</td>
    <td>US</td>
    <td>7116461.0</td>
  </tr>
  <tr>
    <td>86.0</td>
    <td>Star Wars les derniers Jedi</td>
    <td>R. Johnson</td>
    <td>2017.0</td>
    <td>US</td>
    <td>7094279.0</td>
  </tr>
  <tr>
    <td>87.0</td>
    <td>Jeanne d'Arc</td>
    <td>V. Fleming</td>
    <td>1949.0</td>
    <td>US</td>
    <td>7092805.0</td>
  </tr>
  <tr>
    <td>88.0</td>
    <td>La Chèvre</td>
    <td>F. Veber</td>
    <td>1981.0</td>
    <td>FR/MX</td>
    <td>7080976.0</td>
  </tr>
  <tr>
    <td>89.0</td>
    <td>Monsieur Vincent</td>
    <td>M. Cloche</td>
    <td>1947.0</td>
    <td>FR</td>
    <td>7057022.0</td>
  </tr>
  <tr>
    <td>90.0</td>
    <td>Les Sept Mercenaires</td>
    <td>J. Sturges</td>
    <td>1961.0</td>
    <td>US</td>
    <td>7044522.0</td>
  </tr>
  <tr>
    <td>91.0</td>
    <td>Le Seigneur des anneaux - la communauté de l'anneau</td>
    <td>P. Jackson</td>
    <td>2001.0</td>
    <td>NZ</td>
    <td>7011664.0</td>
  </tr>
  <tr>
    <td>92.0</td>
    <td>Skyfall</td>
    <td>S. Mendes</td>
    <td>2012.0</td>
    <td>GB</td>
    <td>7009368.0</td>
  </tr>
  <tr>
    <td>93.0</td>
    <td>Si Versailles m'était conté</td>
    <td>S. Guitry</td>
    <td>1954.0</td>
    <td>FR</td>
    <td>6987432.0</td>
  </tr>
  <tr>
    <td>94.0</td>
    <td>Les Grandes Vacances</td>
    <td>J. Girault</td>
    <td>1967.0</td>
    <td>FR/IT</td>
    <td>6987269.0</td>
  </tr>
  <tr>
    <td>95.0</td>
    <td>Le Salaire de la peur</td>
    <td>H.G. Clouzot</td>
    <td>1953.0</td>
    <td>FR/IT</td>
    <td>6950146.0</td>
  </tr>
  <tr>
    <td>96.0</td>
    <td>Michel Strogoff</td>
    <td>C. Gallone</td>
    <td>1956.0</td>
    <td>FR/IT</td>
    <td>6869247.0</td>
  </tr>
  <tr>
    <td>97.0</td>
    <td>Le Gendarme se marie</td>
    <td>J. Girault</td>
    <td>1968.0</td>
    <td>FR/IT</td>
    <td>6828665.0</td>
  </tr>
  <tr>
    <td>98.0</td>
    <td>Avengers : Endgame</td>
    <td>A. Russo, J. Russo</td>
    <td>2019.0</td>
    <td>US</td>
    <td>6825154.0</td>
  </tr>
  <tr>
    <td>99.0</td>
    <td>Le Bossu de Notre-Dame</td>
    <td>K. Wise, G. Trousdale</td>
    <td>1996.0</td>
    <td>US</td>
    <td>6813099.0</td>
  </tr>
  <tr>
    <td>100.0</td>
    <td>Astérix aux Jeux Olympiques</td>
    <td>F. Forestier, T. Langmann</td>
    <td>2008.0</td>
    <td>FR/DE/ES/IT</td>
    <td>6807835.0</td>
  </tr>
  <tr>
    <td>101.0</td>
    <td>Mission spéciale</td>
    <td>M. de Canonge</td>
    <td>1946.0</td>
    <td>FR</td>
    <td>6781120.0</td>
  </tr>
  <tr>
    <td>102.0</td>
    <td>Jurassic Park</td>
    <td>S. Spielberg</td>
    <td>1993.0</td>
    <td>US</td>
    <td>6755899.0</td>
  </tr>
  <tr>
    <td>103.0</td>
    <td>Fanfan la Tulipe</td>
    <td>Christian-Jaque</td>
    <td>1952.0</td>
    <td>FR/IT</td>
    <td>6737998.0</td>
  </tr>
  <tr>
    <td>104.0</td>
    <td>L'Exorciste</td>
    <td>W. Friedkin</td>
    <td>1974.0</td>
    <td>US</td>
    <td>6727910.0</td>
  </tr>
  <tr>
    <td>105.0</td>
    <td>Qu'est-ce qu'on a encore fait au bon dieu ?</td>
    <td>P. de Chauveron</td>
    <td>2019.0</td>
    <td>FR / BE</td>
    <td>6719759.0</td>
  </tr>
  <tr>
    <td>106.0</td>
    <td>Rox et Rouky</td>
    <td>A. Stevens</td>
    <td>1981.0</td>
    <td>US</td>
    <td>6717395.0</td>
  </tr>
  <tr>
    <td>107.0</td>
    <td>Goldfinger</td>
    <td>G. Hamilton</td>
    <td>1965.0</td>
    <td>GB</td>
    <td>6676568.0</td>
  </tr>
  <tr>
    <td>108.0</td>
    <td>Les Trois Frères</td>
    <td>D. Bourdon, B. Campan</td>
    <td>1995.0</td>
    <td>FR</td>
    <td>6671088.0</td>
  </tr>
  <tr>
    <td>109.0</td>
    <td>les Minions</td>
    <td>P. Coffin, K. Balda</td>
    <td>2015.0</td>
    <td>US</td>
    <td>6663465.0</td>
  </tr>
  <tr>
    <td>110.0</td>
    <td>Nous irons à Paris</td>
    <td>J. Boyer</td>
    <td>1950.0</td>
    <td>FR</td>
    <td>6659325.0</td>
  </tr>
  <tr>
    <td>111.0</td>
    <td>Manon des sources</td>
    <td>C. Berri</td>
    <td>1986.0</td>
    <td>FR</td>
    <td>6646236.0</td>
  </tr>
  <tr>
    <td>112.0</td>
    <td>l'Age de glace 4 : la dérive des continents</td>
    <td>M.Thurmeier, S. Martino</td>
    <td>2012.0</td>
    <td>US</td>
    <td>6642048.0</td>
  </tr>
  <tr>
    <td>113.0</td>
    <td>Sissi</td>
    <td>E. Marischka</td>
    <td>1956.0</td>
    <td>AT</td>
    <td>6637836.0</td>
  </tr>
  <tr>
    <td>114.0</td>
    <td>L'Age de glace 2</td>
    <td>C. Saldanha</td>
    <td>2006.0</td>
    <td>US</td>
    <td>6627706.0</td>
  </tr>
  <tr>
    <td>115.0</td>
    <td>Le Cercle des poètes disparus</td>
    <td>P. Weir</td>
    <td>1989.0</td>
    <td>US</td>
    <td>6601781.0</td>
  </tr>
  <tr>
    <td>116.0</td>
    <td>La Belle au bois dormant</td>
    <td>W. Disney</td>
    <td>1959.0</td>
    <td>US</td>
    <td>6592751.0</td>
  </tr>
  <tr>
    <td>117.0</td>
    <td>Harry Potter et les reliques de la mort - 2e partie</td>
    <td>D. Yates</td>
    <td>2011.0</td>
    <td>GB</td>
    <td>6577156.0</td>
  </tr>
  <tr>
    <td>118.0</td>
    <td>Pirates des Caraïbes - le secret du coffre maudit</td>
    <td>G. Verbinski</td>
    <td>2006.0</td>
    <td>US</td>
    <td>6522015.0</td>
  </tr>
  <tr>
    <td>119.0</td>
    <td>Robin des bois</td>
    <td>W. Reitherman</td>
    <td>1974.0</td>
    <td>US</td>
    <td>6485372.0</td>
  </tr>
  <tr>
    <td>120.0</td>
    <td>Taxi</td>
    <td>G. Pires</td>
    <td>1998.0</td>
    <td>FR</td>
    <td>6485260.0</td>
  </tr>
  <tr>
    <td>121.0</td>
    <td>Rain Man</td>
    <td>B. Levinson</td>
    <td>1989.0</td>
    <td>US</td>
    <td>6475822.0</td>
  </tr>
  <tr>
    <td>122.0</td>
    <td>La Guerre des étoiles</td>
    <td>G. Lucas</td>
    <td>1977.0</td>
    <td>US</td>
    <td>6460540.0</td>
  </tr>
  <tr>
    <td>123.0</td>
    <td>Sissi impératrice</td>
    <td>E. Marischka</td>
    <td>1957.0</td>
    <td>AT</td>
    <td>6429021.0</td>
  </tr>
  <tr>
    <td>124.0</td>
    <td>Les Aventuriers de l'arche perdue</td>
    <td>S. Spielberg</td>
    <td>1981.0</td>
    <td>US</td>
    <td>6404631.0</td>
  </tr>
  <tr>
    <td>125.0</td>
    <td>Tant qu'il y aura des hommes</td>
    <td>F. Zinnemann</td>
    <td>1954.0</td>
    <td>US</td>
    <td>6401375.0</td>
  </tr>
  <tr>
    <td>126.0</td>
    <td>Arthur et les Minimoys</td>
    <td>L. Besson</td>
    <td>2006.0</td>
    <td>FR</td>
    <td>6400180.0</td>
  </tr>
  <tr>
    <td>127.0</td>
    <td>La Cuisine au beurre</td>
    <td>G. Grangier</td>
    <td>1963.0</td>
    <td>FR/IT</td>
    <td>6397594.0</td>
  </tr>
  <tr>
    <td>128.0</td>
    <td>Spider-Man</td>
    <td>S. Raimi</td>
    <td>2002.0</td>
    <td>US</td>
    <td>6382266.0</td>
  </tr>
  <tr>
    <td>129.0</td>
    <td>La Symphonie pastorale</td>
    <td>J. Delannoy</td>
    <td>1946.0</td>
    <td>FR</td>
    <td>6373084.0</td>
  </tr>
  <tr>
    <td>130.0</td>
    <td>Ivanhoé</td>
    <td>R. Thorpe</td>
    <td>1952.0</td>
    <td>US</td>
    <td>6362071.0</td>
  </tr>
  <tr>
    <td>131.0</td>
    <td>Le Bon, la brute et le truand</td>
    <td>S. Leone</td>
    <td>1968.0</td>
    <td>IT</td>
    <td>6350067.0</td>
  </tr>
  <tr>
    <td>132.0</td>
    <td>Les Dents de la mer</td>
    <td>S. Spielberg</td>
    <td>1976.0</td>
    <td>US</td>
    <td>6346372.0</td>
  </tr>
  <tr>
    <td>133.0</td>
    <td>Spider-Man 3</td>
    <td>S. Raimi</td>
    <td>2007.0</td>
    <td>US</td>
    <td>6320882.0</td>
  </tr>
  <tr>
    <td>134.0</td>
    <td>Quo Vadis</td>
    <td>M. Le Roy</td>
    <td>1953.0</td>
    <td>US</td>
    <td>6305624.0</td>
  </tr>
  <tr>
    <td>135.0</td>
    <td>La Gloire de mon père</td>
    <td>Y. Robert</td>
    <td>1990.0</td>
    <td>FR</td>
    <td>6298736.0</td>
  </tr>
  <tr>
    <td>136.0</td>
    <td>Le Gendarme et les extra-terrestres</td>
    <td>J. Girault</td>
    <td>1979.0</td>
    <td>FR</td>
    <td>6280079.0</td>
  </tr>
  <tr>
    <td>137.0</td>
    <td>Indiana Jones et la dernière croisade</td>
    <td>S. Spielberg</td>
    <td>1989.0</td>
    <td>US</td>
    <td>6256297.0</td>
  </tr>
  <tr>
    <td>138.0</td>
    <td>Harry Potter et l'ordre du Phénix</td>
    <td>D. Yates</td>
    <td>2007.0</td>
    <td>GB</td>
    <td>6219499.0</td>
  </tr>
  <tr>
    <td>139.0</td>
    <td>Marche à l'ombre</td>
    <td>M. Blanc</td>
    <td>1984.0</td>
    <td>FR</td>
    <td>6168425.0</td>
  </tr>
  <tr>
    <td>140.0</td>
    <td>Pas si bête</td>
    <td>A. Berthomieu</td>
    <td>1946.0</td>
    <td>FR</td>
    <td>6165419.0</td>
  </tr>
  <tr>
    <td>141.0</td>
    <td>Merlin l'enchanteur</td>
    <td>W. Reitherman</td>
    <td>1964.0</td>
    <td>US</td>
    <td>6160500.0</td>
  </tr>
  <tr>
    <td>142.0</td>
    <td>La Chartreuse de Parme</td>
    <td>Christian-Jaque</td>
    <td>1948.0</td>
    <td>FR</td>
    <td>6152480.0</td>
  </tr>
  <tr>
    <td>143.0</td>
    <td>Germinal</td>
    <td>C. Berri</td>
    <td>1993.0</td>
    <td>FR/BE</td>
    <td>6149725.0</td>
  </tr>
  <tr>
    <td>144.0</td>
    <td>Harry Potter et le Prince de sang-mêlé</td>
    <td>D. Yates</td>
    <td>2009.0</td>
    <td>GB</td>
    <td>6140398.0</td>
  </tr>
  <tr>
    <td>145.0</td>
    <td>Le Père tranquille</td>
    <td>R. Clément</td>
    <td>1946.0</td>
    <td>FR</td>
    <td>6139259.0</td>
  </tr>
  <tr>
    <td>146.0</td>
    <td>Les Feux de la rampe</td>
    <td>C. Chaplin</td>
    <td>1952.0</td>
    <td>US</td>
    <td>6137070.0</td>
  </tr>
  <tr>
    <td>147.0</td>
    <td>Oscar</td>
    <td>E. Molinaro</td>
    <td>1967.0</td>
    <td>FR</td>
    <td>6123063.0</td>
  </tr>
  <tr>
    <td>148.0</td>
    <td>Taxi 3</td>
    <td>G. Krawczyk</td>
    <td>2003.0</td>
    <td>FR</td>
    <td>6108669.0</td>
  </tr>
  <tr>
    <td>149.0</td>
    <td>Harry Potter et les reliques de la mort - 1re partie</td>
    <td>D. Yates</td>
    <td>2010.0</td>
    <td>GB</td>
    <td>6102789.0</td>
  </tr>
  <tr>
    <td>150.0</td>
    <td>Star Wars : épisode 9, l'ascension de Skywalker</td>
    <td>J.J. Abrams</td>
    <td>2019.0</td>
    <td>US</td>
    <td>6063436.0</td>
  </tr>
  <tr>
    <td>151.0</td>
    <td>Terminator 2 - le jugement dernier</td>
    <td>J. Cameron</td>
    <td>1991.0</td>
    <td>US</td>
    <td>6007492.0</td>
  </tr>
  <tr>
    <td>152.0</td>
    <td>Midnight Express</td>
    <td>A. Parker</td>
    <td>1978.0</td>
    <td>GB</td>
    <td>5974912.0</td>
  </tr>
  <tr>
    <td>153.0</td>
    <td>Les Dieux sont tombés sur la tête</td>
    <td>J. Uys</td>
    <td>1983.0</td>
    <td>ZA</td>
    <td>5950116.0</td>
  </tr>
  <tr>
    <td>154.0</td>
    <td>Mourir d'aimer</td>
    <td>A. Cayatte</td>
    <td>1971.0</td>
    <td>FR/IT</td>
    <td>5912600.0</td>
  </tr>
  <tr>
    <td>155.0</td>
    <td>Qui veut la peau de Roger Rabbit ?</td>
    <td>R. Zemeckis</td>
    <td>1988.0</td>
    <td>US</td>
    <td>5909001.0</td>
  </tr>
  <tr>
    <td>156.0</td>
    <td>Crocodile Dundee</td>
    <td>P. Faiman</td>
    <td>1987.0</td>
    <td>AU</td>
    <td>5887982.0</td>
  </tr>
  <tr>
    <td>157.0</td>
    <td>Guerre et Paix</td>
    <td>K. Vidor</td>
    <td>1956.0</td>
    <td>US</td>
    <td>5885856.0</td>
  </tr>
  <tr>
    <td>158.0</td>
    <td>Les Ripoux</td>
    <td>C. Zidi</td>
    <td>1984.0</td>
    <td>FR</td>
    <td>5882397.0</td>
  </tr>
  <tr>
    <td>159.0</td>
    <td>L'Odyssée du Docteur Wassel</td>
    <td>C.B. DeMille</td>
    <td>1946.0</td>
    <td>US</td>
    <td>5866693.0</td>
  </tr>
  <tr>
    <td>160.0</td>
    <td>Rambo 2 - la mission</td>
    <td>G.P. Cosmatos</td>
    <td>1985.0</td>
    <td>US</td>
    <td>5851440.0</td>
  </tr>
  <tr>
    <td>161.0</td>
    <td>Le Bossu</td>
    <td>A. Hunebelle</td>
    <td>1959.0</td>
    <td>FR/IT</td>
    <td>5847123.0</td>
  </tr>
  <tr>
    <td>162.0</td>
    <td>L'Aile ou la Cuisse</td>
    <td>C. Zidi</td>
    <td>1976.0</td>
    <td>FR</td>
    <td>5843090.0</td>
  </tr>
  <tr>
    <td>163.0</td>
    <td>Les Vacances de Monsieur Hulot</td>
    <td>J. Tati</td>
    <td>1953.0</td>
    <td>FR</td>
    <td>5799875.0</td>
  </tr>
  <tr>
    <td>164.0</td>
    <td>Sissi face à son destin</td>
    <td>E. Marischka</td>
    <td>1958.0</td>
    <td>AT</td>
    <td>5794263.0</td>
  </tr>
  <tr>
    <td>165.0</td>
    <td>Quatre mariages et un enterrement</td>
    <td>M. Newell</td>
    <td>1994.0</td>
    <td>GB</td>
    <td>5781268.0</td>
  </tr>
  <tr>
    <td>166.0</td>
    <td>Mulan</td>
    <td>T. Bancroft, B. Cook</td>
    <td>1998.0</td>
    <td>US</td>
    <td>5776901.0</td>
  </tr>
  <tr>
    <td>167.0</td>
    <td>Men in Black</td>
    <td>B. Sonnenfeld</td>
    <td>1997.0</td>
    <td>US</td>
    <td>5759617.0</td>
  </tr>
  <tr>
    <td>168.0</td>
    <td>Le train sifflera trois fois</td>
    <td>F. Zinnemann</td>
    <td>1952.0</td>
    <td>US</td>
    <td>5756216.0</td>
  </tr>
  <tr>
    <td>169.0</td>
    <td>Moi, moche et méchant 3</td>
    <td>K. Balda, P. Coffin, E. Guillon</td>
    <td>2017.0</td>
    <td>US</td>
    <td>5746829.0</td>
  </tr>
  <tr>
    <td>170.0</td>
    <td>Grease</td>
    <td>R. Kleiser</td>
    <td>1978.0</td>
    <td>US</td>
    <td>5745596.0</td>
  </tr>
  <tr>
    <td>171.0</td>
    <td>Les Indestructibles 2</td>
    <td>B. Brad</td>
    <td>2018.0</td>
    <td>US</td>
    <td>5744813.0</td>
  </tr>
  <tr>
    <td>172.0</td>
    <td>Les Fous du stade</td>
    <td>C. Zidi</td>
    <td>1972.0</td>
    <td>FR</td>
    <td>5744270.0</td>
  </tr>
  <tr>
    <td>173.0</td>
    <td>Le Troisième Homme</td>
    <td>C. Reed</td>
    <td>1949.0</td>
    <td>GB</td>
    <td>5742569.0</td>
  </tr>
  <tr>
    <td>174.0</td>
    <td>Opération tonnerre</td>
    <td>T. Young</td>
    <td>1965.0</td>
    <td>GB</td>
    <td>5735506.0</td>
  </tr>
  <tr>
    <td>175.0</td>
    <td>Andalousie</td>
    <td>R. Vernay</td>
    <td>1951.0</td>
    <td>FR/ES</td>
    <td>5735108.0</td>
  </tr>
  <tr>
    <td>176.0</td>
    <td>Les Anges gardiens</td>
    <td>J.M. Poiré</td>
    <td>1995.0</td>
    <td>FR</td>
    <td>5734326.0</td>
  </tr>
  <tr>
    <td>177.0</td>
    <td>Les Valseuses</td>
    <td>B. Blier</td>
    <td>1974.0</td>
    <td>FR</td>
    <td>5729042.0</td>
  </tr>
  <tr>
    <td>178.0</td>
    <td>La Bataille du rail</td>
    <td>R. Clément</td>
    <td>1946.0</td>
    <td>FR</td>
    <td>5727974.0</td>
  </tr>
  <tr>
    <td>179.0</td>
    <td>Lawrence d'Arabie</td>
    <td>D. Lean</td>
    <td>1963.0</td>
    <td>GB</td>
    <td>5718291.0</td>
  </tr>
  <tr>
    <td>180.0</td>
    <td>A nous les petites Anglaises</td>
    <td>M. Lang</td>
    <td>1976.0</td>
    <td>FR</td>
    <td>5704446.0</td>
  </tr>
  <tr>
    <td>181.0</td>
    <td>La Vérité</td>
    <td>H.G. Clouzot</td>
    <td>1960.0</td>
    <td>FR/IT</td>
    <td>5701210.0</td>
  </tr>
  <tr>
    <td>182.0</td>
    <td>Notre-Dame de Paris</td>
    <td>J. Delannoy</td>
    <td>1956.0</td>
    <td>FR/IT</td>
    <td>5700102.0</td>
  </tr>
  <tr>
    <td>183.0</td>
    <td>Indiana Jones et le temple maudit</td>
    <td>S. Spielberg</td>
    <td>1984.0</td>
    <td>US</td>
    <td>5690878.0</td>
  </tr>
  <tr>
    <td>184.0</td>
    <td>Les Tuche 3</td>
    <td>O. Baroux</td>
    <td>2018.0</td>
    <td>FR</td>
    <td>5687833.0</td>
  </tr>
  <tr>
    <td>185.0</td>
    <td>Matrix Reloaded</td>
    <td>L. Wachowski, A. Wachowski</td>
    <td>2003.0</td>
    <td>US</td>
    <td>5672070.0</td>
  </tr>
  <tr>
    <td>186.0</td>
    <td>Pirates des Caraïbes - jusqu'au bout du monde</td>
    <td>G. Verbinski</td>
    <td>2007.0</td>
    <td>US</td>
    <td>5639260.0</td>
  </tr>
  <tr>
    <td>187.0</td>
    <td>Pocahontas, une légende indienne</td>
    <td>M. Gabriel, E. Goldberg</td>
    <td>1995.0</td>
    <td>US</td>
    <td>5634513.0</td>
  </tr>
  <tr>
    <td>188.0</td>
    <td>La Ch'tite Famille</td>
    <td>D. Boon</td>
    <td>2018.0</td>
    <td>FR</td>
    <td>5630428.0</td>
  </tr>
  <tr>
    <td>189.0</td>
    <td>Bons baisers de Russie</td>
    <td>T. Young</td>
    <td>1964.0</td>
    <td>GB</td>
    <td>5625125.0</td>
  </tr>
  <tr>
    <td>190.0</td>
    <td>Star Wars : épisode 2 - l'attaque des clones</td>
    <td>G. Lucas</td>
    <td>2002.0</td>
    <td>US</td>
    <td>5624277.0</td>
  </tr>
  <tr>
    <td>191.0</td>
    <td>Le Petit Nicolas</td>
    <td>L. Tirard</td>
    <td>2009.0</td>
    <td>FR/BE</td>
    <td>5616187.0</td>
  </tr>
  <tr>
    <td>192.0</td>
    <td>Joker</td>
    <td>T. Phillips</td>
    <td>2019.0</td>
    <td>US</td>
    <td>5611793.0</td>
  </tr>
  <tr>
    <td>193.0</td>
    <td>Independence Day</td>
    <td>R. Emmerich</td>
    <td>1996.0</td>
    <td>US</td>
    <td>5606839.0</td>
  </tr>
  <tr>
    <td>194.0</td>
    <td>Quai des Orfèvres</td>
    <td>H.G. Clouzot</td>
    <td>1947.0</td>
    <td>FR</td>
    <td>5582579.0</td>
  </tr>
  <tr>
    <td>195.0</td>
    <td>La Folie des grandeurs</td>
    <td>G. Oury</td>
    <td>1971.0</td>
    <td>FR/DE/ES</td>
    <td>5568547.0</td>
  </tr>
  <tr>
    <td>196.0</td>
    <td>Le Cerveau</td>
    <td>G. Oury</td>
    <td>1969.0</td>
    <td>FR/IT</td>
    <td>5548991.0</td>
  </tr>
  <tr>
    <td>197.0</td>
    <td>Vaïana, la légende du bout du monde</td>
    <td>J. Musker, R. Clements</td>
    <td>2016.0</td>
    <td>US</td>
    <td>5548902.0</td>
  </tr>
  <tr>
    <td>198.0</td>
    <td>Le Petit Baigneur</td>
    <td>R. Dhéry</td>
    <td>1968.0</td>
    <td>FR/IT</td>
    <td>5542856.0</td>
  </tr>
  <tr>
    <td>199.0</td>
    <td>Shrek le troisième</td>
    <td>C. Miller</td>
    <td>2007.0</td>
    <td>US</td>
    <td>5536365.0</td>
  </tr>
  <tr>
    <td>200.0</td>
    <td>Love Story</td>
    <td>A. Hiller</td>
    <td>1971.0</td>
    <td>US</td>
    <td>5512408.0</td>
  </tr>
  <tr>
    <td>1 AT : Autriche / AU : Australie / BE : Belgique / CH : Suisse / CZ : République Tchèque / DE : Allemagne / ES : Espagne / FR : France / GB : Royaume-Uni / IT : Italie / MX : Mexique / NZ : Nouvelle-Zélande / RU : Russie / US : Etats-Unis / ZA : Afrique du Sud.</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>2 Entrées cumulées de la sortie jusqu'au 28 décembre 2021.</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Source : CNC.</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

Et le voici après les modifications mentionnées plus haut sur OpenRefine :

<table width="600" height="400" framework="0">
<thead>
  <tr>
    <th>Rang</th>
    <th>Titre</th>
    <th>réalisateur</th>
    <th>année de sortie</th>
    <th>nationalité</th>
    <th>nombre d'entrées en millions</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>1</td>
    <td>Titanic</td>
    <td>J. Cameron</td>
    <td>1998</td>
    <td>US</td>
    <td>21798906</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Bienvenue chez les Ch'tis</td>
    <td>D. Boon</td>
    <td>2008</td>
    <td>FR</td>
    <td>20444918</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Intouchables</td>
    <td>E. Tolédano, O. Nakache</td>
    <td>2011</td>
    <td>FR</td>
    <td>19509835</td>
  </tr>
  <tr>
    <td>4</td>
    <td>La Grande Vadrouille</td>
    <td>G. Oury</td>
    <td>1966</td>
    <td>FR/GB</td>
    <td>17330139</td>
  </tr>
  <tr>
    <td>5</td>
    <td>Autant en emporte le vent</td>
    <td>V. Fleming</td>
    <td>1950</td>
    <td>US</td>
    <td>16728160</td>
  </tr>
  <tr>
    <td>6</td>
    <td>Il était une fois dans l'Ouest</td>
    <td>S. Leone</td>
    <td>1969</td>
    <td>IT</td>
    <td>14891828</td>
  </tr>
  <tr>
    <td>7</td>
    <td>Le Livre de la jungle</td>
    <td>W. Reitherman</td>
    <td>1968</td>
    <td>US</td>
    <td>14798057</td>
  </tr>
  <tr>
    <td>8</td>
    <td>Avatar</td>
    <td>J. Cameron</td>
    <td>2009</td>
    <td>US</td>
    <td>14782116</td>
  </tr>
  <tr>
    <td>9</td>
    <td>Les 101 Dalmatiens</td>
    <td>W. Disney</td>
    <td>1961</td>
    <td>US</td>
    <td>14697525</td>
  </tr>
  <tr>
    <td>10</td>
    <td>Astérix et Obélix : mission Cléopâtre</td>
    <td>A. Chabat</td>
    <td>2002</td>
    <td>FR</td>
    <td>14408347</td>
  </tr>
  <tr>
    <td>11</td>
    <td>Les Dix Commandements</td>
    <td>C.B. DeMille</td>
    <td>1958</td>
    <td>US</td>
    <td>14237371</td>
  </tr>
  <tr>
    <td>12</td>
    <td>Ben Hur</td>
    <td>W. Wyler</td>
    <td>1960</td>
    <td>US</td>
    <td>13857770</td>
  </tr>
  <tr>
    <td>13</td>
    <td>Les Visiteurs</td>
    <td>J.M. Poiré</td>
    <td>1993</td>
    <td>FR</td>
    <td>13673172</td>
  </tr>
  <tr>
    <td>14</td>
    <td>Le Pont de la rivière Kwai</td>
    <td>D. Lean</td>
    <td>1957</td>
    <td>GB</td>
    <td>13477151</td>
  </tr>
  <tr>
    <td>15</td>
    <td>Cendrillon</td>
    <td>W. Disney</td>
    <td>1950</td>
    <td>US</td>
    <td>13269623</td>
  </tr>
  <tr>
    <td>16</td>
    <td>Le Petit Monde de Don Camillo</td>
    <td>J. Duvivier</td>
    <td>1952</td>
    <td>IT/FR</td>
    <td>12791213</td>
  </tr>
  <tr>
    <td>17</td>
    <td>Les Aristochats</td>
    <td>W. Reitherman</td>
    <td>1971</td>
    <td>US</td>
    <td>12737882</td>
  </tr>
  <tr>
    <td>18</td>
    <td>Qu'est-ce qu'on a fait au bon dieu ?</td>
    <td>P. De Chauveron</td>
    <td>2014</td>
    <td>FR</td>
    <td>12356551</td>
  </tr>
  <tr>
    <td>19</td>
    <td>Le Jour le plus long</td>
    <td>Collectif</td>
    <td>1962</td>
    <td>US</td>
    <td>11930550</td>
  </tr>
  <tr>
    <td>20</td>
    <td>Le Corniaud</td>
    <td>G. Oury</td>
    <td>1965</td>
    <td>FR/IT</td>
    <td>11744912</td>
  </tr>
  <tr>
    <td>21</td>
    <td>La Belle et le clochard</td>
    <td>W. Disney</td>
    <td>1955</td>
    <td>US</td>
    <td>11253225</td>
  </tr>
  <tr>
    <td>22</td>
    <td>Le Roi lion</td>
    <td>R. Aller, R. Minkoff</td>
    <td>1994</td>
    <td>US</td>
    <td>10747322</td>
  </tr>
  <tr>
    <td>23</td>
    <td>Bambi</td>
    <td>W. Disney</td>
    <td>1948</td>
    <td>US</td>
    <td>10715149</td>
  </tr>
  <tr>
    <td>24</td>
    <td>Star Wars : Episode 7, le reveil de la force</td>
    <td>J. J. Abrams</td>
    <td>2015</td>
    <td>US</td>
    <td>10345644</td>
  </tr>
  <tr>
    <td>25</td>
    <td>Taxi 2</td>
    <td>G. Krawczyk</td>
    <td>2000</td>
    <td>FR</td>
    <td>10302954</td>
  </tr>
  <tr>
    <td>26</td>
    <td>Trois hommes et un couffin</td>
    <td>C. Serreau</td>
    <td>1985</td>
    <td>FR</td>
    <td>10251813</td>
  </tr>
  <tr>
    <td>27</td>
    <td>Les Bronzés 3 - amis pour la vie</td>
    <td>P. Leconte</td>
    <td>2006</td>
    <td>FR</td>
    <td>10229483</td>
  </tr>
  <tr>
    <td>28</td>
    <td>Les Canons de Navarone</td>
    <td>J. Lee Thompson</td>
    <td>1961</td>
    <td>US</td>
    <td>10181324</td>
  </tr>
  <tr>
    <td>29</td>
    <td>La Guerre des boutons</td>
    <td>Y. Robert</td>
    <td>1962</td>
    <td>FR</td>
    <td>10052423</td>
  </tr>
  <tr>
    <td>30</td>
    <td>Les Misérables</td>
    <td>J.P. Le Chanois, J.P. Dreyfus</td>
    <td>1958</td>
    <td>FR/IT</td>
    <td>9969086</td>
  </tr>
  <tr>
    <td>31</td>
    <td>Le Roi Lion</td>
    <td>J. Favreau</td>
    <td>2019</td>
    <td>US</td>
    <td>9848728</td>
  </tr>
  <tr>
    <td>32</td>
    <td>E.T. l'extra-terrestre</td>
    <td>S. Spielberg</td>
    <td>1982</td>
    <td>US</td>
    <td>9847614</td>
  </tr>
  <tr>
    <td>33</td>
    <td>Docteur Jivago</td>
    <td>D. Lean</td>
    <td>1966</td>
    <td>US</td>
    <td>9817737</td>
  </tr>
  <tr>
    <td>34</td>
    <td>Vingt mille lieues sous les mers</td>
    <td>R. Fleischer</td>
    <td>1955</td>
    <td>US</td>
    <td>9628014</td>
  </tr>
  <tr>
    <td>35</td>
    <td>Harry Potter à l'école des sorciers</td>
    <td>C. Colombus</td>
    <td>2001</td>
    <td>US</td>
    <td>9545909</td>
  </tr>
  <tr>
    <td>36</td>
    <td>Sous le plus grand chapiteau du monde</td>
    <td>C.B. DeMille</td>
    <td>1953</td>
    <td>US</td>
    <td>9488114</td>
  </tr>
  <tr>
    <td>37</td>
    <td>Le Monde de Nemo</td>
    <td>A. Stanton, L. Unkrich</td>
    <td>2003</td>
    <td>US</td>
    <td>9446595</td>
  </tr>
  <tr>
    <td>38</td>
    <td>Le Dîner de cons</td>
    <td>F. Veber</td>
    <td>1998</td>
    <td>FR</td>
    <td>9249770</td>
  </tr>
  <tr>
    <td>39</td>
    <td>Le Grand Bleu</td>
    <td>L. Besson</td>
    <td>1988</td>
    <td>FR</td>
    <td>9200891</td>
  </tr>
  <tr>
    <td>40</td>
    <td>L'Ours</td>
    <td>J.J. Annaud</td>
    <td>1988</td>
    <td>FR</td>
    <td>9138948</td>
  </tr>
  <tr>
    <td>41</td>
    <td>Emmanuelle</td>
    <td>J. Jaeckin</td>
    <td>1974</td>
    <td>FR</td>
    <td>8894166</td>
  </tr>
  <tr>
    <td>42</td>
    <td>Harry Potter et la chambre des secrets</td>
    <td>C. Colombus</td>
    <td>2002</td>
    <td>US</td>
    <td>8862273</td>
  </tr>
  <tr>
    <td>43</td>
    <td>La Vache et le prisonnier</td>
    <td>H. Verneuil</td>
    <td>1959</td>
    <td>FR/IT</td>
    <td>8851261</td>
  </tr>
  <tr>
    <td>44</td>
    <td>West Side Story</td>
    <td>R. Wise, J. Robbins</td>
    <td>1962</td>
    <td>US</td>
    <td>8780013</td>
  </tr>
  <tr>
    <td>45</td>
    <td>Astérix et Obélix contre César</td>
    <td>C. Zidi</td>
    <td>1999</td>
    <td>FR/DE/IT</td>
    <td>8776587</td>
  </tr>
  <tr>
    <td>46</td>
    <td>La Grande Evasion</td>
    <td>R. Walsh</td>
    <td>1963</td>
    <td>US</td>
    <td>8757609</td>
  </tr>
  <tr>
    <td>47</td>
    <td>Le Bataillon du ciel</td>
    <td>A. Esway</td>
    <td>1947</td>
    <td>FR</td>
    <td>8649752</td>
  </tr>
  <tr>
    <td>48</td>
    <td>Le Fabuleux Destin d'Amélie Poulain</td>
    <td>J.P. Jeunet</td>
    <td>2001</td>
    <td>FR/DE</td>
    <td>8527435</td>
  </tr>
  <tr>
    <td>49</td>
    <td>Les Choristes</td>
    <td>C. Barratier</td>
    <td>2004</td>
    <td>FR/CH</td>
    <td>8469922</td>
  </tr>
  <tr>
    <td>50</td>
    <td>Le Dictateur</td>
    <td>C. Chaplin</td>
    <td>1945</td>
    <td>US</td>
    <td>8406911</td>
  </tr>
  <tr>
    <td>51</td>
    <td>Pour qui sonne le glas ?</td>
    <td>S. Wood</td>
    <td>1947</td>
    <td>US</td>
    <td>8274759</td>
  </tr>
  <tr>
    <td>52</td>
    <td>Rien à déclarer</td>
    <td>D. Boon</td>
    <td>2011</td>
    <td>FR/BE</td>
    <td>8140813</td>
  </tr>
  <tr>
    <td>53</td>
    <td>Violettes impériales</td>
    <td>R. Pottier</td>
    <td>1952</td>
    <td>FR/ES</td>
    <td>8125846</td>
  </tr>
  <tr>
    <td>54</td>
    <td>Les Couloirs du temps - les visiteurs 2</td>
    <td>J.M. Poiré</td>
    <td>1998</td>
    <td>FR</td>
    <td>8039466</td>
  </tr>
  <tr>
    <td>55</td>
    <td>Le Boulanger de Valorgue</td>
    <td>H. Verneuil</td>
    <td>1953</td>
    <td>FR</td>
    <td>7889091</td>
  </tr>
  <tr>
    <td>56</td>
    <td>Un Indien dans la ville</td>
    <td>H. Palud</td>
    <td>1994</td>
    <td>FR</td>
    <td>7887974</td>
  </tr>
  <tr>
    <td>57</td>
    <td>Pinocchio</td>
    <td>W. Disney</td>
    <td>1946</td>
    <td>US</td>
    <td>7854113</td>
  </tr>
  <tr>
    <td>58</td>
    <td>L'Âge de glace 3 - le temps des dinosaures</td>
    <td>C. Saldanha</td>
    <td>2009</td>
    <td>US</td>
    <td>7836584</td>
  </tr>
  <tr>
    <td>59</td>
    <td>Star Wars : épisode 1 - la menace fantôme</td>
    <td>G. Lucas</td>
    <td>1999</td>
    <td>US</td>
    <td>7835365</td>
  </tr>
  <tr>
    <td>60</td>
    <td>Tarzan</td>
    <td>C. Buck, K. Lima</td>
    <td>1999</td>
    <td>US</td>
    <td>7822887</td>
  </tr>
  <tr>
    <td>61</td>
    <td>Le Gendarme de Saint-Tropez</td>
    <td>J. Girault</td>
    <td>1964</td>
    <td>FR/IT</td>
    <td>7811393</td>
  </tr>
  <tr>
    <td>62</td>
    <td>Le Comte de Monte Cristo</td>
    <td>R. Vernay</td>
    <td>1955</td>
    <td>FR/IT</td>
    <td>7780963</td>
  </tr>
  <tr>
    <td>63</td>
    <td>Sixième Sens</td>
    <td>M. Night Shyamalan</td>
    <td>2000</td>
    <td>US</td>
    <td>7743424</td>
  </tr>
  <tr>
    <td>64</td>
    <td>Ratatouille</td>
    <td>B. Bird, J. Pinkava</td>
    <td>2007</td>
    <td>US</td>
    <td>7727621</td>
  </tr>
  <tr>
    <td>65</td>
    <td>Le Cinquième Elément</td>
    <td>L. Besson</td>
    <td>1997</td>
    <td>FR</td>
    <td>7713105</td>
  </tr>
  <tr>
    <td>66</td>
    <td>Harry Potter et la coupe de feu</td>
    <td>M. Newell</td>
    <td>2005</td>
    <td>GB</td>
    <td>7712423</td>
  </tr>
  <tr>
    <td>67</td>
    <td>la famille Bélier</td>
    <td>É. Lartigau</td>
    <td>2014</td>
    <td>FR</td>
    <td>7704036</td>
  </tr>
  <tr>
    <td>68</td>
    <td>Orange mécanique</td>
    <td>S. Kubrick</td>
    <td>1972</td>
    <td>GB</td>
    <td>7629804</td>
  </tr>
  <tr>
    <td>69</td>
    <td>La Reine des neiges 2</td>
    <td>C. Buck, J. Lee</td>
    <td>2019</td>
    <td>US</td>
    <td>7527360</td>
  </tr>
  <tr>
    <td>70</td>
    <td>Les Bidasses en folie</td>
    <td>C. Zidi</td>
    <td>1971</td>
    <td>FR</td>
    <td>7460911</td>
  </tr>
  <tr>
    <td>71</td>
    <td>Le Retour de Don Camillo</td>
    <td>J. Duvivier</td>
    <td>1953</td>
    <td>IT/FR</td>
    <td>7425550</td>
  </tr>
  <tr>
    <td>72</td>
    <td>Le Seigneur des anneaux - le retour du roi</td>
    <td>P. Jackson</td>
    <td>2003</td>
    <td>NZ</td>
    <td>7423673</td>
  </tr>
  <tr>
    <td>73</td>
    <td>La Vérité si je mens 2</td>
    <td>T. Gilou</td>
    <td>2001</td>
    <td>FR</td>
    <td>7407982</td>
  </tr>
  <tr>
    <td>74</td>
    <td>Jour de fête</td>
    <td>J. Tati</td>
    <td>1949</td>
    <td>FR</td>
    <td>7402939</td>
  </tr>
  <tr>
    <td>75</td>
    <td>Aladdin</td>
    <td>J. Musker</td>
    <td>1993</td>
    <td>US</td>
    <td>7353322</td>
  </tr>
  <tr>
    <td>76</td>
    <td>Les Aventures de Peter Pan</td>
    <td>W. Disney</td>
    <td>1953</td>
    <td>US</td>
    <td>7347176</td>
  </tr>
  <tr>
    <td>77</td>
    <td>Les Aventures de Rabbi Jacob</td>
    <td>G. Oury</td>
    <td>1973</td>
    <td>FR/IT</td>
    <td>7307118</td>
  </tr>
  <tr>
    <td>78</td>
    <td>Danse avec les loups</td>
    <td>K. Costner</td>
    <td>1991</td>
    <td>US</td>
    <td>7281824</td>
  </tr>
  <tr>
    <td>79</td>
    <td>Les Aventures de Bernard et Bianca</td>
    <td>Collectif</td>
    <td>1977</td>
    <td>US</td>
    <td>7242381</td>
  </tr>
  <tr>
    <td>80</td>
    <td>Jean de Florette</td>
    <td>C. Berri</td>
    <td>1986</td>
    <td>FR</td>
    <td>7225184</td>
  </tr>
  <tr>
    <td>81</td>
    <td>Star Wars : épisode 3 - la revanche des Sith</td>
    <td>G. Lucas</td>
    <td>2005</td>
    <td>US</td>
    <td>7205953</td>
  </tr>
  <tr>
    <td>82</td>
    <td>Harry Potter et le prisonnier d'Azkaban</td>
    <td>A. Cuaron</td>
    <td>2004</td>
    <td>GB</td>
    <td>7152904</td>
  </tr>
  <tr>
    <td>83</td>
    <td>Shrek 2</td>
    <td>A. Adamson, V. Jenson</td>
    <td>2004</td>
    <td>US</td>
    <td>7142658</td>
  </tr>
  <tr>
    <td>84</td>
    <td>Le Seigneur des anneaux - les deux tours</td>
    <td>P. Jackson</td>
    <td>2002</td>
    <td>NZ</td>
    <td>7128603</td>
  </tr>
  <tr>
    <td>85</td>
    <td>Samson et Dalila</td>
    <td>C.B. DeMille</td>
    <td>1951</td>
    <td>US</td>
    <td>7116461</td>
  </tr>
  <tr>
    <td>86</td>
    <td>Star Wars les derniers Jedi</td>
    <td>R. Johnson</td>
    <td>2017</td>
    <td>US</td>
    <td>7094279</td>
  </tr>
  <tr>
    <td>87</td>
    <td>Jeanne d'Arc</td>
    <td>V. Fleming</td>
    <td>1949</td>
    <td>US</td>
    <td>7092805</td>
  </tr>
  <tr>
    <td>88</td>
    <td>La Chèvre</td>
    <td>F. Veber</td>
    <td>1981</td>
    <td>FR/MX</td>
    <td>7080976</td>
  </tr>
  <tr>
    <td>89</td>
    <td>Monsieur Vincent</td>
    <td>M. Cloche</td>
    <td>1947</td>
    <td>FR</td>
    <td>7057022</td>
  </tr>
  <tr>
    <td>90</td>
    <td>Les Sept Mercenaires</td>
    <td>J. Sturges</td>
    <td>1961</td>
    <td>US</td>
    <td>7044522</td>
  </tr>
  <tr>
    <td>91</td>
    <td>Le Seigneur des anneaux - la communauté de l'anneau</td>
    <td>P. Jackson</td>
    <td>2001</td>
    <td>NZ</td>
    <td>7011664</td>
  </tr>
  <tr>
    <td>92</td>
    <td>Skyfall</td>
    <td>S. Mendes</td>
    <td>2012</td>
    <td>GB</td>
    <td>7009368</td>
  </tr>
  <tr>
    <td>93</td>
    <td>Si Versailles m'était conté</td>
    <td>S. Guitry</td>
    <td>1954</td>
    <td>FR</td>
    <td>6987432</td>
  </tr>
  <tr>
    <td>94</td>
    <td>Les Grandes Vacances</td>
    <td>J. Girault</td>
    <td>1967</td>
    <td>FR/IT</td>
    <td>6987269</td>
  </tr>
  <tr>
    <td>95</td>
    <td>Le Salaire de la peur</td>
    <td>H.G. Clouzot</td>
    <td>1953</td>
    <td>FR/IT</td>
    <td>6950146</td>
  </tr>
  <tr>
    <td>96</td>
    <td>Michel Strogoff</td>
    <td>C. Gallone</td>
    <td>1956</td>
    <td>FR/IT</td>
    <td>6869247</td>
  </tr>
  <tr>
    <td>97</td>
    <td>Le Gendarme se marie</td>
    <td>J. Girault</td>
    <td>1968</td>
    <td>FR/IT</td>
    <td>6828665</td>
  </tr>
  <tr>
    <td>98</td>
    <td>Avengers : Endgame</td>
    <td>A. Russo, J. Russo</td>
    <td>2019</td>
    <td>US</td>
    <td>6825154</td>
  </tr>
  <tr>
    <td>99</td>
    <td>Le Bossu de Notre-Dame</td>
    <td>K. Wise, G. Trousdale</td>
    <td>1996</td>
    <td>US</td>
    <td>6813099</td>
  </tr>
  <tr>
    <td>100</td>
    <td>Astérix aux Jeux Olympiques</td>
    <td>F. Forestier, T. Langmann</td>
    <td>2008</td>
    <td>FR/DE/ES/IT</td>
    <td>6807835</td>
  </tr>
  <tr>
    <td>101</td>
    <td>Mission spéciale</td>
    <td>M. de Canonge</td>
    <td>1946</td>
    <td>FR</td>
    <td>6781120</td>
  </tr>
  <tr>
    <td>102</td>
    <td>Jurassic Park</td>
    <td>S. Spielberg</td>
    <td>1993</td>
    <td>US</td>
    <td>6755899</td>
  </tr>
  <tr>
    <td>103</td>
    <td>Fanfan la Tulipe</td>
    <td>Christian-Jaque</td>
    <td>1952</td>
    <td>FR/IT</td>
    <td>6737998</td>
  </tr>
  <tr>
    <td>104</td>
    <td>L'Exorciste</td>
    <td>W. Friedkin</td>
    <td>1974</td>
    <td>US</td>
    <td>6727910</td>
  </tr>
  <tr>
    <td>105</td>
    <td>Qu'est-ce qu'on a encore fait au bon dieu ?</td>
    <td>P. de Chauveron</td>
    <td>2019</td>
    <td>FR / BE</td>
    <td>6719759</td>
  </tr>
  <tr>
    <td>106</td>
    <td>Rox et Rouky</td>
    <td>A. Stevens</td>
    <td>1981</td>
    <td>US</td>
    <td>6717395</td>
  </tr>
  <tr>
    <td>107</td>
    <td>Goldfinger</td>
    <td>G. Hamilton</td>
    <td>1965</td>
    <td>GB</td>
    <td>6676568</td>
  </tr>
  <tr>
    <td>108</td>
    <td>Les Trois Frères</td>
    <td>D. Bourdon, B. Campan</td>
    <td>1995</td>
    <td>FR</td>
    <td>6671088</td>
  </tr>
  <tr>
    <td>109</td>
    <td>les Minions</td>
    <td>P. Coffin, K. Balda</td>
    <td>2015</td>
    <td>US</td>
    <td>6663465</td>
  </tr>
  <tr>
    <td>110</td>
    <td>Nous irons à Paris</td>
    <td>J. Boyer</td>
    <td>1950</td>
    <td>FR</td>
    <td>6659325</td>
  </tr>
  <tr>
    <td>111</td>
    <td>Manon des sources</td>
    <td>C. Berri</td>
    <td>1986</td>
    <td>FR</td>
    <td>6646236</td>
  </tr>
  <tr>
    <td>112</td>
    <td>l'Age de glace 4 : la dérive des continents</td>
    <td>M.Thurmeier, S. Martino</td>
    <td>2012</td>
    <td>US</td>
    <td>6642048</td>
  </tr>
  <tr>
    <td>113</td>
    <td>Sissi</td>
    <td>E. Marischka</td>
    <td>1956</td>
    <td>AT</td>
    <td>6637836</td>
  </tr>
  <tr>
    <td>114</td>
    <td>L'Age de glace 2</td>
    <td>C. Saldanha</td>
    <td>2006</td>
    <td>US</td>
    <td>6627706</td>
  </tr>
  <tr>
    <td>115</td>
    <td>Le Cercle des poètes disparus</td>
    <td>P. Weir</td>
    <td>1989</td>
    <td>US</td>
    <td>6601781</td>
  </tr>
  <tr>
    <td>116</td>
    <td>La Belle au bois dormant</td>
    <td>W. Disney</td>
    <td>1959</td>
    <td>US</td>
    <td>6592751</td>
  </tr>
  <tr>
    <td>117</td>
    <td>Harry Potter et les reliques de la mort - 2e partie</td>
    <td>D. Yates</td>
    <td>2011</td>
    <td>GB</td>
    <td>6577156</td>
  </tr>
  <tr>
    <td>118</td>
    <td>Pirates des Caraïbes - le secret du coffre maudit</td>
    <td>G. Verbinski</td>
    <td>2006</td>
    <td>US</td>
    <td>6522015</td>
  </tr>
  <tr>
    <td>119</td>
    <td>Robin des bois</td>
    <td>W. Reitherman</td>
    <td>1974</td>
    <td>US</td>
    <td>6485372</td>
  </tr>
  <tr>
    <td>120</td>
    <td>Taxi</td>
    <td>G. Pires</td>
    <td>1998</td>
    <td>FR</td>
    <td>6485260</td>
  </tr>
  <tr>
    <td>121</td>
    <td>Rain Man</td>
    <td>B. Levinson</td>
    <td>1989</td>
    <td>US</td>
    <td>6475822</td>
  </tr>
  <tr>
    <td>122</td>
    <td>La Guerre des étoiles</td>
    <td>G. Lucas</td>
    <td>1977</td>
    <td>US</td>
    <td>6460540</td>
  </tr>
  <tr>
    <td>123</td>
    <td>Sissi impératrice</td>
    <td>E. Marischka</td>
    <td>1957</td>
    <td>AT</td>
    <td>6429021</td>
  </tr>
  <tr>
    <td>124</td>
    <td>Les Aventuriers de l'arche perdue</td>
    <td>S. Spielberg</td>
    <td>1981</td>
    <td>US</td>
    <td>6404631</td>
  </tr>
  <tr>
    <td>125</td>
    <td>Tant qu'il y aura des hommes</td>
    <td>F. Zinnemann</td>
    <td>1954</td>
    <td>US</td>
    <td>6401375</td>
  </tr>
  <tr>
    <td>126</td>
    <td>Arthur et les Minimoys</td>
    <td>L. Besson</td>
    <td>2006</td>
    <td>FR</td>
    <td>6400180</td>
  </tr>
  <tr>
    <td>127</td>
    <td>La Cuisine au beurre</td>
    <td>G. Grangier</td>
    <td>1963</td>
    <td>FR/IT</td>
    <td>6397594</td>
  </tr>
  <tr>
    <td>128</td>
    <td>Spider-Man</td>
    <td>S. Raimi</td>
    <td>2002</td>
    <td>US</td>
    <td>6382266</td>
  </tr>
  <tr>
    <td>129</td>
    <td>La Symphonie pastorale</td>
    <td>J. Delannoy</td>
    <td>1946</td>
    <td>FR</td>
    <td>6373084</td>
  </tr>
  <tr>
    <td>130</td>
    <td>Ivanhoé</td>
    <td>R. Thorpe</td>
    <td>1952</td>
    <td>US</td>
    <td>6362071</td>
  </tr>
  <tr>
    <td>131</td>
    <td>Le Bon, la brute et le truand</td>
    <td>S. Leone</td>
    <td>1968</td>
    <td>IT</td>
    <td>6350067</td>
  </tr>
  <tr>
    <td>132</td>
    <td>Les Dents de la mer</td>
    <td>S. Spielberg</td>
    <td>1976</td>
    <td>US</td>
    <td>6346372</td>
  </tr>
  <tr>
    <td>133</td>
    <td>Spider-Man 3</td>
    <td>S. Raimi</td>
    <td>2007</td>
    <td>US</td>
    <td>6320882</td>
  </tr>
  <tr>
    <td>134</td>
    <td>Quo Vadis</td>
    <td>M. Le Roy</td>
    <td>1953</td>
    <td>US</td>
    <td>6305624</td>
  </tr>
  <tr>
    <td>135</td>
    <td>La Gloire de mon père</td>
    <td>Y. Robert</td>
    <td>1990</td>
    <td>FR</td>
    <td>6298736</td>
  </tr>
  <tr>
    <td>136</td>
    <td>Le Gendarme et les extra-terrestres</td>
    <td>J. Girault</td>
    <td>1979</td>
    <td>FR</td>
    <td>6280079</td>
  </tr>
  <tr>
    <td>137</td>
    <td>Indiana Jones et la dernière croisade</td>
    <td>S. Spielberg</td>
    <td>1989</td>
    <td>US</td>
    <td>6256297</td>
  </tr>
  <tr>
    <td>138</td>
    <td>Harry Potter et l'ordre du Phénix</td>
    <td>D. Yates</td>
    <td>2007</td>
    <td>GB</td>
    <td>6219499</td>
  </tr>
  <tr>
    <td>139</td>
    <td>Marche à l'ombre</td>
    <td>M. Blanc</td>
    <td>1984</td>
    <td>FR</td>
    <td>6168425</td>
  </tr>
  <tr>
    <td>140</td>
    <td>Pas si bête</td>
    <td>A. Berthomieu</td>
    <td>1946</td>
    <td>FR</td>
    <td>6165419</td>
  </tr>
  <tr>
    <td>141</td>
    <td>Merlin l'enchanteur</td>
    <td>W. Reitherman</td>
    <td>1964</td>
    <td>US</td>
    <td>6160500</td>
  </tr>
  <tr>
    <td>142</td>
    <td>La Chartreuse de Parme</td>
    <td>Christian-Jaque</td>
    <td>1948</td>
    <td>FR</td>
    <td>6152480</td>
  </tr>
  <tr>
    <td>143</td>
    <td>Germinal</td>
    <td>C. Berri</td>
    <td>1993</td>
    <td>FR/BE</td>
    <td>6149725</td>
  </tr>
  <tr>
    <td>144</td>
    <td>Harry Potter et le Prince de sang-mêlé</td>
    <td>D. Yates</td>
    <td>2009</td>
    <td>GB</td>
    <td>6140398</td>
  </tr>
  <tr>
    <td>145</td>
    <td>Le Père tranquille</td>
    <td>R. Clément</td>
    <td>1946</td>
    <td>FR</td>
    <td>6139259</td>
  </tr>
  <tr>
    <td>146</td>
    <td>Les Feux de la rampe</td>
    <td>C. Chaplin</td>
    <td>1952</td>
    <td>US</td>
    <td>6137070</td>
  </tr>
  <tr>
    <td>147</td>
    <td>Oscar</td>
    <td>E. Molinaro</td>
    <td>1967</td>
    <td>FR</td>
    <td>6123063</td>
  </tr>
  <tr>
    <td>148</td>
    <td>Taxi 3</td>
    <td>G. Krawczyk</td>
    <td>2003</td>
    <td>FR</td>
    <td>6108669</td>
  </tr>
  <tr>
    <td>149</td>
    <td>Harry Potter et les reliques de la mort - 1re partie</td>
    <td>D. Yates</td>
    <td>2010</td>
    <td>GB</td>
    <td>6102789</td>
  </tr>
  <tr>
    <td>150</td>
    <td>Star Wars : épisode 9, l'ascension de Skywalker</td>
    <td>J.J. Abrams</td>
    <td>2019</td>
    <td>US</td>
    <td>6063436</td>
  </tr>
  <tr>
    <td>151</td>
    <td>Terminator 2 - le jugement dernier</td>
    <td>J. Cameron</td>
    <td>1991</td>
    <td>US</td>
    <td>6007492</td>
  </tr>
  <tr>
    <td>152</td>
    <td>Midnight Express</td>
    <td>A. Parker</td>
    <td>1978</td>
    <td>GB</td>
    <td>5974912</td>
  </tr>
  <tr>
    <td>153</td>
    <td>Les Dieux sont tombés sur la tête</td>
    <td>J. Uys</td>
    <td>1983</td>
    <td>ZA</td>
    <td>5950116</td>
  </tr>
  <tr>
    <td>154</td>
    <td>Mourir d'aimer</td>
    <td>A. Cayatte</td>
    <td>1971</td>
    <td>FR/IT</td>
    <td>5912600</td>
  </tr>
  <tr>
    <td>155</td>
    <td>Qui veut la peau de Roger Rabbit ?</td>
    <td>R. Zemeckis</td>
    <td>1988</td>
    <td>US</td>
    <td>5909001</td>
  </tr>
  <tr>
    <td>156</td>
    <td>Crocodile Dundee</td>
    <td>P. Faiman</td>
    <td>1987</td>
    <td>AU</td>
    <td>5887982</td>
  </tr>
  <tr>
    <td>157</td>
    <td>Guerre et Paix</td>
    <td>K. Vidor</td>
    <td>1956</td>
    <td>US</td>
    <td>5885856</td>
  </tr>
  <tr>
    <td>158</td>
    <td>Les Ripoux</td>
    <td>C. Zidi</td>
    <td>1984</td>
    <td>FR</td>
    <td>5882397</td>
  </tr>
  <tr>
    <td>159</td>
    <td>L'Odyssée du Docteur Wassel</td>
    <td>C.B. DeMille</td>
    <td>1946</td>
    <td>US</td>
    <td>5866693</td>
  </tr>
  <tr>
    <td>160</td>
    <td>Rambo 2 - la mission</td>
    <td>G.P. Cosmatos</td>
    <td>1985</td>
    <td>US</td>
    <td>5851440</td>
  </tr>
  <tr>
    <td>161</td>
    <td>Le Bossu</td>
    <td>A. Hunebelle</td>
    <td>1959</td>
    <td>FR/IT</td>
    <td>5847123</td>
  </tr>
  <tr>
    <td>162</td>
    <td>L'Aile ou la Cuisse</td>
    <td>C. Zidi</td>
    <td>1976</td>
    <td>FR</td>
    <td>5843090</td>
  </tr>
  <tr>
    <td>163</td>
    <td>Les Vacances de Monsieur Hulot</td>
    <td>J. Tati</td>
    <td>1953</td>
    <td>FR</td>
    <td>5799875</td>
  </tr>
  <tr>
    <td>164</td>
    <td>Sissi face à son destin</td>
    <td>E. Marischka</td>
    <td>1958</td>
    <td>AT</td>
    <td>5794263</td>
  </tr>
  <tr>
    <td>165</td>
    <td>Quatre mariages et un enterrement</td>
    <td>M. Newell</td>
    <td>1994</td>
    <td>GB</td>
    <td>5781268</td>
  </tr>
  <tr>
    <td>166</td>
    <td>Mulan</td>
    <td>T. Bancroft, B. Cook</td>
    <td>1998</td>
    <td>US</td>
    <td>5776901</td>
  </tr>
  <tr>
    <td>167</td>
    <td>Men in Black</td>
    <td>B. Sonnenfeld</td>
    <td>1997</td>
    <td>US</td>
    <td>5759617</td>
  </tr>
  <tr>
    <td>168</td>
    <td>Le train sifflera trois fois</td>
    <td>F. Zinnemann</td>
    <td>1952</td>
    <td>US</td>
    <td>5756216</td>
  </tr>
  <tr>
    <td>169</td>
    <td>Moi, moche et méchant 3</td>
    <td>K. Balda, P. Coffin, E. Guillon</td>
    <td>2017</td>
    <td>US</td>
    <td>5746829</td>
  </tr>
  <tr>
    <td>170</td>
    <td>Grease</td>
    <td>R. Kleiser</td>
    <td>1978</td>
    <td>US</td>
    <td>5745596</td>
  </tr>
  <tr>
    <td>171</td>
    <td>Les Indestructibles 2</td>
    <td>B. Brad</td>
    <td>2018</td>
    <td>US</td>
    <td>5744813</td>
  </tr>
  <tr>
    <td>172</td>
    <td>Les Fous du stade</td>
    <td>C. Zidi</td>
    <td>1972</td>
    <td>FR</td>
    <td>5744270</td>
  </tr>
  <tr>
    <td>173</td>
    <td>Le Troisième Homme</td>
    <td>C. Reed</td>
    <td>1949</td>
    <td>GB</td>
    <td>5742569</td>
  </tr>
  <tr>
    <td>174</td>
    <td>Opération tonnerre</td>
    <td>T. Young</td>
    <td>1965</td>
    <td>GB</td>
    <td>5735506</td>
  </tr>
  <tr>
    <td>175</td>
    <td>Andalousie</td>
    <td>R. Vernay</td>
    <td>1951</td>
    <td>FR/ES</td>
    <td>5735108</td>
  </tr>
  <tr>
    <td>176</td>
    <td>Les Anges gardiens</td>
    <td>J.M. Poiré</td>
    <td>1995</td>
    <td>FR</td>
    <td>5734326</td>
  </tr>
  <tr>
    <td>177</td>
    <td>Les Valseuses</td>
    <td>B. Blier</td>
    <td>1974</td>
    <td>FR</td>
    <td>5729042</td>
  </tr>
  <tr>
    <td>178</td>
    <td>La Bataille du rail</td>
    <td>R. Clément</td>
    <td>1946</td>
    <td>FR</td>
    <td>5727974</td>
  </tr>
  <tr>
    <td>179</td>
    <td>Lawrence d'Arabie</td>
    <td>D. Lean</td>
    <td>1963</td>
    <td>GB</td>
    <td>5718291</td>
  </tr>
  <tr>
    <td>180</td>
    <td>A nous les petites Anglaises</td>
    <td>M. Lang</td>
    <td>1976</td>
    <td>FR</td>
    <td>5704446</td>
  </tr>
  <tr>
    <td>181</td>
    <td>La Vérité</td>
    <td>H.G. Clouzot</td>
    <td>1960</td>
    <td>FR/IT</td>
    <td>5701210</td>
  </tr>
  <tr>
    <td>182</td>
    <td>Notre-Dame de Paris</td>
    <td>J. Delannoy</td>
    <td>1956</td>
    <td>FR/IT</td>
    <td>5700102</td>
  </tr>
  <tr>
    <td>183</td>
    <td>Indiana Jones et le temple maudit</td>
    <td>S. Spielberg</td>
    <td>1984</td>
    <td>US</td>
    <td>5690878</td>
  </tr>
  <tr>
    <td>184</td>
    <td>Les Tuche 3</td>
    <td>O. Baroux</td>
    <td>2018</td>
    <td>FR</td>
    <td>5687833</td>
  </tr>
  <tr>
    <td>185</td>
    <td>Matrix Reloaded</td>
    <td>L. Wachowski, A. Wachowski</td>
    <td>2003</td>
    <td>US</td>
    <td>5672070</td>
  </tr>
  <tr>
    <td>186</td>
    <td>Pirates des Caraïbes - jusqu'au bout du monde</td>
    <td>G. Verbinski</td>
    <td>2007</td>
    <td>US</td>
    <td>5639260</td>
  </tr>
  <tr>
    <td>187</td>
    <td>Pocahontas, une légende indienne</td>
    <td>M. Gabriel, E. Goldberg</td>
    <td>1995</td>
    <td>US</td>
    <td>5634513</td>
  </tr>
  <tr>
    <td>188</td>
    <td>La Ch'tite Famille</td>
    <td>D. Boon</td>
    <td>2018</td>
    <td>FR</td>
    <td>5630428</td>
  </tr>
  <tr>
    <td>189</td>
    <td>Bons baisers de Russie</td>
    <td>T. Young</td>
    <td>1964</td>
    <td>GB</td>
    <td>5625125</td>
  </tr>
  <tr>
    <td>190</td>
    <td>Star Wars : épisode 2 - l'attaque des clones</td>
    <td>G. Lucas</td>
    <td>2002</td>
    <td>US</td>
    <td>5624277</td>
  </tr>
  <tr>
    <td>191</td>
    <td>Le Petit Nicolas</td>
    <td>L. Tirard</td>
    <td>2009</td>
    <td>FR/BE</td>
    <td>5616187</td>
  </tr>
  <tr>
    <td>192</td>
    <td>Joker</td>
    <td>T. Phillips</td>
    <td>2019</td>
    <td>US</td>
    <td>5611793</td>
  </tr>
  <tr>
    <td>193</td>
    <td>Independence Day</td>
    <td>R. Emmerich</td>
    <td>1996</td>
    <td>US</td>
    <td>5606839</td>
  </tr>
  <tr>
    <td>194</td>
    <td>Quai des Orfèvres</td>
    <td>H.G. Clouzot</td>
    <td>1947</td>
    <td>FR</td>
    <td>5582579</td>
  </tr>
  <tr>
    <td>195</td>
    <td>La Folie des grandeurs</td>
    <td>G. Oury</td>
    <td>1971</td>
    <td>FR/DE/ES</td>
    <td>5568547</td>
  </tr>
  <tr>
    <td>196</td>
    <td>Le Cerveau</td>
    <td>G. Oury</td>
    <td>1969</td>
    <td>FR/IT</td>
    <td>5548991</td>
  </tr>
  <tr>
    <td>197</td>
    <td>Vaïana, la légende du bout du monde</td>
    <td>J. Musker, R. Clements</td>
    <td>2016</td>
    <td>US</td>
    <td>5548902</td>
  </tr>
  <tr>
    <td>198</td>
    <td>Le Petit Baigneur</td>
    <td>R. Dhéry</td>
    <td>1968</td>
    <td>FR/IT</td>
    <td>5542856</td>
  </tr>
  <tr>
    <td>199</td>
    <td>Shrek le troisième</td>
    <td>C. Miller</td>
    <td>2007</td>
    <td>US</td>
    <td>5536365</td>
  </tr>
  <tr>
    <td>200</td>
    <td>Love Story</td>
    <td>A. Hiller</td>
    <td>1971</td>
    <td>US</td>
    <td>5512408</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>1971</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>1971</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>1971</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>1971</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>


**2) Visualisations**

**A. Scatter plot des scores réalisés par les films les plus populaires au cinéma en France de 1945 à 2021** 

Sur ce visuel dynamique, les films du jeu de données sont représentés par une étoile. On peut avoir accès à leur année de sortie ainsi qu'à leur nombre d'entrées réalisées en passant par dessus avec le curseur. Ce visuel représente un excellent moyen de voir les films qui se détachent nettement des autres par leur performance en terme de chiffres, comme par exemple le film _Titanic_, tout en haut du graphique, avec 21 798 906 entrées.
<iframe src='https://public.flourish.studio/visualisation/12691863/embed' title='Score réalisés par les films les plus populaires au cinéma en France de 1945 à 2021' frameborder='0' scrolling='no' style='width:100%;height:600px;'></iframe>

**B. Pie charts: Répartition par année des plus gros succès et de leur chiffres au box office** 
   
Ce visuel présente l'intérêt majeur de permettre un regard plus précis sur les données, en proposant une vision de l'année au choix, mais également des films et de leurs nombres d'entrées.
<iframe src='https://public.flourish.studio/visualisation/12692271/embed' title='Répartition par année des plus gros succès et de leur chiffres au box office' frameborder='0' scrolling='no' style='width:600;height:450px;'></iframe>

**C. Circle hierarchy - Vision globale des réalisateurs et des performances de leurs films dans les salles françaises** 

Comme pour le visuel précédent, cette hiérarchie de cercles laisse le choix de consultation de la cellule au choix, cette fois pour les réalisateurs; nous obtenons ainsi une vue claire de leurs films ainsi que des chiffres réalisés. La vision élargie de tous les cercles permet aussi de constater les noms qui prennent le dessus sur les autres, comme ceux de Walt Disney ou de Steven Spielberg. En zoomant sur leurs cercles, on se rend compte qu'ils ont respectivement sept et six films s'étant classés parmi les 200 films les plus vus au cinéma en France depuis 1945, mais aussi que chacun de leurs films ont dépassé la barre des 5 millions d'entrées.
<iframe src='https://public.flourish.studio/visualisation/12706313/embed' title= 'Vision globale des réalisateurs et des performances de leurs films dans les salles françaises' frameborder='0' scrolling='yes' style='width:100%;height:800px;'></iframe>
  
**D. Le Cinéma Français à l'international avec Wikidata Query Service**
   
L'analyse de ces données laisse clairement transparaître l'enthousiasme des français pour le grand écran, tant du côté des spectateurs que de celui des créateurs. Cependant, elle soulève également d'autres questions. On pourrait par exemple se demander ce qu'il en est du succès - ou non - du cinéma français contemporain à l'international, en comparaison avec les autres pays. Pour obtenir des données pertinentes à ce sujet, il a fallu interroger la base de données Wikidata. J'ai formulé la requête suivante :
```SPARQL

#création de colonnes qui renseignent : le pays d'origine, les chiffres au box office, ainsi que les noms de ces films
SELECT DISTINCT ?item ?origincountry ?boxoffice ?name  WHERE {
  ?item rdfs:label ?name;
        wdt:P31 wd:Q11424; #déclaration des titres comme étant de nature "film"  
        wdt:P577 ?publication_date; #indication de leur date de publication
        wdt:P2142 ?boxoffice. #indication de leurs chiffres au box office
  OPTIONAL {
    ?item wdt:P495 ?Qorigincountry. 
    ?Qorigincountry rdfs:label ?origincountry. #affichage du nom du pays d'origine en français
    FILTER((LANG(?origincountry)) = "fr")   
  }       
  
  FILTER(xsd:date(?publication_date) > "2022-01-01"^^xsd:date) 
  FILTER ( lang(?name) = "fr")
 }
ORDER BY ?boxoffice #limitation de la requête aux films sortis depuis le début de l'année 2022, dont on veut le titre en français

```
J'ai ainsi pu obtenir le résultat suivant :
<iframe style="width: 80vw; height: 70vh; border: none;" src="https://query.wikidata.org/embed.html#%23%20cr%C3%A9ation%20de%20colonnes%20qui%20renseignent%20%3A%20le%20pays%20d%27origine%2C%20les%20chiffres%20au%20box%20office%2C%20ainsi%20que%20les%20noms%20de%20ces%20films%0ASELECT%20DISTINCT%20%3Fitem%20%3Forigincountry%20%3Fboxoffice%20%3Fname%20%20WHERE%20%7B%0A%20%20%3Fitem%20rdfs%3Alabel%20%3Fname%3B%0A%20%20%20%20%20%20%20%20wdt%3AP31%20wd%3AQ11424%3B%20%23%20d%C3%A9claration%20des%20titres%20comme%20%C3%A9tant%20de%20nature%20%22film%22%0A%20%20%20%20%20%20%20%20wdt%3AP577%20%3Fpublication_date%3B%20%23%20indication%20de%20leur%20date%20de%20publication%0A%20%20%20%20%20%20%20%20wdt%3AP2142%20%3Fboxoffice.%20%23%20indication%20de%20leurs%20chiffres%20au%20box%20office%0A%20%20OPTIONAL%20%7B%0A%20%20%20%20%3Fitem%20wdt%3AP495%20%3FQorigincountry.%20%23%20affichage%20du%20nom%20du%20pays%20d%27origine%0A%20%20%20%20%3FQorigincountry%20rdfs%3Alabel%20%3Forigincountry.%0A%20%20%20%20FILTER%28%28LANG%28%3Forigincountry%29%29%20%3D%20%22fr%22%29%20%23%20en%20fran%C3%A7ais%20%20%0A%20%20%7D%0A%23%20limitation%20de%20la%20requ%C3%AAte%20aux%20films%20sortis%20depuis%20le%20d%C3%A9but%20de%20l%27ann%C3%A9e%202022%2C%20dont%20on%20veut%20le%20titre%20en%20fran%C3%A7ais%20%20%20%20%20%20%20%20%0A%20%20FILTER%28xsd%3Adate%28%3Fpublication_date%29%20%3E%20%222022-01-01%22%5E%5Exsd%3Adate%29%0A%20%20FILTER%20%28%20lang%28%3Fname%29%20%3D%20%22fr%22%29%0A%20%7D%0AORDER%20BY%20%3Fboxoffice%20%23%20classement%20par%20chiffre%20r%C3%A9alis%C3%A9%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

Le visuel le plus intéressant qu'offre ce résultat est le bar chart. Cette visualisation laisse transparaître la dominance écrasante des Etats-Unis sur le marché du cinéma, dont les recettes totales des films de 2022 au box office s'élèvent à plus de 22 milliards de dollars. Le box office des films français se classe néanmoins à la cinquième place ; mais avec une différence abyssale, en s'élevant à moins d'un milliard de dollars. Après étude de cette visualisation, on peut émettre certaines hypothèses ; en effet, les pays qui sont avant la France au classement sont les Etats-Unis, le Royaume-Uni, la Chine et l'Australie. Trois d'entre eux ont la même langue, l'anglais, qui est la deuxième la plus parlée au monde, tandis que le chinois est la langue la plus parlée au monde. Ce facteur explique assurément les succès des films de ces pays.

**Conclusion**

Ce projet a été intéressant bien que chronophage et complexe. L'analyse de ces données fût enrichissante en ce qu'elle a été l'occasion de se rendre compte de la conséquence du marché du cinéma. Il engage des chiffres astronomiques, qu'il s'agisse des recettes, qui se comptent en milliards, ou des fréquentations des salles, rien que sur l'échelle d'un seul pays comme la France.

[^1]: [Wikipédia](https://fr.wikipedia.org/wiki/Cin%C3%A9ma_fran%C3%A7ais#Exploitation)

