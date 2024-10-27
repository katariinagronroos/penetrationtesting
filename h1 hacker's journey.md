Ao. vastaukset ovat osa kotitehtävää h1 hacker's journey Haaga-Helian tunkeutumistestaus-kurssilla, jota opettaa Tero Karvinen. Harjoituksia tehtiin 27.10 ja __ kotona omalla tietokoneella Lenovo Yoga Slim 7 14ARE05. Hyödynsin tehtävissä virtuaalikoneita ja Oracle vm Virtualbox-alustaa. 

Harjoituksen tehtävänannot löytyvät osoitteesta https://terokarvinen.com/tunkeutumistestaus/.

### x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

### Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains, chapters Abstract, 3.2 Intrusion Kill Chain.
-
-
-

###  KKO:2003:36
-KKO:2003:36 on Korkeimman Oikeuden ennakkopäätös vuodelta 2003, jossa käsiteltiin tekijän A syytettä tietomurron yrityksestä.
-
-

### a) Asenna Kali virtuaalikoneeseen. (Jos asennuksessa ei ole mitään ongelmia tai olet asentanut jo aiemmin, tarkkaa raporttia tästä alakohdasta ei tarvita. Kerro silloin kuitenkin, mikä versio ja millä asennustavalla. Jos on ongelmia, niin tarkka ja toistettava raportti).

Asensin virtualboxin virtuaalikoneeseen Kalin live-version 2024.3 (kali-linux-2024.3-live-AMD64.iso).
Ensiksi testasin live-versiota,ja tämän jälkeen asensin koko käyttöjärjestelmän koneelle. 

Tämän jälkeen huomasin, että Kalin sivuilla oli myös tälläisiä "Pre-Made Kali VirtualBox VM", joten poistin manuaalisesti asentamani Kalin ja halusin testata tälläisen valmiin asennusta.
Luin tämän manuaalia (https://www.kali.org/docs/virtualization/import-premade-virtualbox/) 

Asensin Kalin kuitenkin myös manuaalisesti uusiksi. 
Näissä ei ollut ongelmia, joten tästä ei ole enempää raportoitavaa.

### b) Irrota Kali-virtuaalikone verkosta. Todista testein, että kone ei saa yhteyttä Internetiin (esim. 'ping 8.8.8.8')

Ensin testasin verkkoyhteyden ping-komennolla, ennenkuin olin irrottanut koneen verkosta. Näytti toimivan, ja paketteja siirtyi. Tämän jälkeen irrotin Kalini verkosta virtualboxin asetuksista, eikä ping-komennolle tullut enää vastausta. Oli siis irroitettu netistä.

"--- 8.8.8.8 ping statistics ---
339 packets transmitted, 0 received, 100% packet loss, time 353002ms"


![image](https://github.com/user-attachments/assets/7521caca-cf0d-4704-8ea0-6f6f80607a0e)


### c) Porttiskannaa 1000 tavallisinta tcp-porttia omasta koneestasi (nmap -A localhost). Analysoi tulokset.
 
Porttiskannasin 1000 tavallista tcp-porttia nmap -A localhost komennolla. Koska olin irrottanut koneen verkosta, oli tuloksena se, localhost oli aktiivinen, mutta DNS-palvelimia ei löytynyt. 
"All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.
Not shown: 1000 closed tcp ports (conn-refused)"


![image](https://github.com/user-attachments/assets/f103156b-7655-42aa-9e94-d5f3e0093592)


### d) Asenna kaksi vapaavalintaista demonia ja skannaa uudelleen. Analysoi ja selitä erot.

Asentaakseni demoneja, täytyi kone yhdistää takaisin nettiin. 

## Lähteet

Karvinen, Tero 2024: Tunkeutumistestaus. Luettavissa: 

https://terokarvinen.com/tunkeutumistestaus/ Luettu 27.10.2024

KKO KKO:2003:36, 2003. Luettavissa:

https://finlex.fi/fi/oikeus/kko/kko/2003/20030036 Luettu 27.10.2024

https://www.kali.org/docs/virtualization/import-premade-virtualbox/ Luettu 27.10.2024

Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains Luettavissa:

https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf Luettu 27.10.2024

Kali. Luettavissa:

https://www.kali.org/get-kali/#kali-live Luettu 27.10.2024
