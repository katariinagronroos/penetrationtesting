Jatkan overthewirea;

## Bandit Level 4 → Level 5

![image](https://github.com/user-attachments/assets/1fade91c-444d-42f6-b7db-98e7b0fdaf7d)

![image](https://github.com/user-attachments/assets/ba2b3a56-2ea9-4aef-9011-c45cd79d4507)

käytiin tiedostoja läpi yksitellen siihen asti että luettava tiedosto löytyy; bingo.
Tähän oletettavasti olisi joku helpompikin tapa, jos tiedostoja olisikin 10 sijasta vaikka 100, niin ei näitä jaksa käydä läpi millään yksitellen.
Etsin tietoa sopivasta komennosta verkosta, ja löydän overthewire banditin walkthroughn sivulta https://mayadevbe.me/posts/overthewire/bandit/level5/, jossa käydään asiaa läpi, ja tässä mainitaan file-komento, joka on minulle uusi.

![image](https://github.com/user-attachments/assets/c3baea9d-79a1-4b41-be89-1a2367538f2a)

eli `file ./`-komennolla saadaan printattua tiedostojen tyyppejä

--

![image](https://github.com/user-attachments/assets/8ae327b8-eafd-4289-ba6c-7b54cd80f34d)

Käyn näitä läpi yksitellen, ja koitan löytää annettuihin spekseihin sopivaa tiedostoa, mutta tässä alkaa olemaan jo manuaalisesti aika iso homma. 
Katson siis walkthroughsta https://mayadevbe.me/posts/overthewire/bandit/level6/ taas vinkkiä sopivaan komentoon ja parametreihin, ja opinkin tästä uutta;

Kun olen directoryssa, voin komennolla `ls -la [tiedostonnimi]` katsoa tietoja avaamatta jokaista aina yksitellen

![image](https://github.com/user-attachments/assets/7c9666f8-0e9b-4b79-9399-e31ed355fa55)

Komennolla `file */{.,}*` näen kaikkien tietoja listattuna suorilteen, joten ei tarvitse käydä kaikkia läpi yksitellen: 

![image](https://github.com/user-attachments/assets/97a89ac2-d270-4bff-9459-d2f8316018a7)

Täältä löytyy yksi kiinnostavan oloinen tiedosto, jota ei ole listattu erikseen että sisältäisi montaa riviä, joten salasana luultavimmin olisi täällä?
Mutta tarkemmin katsottuna tämä ei ole sopivan kokoinen, koon pitäisi olla 1033 bytes mutta tämä näyttää olevan 99, joten liian pieni.

 ![image](https://github.com/user-attachments/assets/c750b239-f34a-4d0c-b90c-f6d76340b1e4)

Tutkitaan.


## Lähteet:

https://mayadevbe.me/posts/overthewire/bandit/level5/
https://mayadevbe.me/posts/overthewire/bandit/level6/
