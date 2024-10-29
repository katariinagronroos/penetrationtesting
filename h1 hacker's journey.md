Ao. vastaukset ovat osa kotitehtävää h1 hacker's journey Haaga-Helian tunkeutumistestaus-kurssilla, jota opettaa Tero Karvinen. Harjoituksia tehtiin 27.10 ja 29.10 VirtualBox VM, jossa asennettuna Kali Linux. Kalissa 6 GB muistia ja 20GB tilaa.

Harjoituksen tehtävänannot löytyvät osoitteesta https://terokarvinen.com/tunkeutumistestaus/.

### x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

### Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains, chapters Abstract, 3.2 Intrusion Kill Chain.

- Intrusion Kill Chain tai Cyber Kill Chain on Lockheed Martinin kehittämä 7-osainen prosessi, jossa kuvataan tietojärjestelmiin tunkeutumista vaihe vaiheelta. Mikäli jokin vaihe epäonnistuu, koko yritys epäonnistuu.
- Tausta USAn armeijan toiminnassa, muokattu tietojärjestelmille sopivaksi
- Reconnaissance, weaponization, delivery, Exploitation, Installation, Command and Control (C2), Actions on Objectives

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
Asensin apache2 ja nanon, ja tämän jälkeen skannasin uusiksi.

![image](https://github.com/user-attachments/assets/87fdfe1b-fc5c-4693-b11c-96870a287f2e)

Tässä ei nyt näytä olevan eroja mitä analysoida, joten jotain on luultavimmin väärin. Palaan tähän myöhemmin.

### e) Asenna Metasploitable 2 virtuaalikoneeseen

Asensin Metasploitable 2 osoitteesta https://sourceforge.net/projects/metasploitable/files/latest/download.
Noudatin Valkamon ohjeita(https://tuomasvalkamo.com/PenTestCourse/week-2/) asennuksessa, purin tiedoston ja lisäsin tämän Virtualboxiin.


### f) Tee koneiden välille virtuaaliverkko.

Tein koneiden välille virtuaaliverkon niin, että 

Muokkasin verkkoasetuksia ohjeistuksen mukaan niin, että sallin DHCP serverin. 

![image](https://github.com/user-attachments/assets/1e84b50e-e6e3-4f3e-a952-aa5801b4dd04)


Muokkasin Metasploitablen asetuksia niin, että vaihdoin network adapterin Natista luomaani Host only#2.

![image](https://github.com/user-attachments/assets/029ec522-3557-4288-a8b8-b442b4ca16bf)

Tämän jälkeen muokkasin Kalin verkkoasetuksia niin, että lisäsin kyseisen verkon  adapter 2 kohtaan.
## Lähteet

Karvinen 2024: Tunkeutumistestaus. Luettavissa: 

https://terokarvinen.com/tunkeutumistestaus/ Luettu 27.10.2024

KKO KKO:2003:36, 2003. Luettavissa:

https://finlex.fi/fi/oikeus/kko/kko/2003/20030036 Luettu 27.10.2024

https://www.kali.org/docs/virtualization/import-premade-virtualbox/ Luettu 27.10.2024

Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains Luettavissa:

https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf Luettu 27.10.2024

Kali. Luettavissa:

https://www.kali.org/get-kali/#kali-live Luettu 27.10.2024

Luettavissa: 

https://sourceforge.net/projects/metasploitable/files/latest/download Luettu 29.10.2024

Valkamo 2022: Hacking into a Target Using Metasploit. Luettavissa:

https://tuomasvalkamo.com/PenTestCourse/week-2/ Luettu 29.10.2024
