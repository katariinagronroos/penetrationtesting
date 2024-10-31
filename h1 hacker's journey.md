Ao. vastaukset ovat osa kotitehtävää h1 hacker's journey Haaga-Helian tunkeutumistestaus-kurssilla, jota opettaa Tero Karvinen. Harjoituksia tehtiin 27.10, 29.10 ja 30.10. VirtualBox VM-alustalla, jossa asennettuna Kali Linux ja Metasploit 2. Kalissa 6 GB muistia ja 20GB tilaa.

Harjoituksen tehtävänannot löytyvät osoitteesta https://terokarvinen.com/tunkeutumistestaus/.

### x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

### Herrasmieshakkerit (RSS) tai Darknet Diaries (RSS) , yksi vapaavalintainen jakso jommasta kummasta.

Kuuntelin Herrasmieshakkereiden toiseksi uusimman jakson Case Vastaamo, vieraana Marko Leponiemi 0x33. Tässä rikosylikomisaario Marko Leponen oli kertomassa Vastaamon tietomurtotapauksen tutkinnasta poliisin näkökulmasta. Tästä mieleen jäivät seuraavat asiat; 
- todistusaineiston(palvelimia, palvelinkuvia) valtava määrä; 1 betatavu, eli tuhat teratavua. KRPn tutkintamateriaaleja ei saa säilöä pilvessä, joten ollut oma hommansa keksiä mihin tuollaisen määrän dataa saa ylipäätään talletettua, saati läpikäytyä.
- tutkinnassa auttanut vahingossa vuodettu tar(tape archive)-tiedosto, joka oli yksi keskeinen asia. Tar tiedostoformaattina sellainen, että vain palasesta saa selville tiedoston ensimmäisiä rivejä. Eli jos 11 GB tiedostosta saadaan vain megatavu, pystyy näkemään mitkä tiedoston ensimmäiset rivit ovat. Tässä oli linkkejä eteenpäin, ip-osoitteita jota pystyttiin seuraamaan yms.
- virtualivaluutta Moneron lohkoketjun selvitys, joka oli ollut poikkeuksellinen prosessi ihan maailmanlaajuisesti. 

### Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains, chapters Abstract, 3.2 Intrusion Kill Chain.

- Intrusion Kill Chain tai Cyber Kill Chain on Lockheed Martinin kehittämä 7-osainen prosessi, jossa kuvataan tietojärjestelmiin tunkeutumista vaihe vaiheelta. Mikäli jokin vaihe epäonnistuu, koko yritys epäonnistuu.
- Tausta USAn armeijan toiminnassa, muokattu tietojärjestelmille sopivaksi
- Kill Chainin osa-alueet ovat: Reconnaissance, weaponization, delivery, Exploitation, Installation, Command and Control (C2), Actions on Objectives

### € Santos et al: The Art of Hacking (Video Collection): 4.3 Surveying Essential Tools for Active Reconnaissance.
- Videoilla esitellään active reconnaissancea(aktiivista tiedustelua), ja tämän työkaluja. 
- Alussa kerrotaan aktiivisen ja passiivisen tiedustelun eroja; siinä missä passiivinen tiedustelu ei jätä jälkiä, aktiivisessa lähetään dataa vastaanottajan verkkoon, jolloin tästä jää jälki lokeihin, jonka voi nähdä näistä lokeista.
- Aktiiviseen tiedustelun metodeja ovat porttiskannaus (port scanning), web service review ja vulnerability scanning (haavoittuvuusskannaus?)
- Videolla esitellään kahta TCP-skanneria(Nmap, MAssScan), ja tämän lisäksi UDP-protokrollaskanneria. Näistä Nmap suosituin ja monipuolisin porttiskanneri, kun taas MassScan on nopein skanneri, jolla voi skannata esim koko internetin laajuisesti ihan hetkessä.
- Videolla suositellaan seuraavia nmapin parametreja;
o	-p <port ranges>, voi skannata vain tietyn portin
- Videossa hyödynnetään web service reviewihin Eyewitness-ohjelmaa, jonka avulla saa avoimista porteista ja näihin liittyvistä verkkosivuista lisätietoa, jolloin voi päätellä mihin tulisi hyökätä (ohjelma ottaa snapshotteja, joiden avulla näkyy tarkemmin millainen sivu on käytännössä).
- Toisessa videossa käydään läpi network vulnerability skannereita(esim OpenVAS, Nessus) ja web vulnerability skannereita(esim Nikto,  WPScan). Nmapilla voi myös vulnerability skannata rajoitetusti. Videolla demotaan yhden haavoittuvuuden skannausta nmapilla.


###  KKO:2003:36

- KKO:2003:36 on Korkeimman Oikeuden ennakkopäätös vuodelta 2003, jossa käsiteltiin tekijän A syytettä tietomurron yrityksestä pankin tietojärjestelmään.
- Rikos oli tapahtunut vuonna 1998, kun tuolloin 17-vuotias syytetty oli porttiskannannut osuuskunnan nettiin yhteydessä olevat verkon osoitteet tarkoituksena löytää avoimia portteja joiden kautta murtautua tietojärjestelmään.
- Avoimia portteja ei ollut ollut, eikä täten murtautumista ollut tapahtunut, mutta syyte perustui siihen, että mikäli näitä olisi ollut, olisi myös tietomurto toteutettu.
- Tekijä tuomittu kymmenien tuhansien markkojen sakkoihin ja vahingonkorvauksiin.

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

1000 tavallisinta tcp-porttia ovat "ignored" tilassa, ja myöskin "1000 closed tcp-ports", eli kaikki portit kiinni niinkuin kuuluisikin?

![image](https://github.com/user-attachments/assets/f103156b-7655-42aa-9e94-d5f3e0093592)


### d) Asenna kaksi vapaavalintaista demonia ja skannaa uudelleen. Analysoi ja selitä erot.

Asentaakseni demoneja, täytyi kone yhdistää takaisin nettiin. 
Asensin apache2 ja openssh-serverin, ja tämän jälkeen skannasin uusiksi.

![image](https://github.com/user-attachments/assets/87fdfe1b-fc5c-4693-b11c-96870a287f2e)

Tässä ei nyt näytä olevan eroja mitä analysoida, joten jotain on luultavimmin väärin. Palaan tähän myöhemmin. // edit 29.10.2024

En tainnut startata näitä demoneja, joten mitä todennäköisemmin tämän vuoksi ei tullut tuloksia. Testaan uusiksi käynnistämällä nämä, ja tekemällä nmappauksen uudestaan.

    $ sudo systemctl start apache2
    $ sudo systemctl start ssh
    $ nmap -A localhost

![image](https://github.com/user-attachments/assets/5f9c9f0e-f787-43ea-bbb1-1123c9dc2e51)

Noniin, nyt näkyy 2 porttia avoimena kuten olikin tarkoitus, ja 998 suljettua porttia. Porttiskannauksella ei siis näe suljettuna olevia servereitä.

Tässä avoimina näkyvät portit 80 ja 22. Tästä näkee, että portti 22 on SSH, ja tämän tarkempi versiokin(OpenSSH 9.9p1 Debian).
Portti 80 taas HTTP, ja apache


### e) Asenna Metasploitable 2 virtuaalikoneeseen

Asensin Metasploitable 2 osoitteesta https://sourceforge.net/projects/metasploitable/files/latest/download.
Noudatin Valkamon ohjeita(https://tuomasvalkamo.com/PenTestCourse/week-2/) asennuksessa, purin tiedoston ja lisäsin tämän Virtualboxiin.


### f) Tee koneiden välille virtuaaliverkko. Jos säätelet VirtualBoxista

   -  Kali saa yhteyden Internettiin, mutta sen voi laittaa pois päältä
   -  Kalin ja Metasploitablen välillä on host-only network, niin että porttiskannatessa ym. koneet on eristetty intenetistä, mutta ne saavat yhteyden toisiinsa
   -  Vaihtoehtoisesti voit tehdä molempien koneiden asennuksen ja virtuaaliverkon vagrantilla. Silloin molemmat koneet samaan Vagrantfile:n.


Muokkasin verkkoasetuksia ohjeistuksen mukaan niin, että tein HostOnly#2, ja sallin tälle DHCP serverin. 

![image](https://github.com/user-attachments/assets/1e84b50e-e6e3-4f3e-a952-aa5801b4dd04)


Muokkasin Metasploitablen asetuksia niin, että vaihdoin network adapterin Natista luomaani Host only#2.

![image](https://github.com/user-attachments/assets/029ec522-3557-4288-a8b8-b442b4ca16bf)

Tämän jälkeen muokkasin Kalin verkkoasetuksia niin, että lisäsin kyseisen verkon adapter 2 kohtaan.

Testasin Kalin toimintaa tämän jälkeen, mutta jotain oli mennyt rikki, sillä kone ei enää auennutkaan, vaan heittää "aborted"-herjaa.

![image](https://github.com/user-attachments/assets/d2f9aa15-2925-4db9-95df-f43dc699ff92)

Muokkailen asetuksia niin, että otan ruksin pois adapter2 kohdasta, niin kone aukeaa taas. Ongelma taisi olla, että tässä mulla oli jäänyt ruksi molempiin kohtiin, joten testaan vaihtaa ruksit toisinpäin.
Tämäkään ei auttanut, virheviestiä tulee. Ilmeisesti tässä host-only verkossa, jonka tein, on joku bitti vinossa, minkä vuoksi ei nyt toimi.

![image](https://github.com/user-attachments/assets/9ae600a8-2f17-4077-9e29-d44442098966)

Katson verkkoasetuksia ja vaihdan host-only verkkoyhteydeksi 

"VM Name: kali

Failed to open/create the internal network 'HostInterfaceNetworking-VirtualBox Host-Only Ethernet Adapter #2' (VERR_INTNET_FLT_IF_NOT_FOUND).
Failed to attach the network LUN (VERR_INTNET_FLT_IF_NOT_FOUND).
Result Code:
E_FAIL (0X80004005)
Component:
ConsoleWrap
Interface:
IConsole {6ac83d89-6ee7-4e33-8ae6-b257b2e81be8}
"
Tätä täytyy hieman tutkia. Testasin poistaa luomani verkon ja tehdä sen uudestaan, ei auta.

Yrityksenä on nyt siis saada Kalin ja Metasploitablen välille host only verkon, ja Kali saa myös tarvittaesssa yhteyden verkkoon. 

Vaihdan asetuksista VirtualBoxissa valmiina olleen virtualbox host-only ethernet adapterin, ja muokkaan virtuaalikoneiden asetuksia niin, että ne käyttävät tätä.
Tämä näyttää toimivan, molemmat koneet käynnistyvät taas. Testaan näiden välistä verkkoa tarkemmin.

Pingaan 8.8.8.8, ja toimii. Irrotan verkkokaapelin virtualboxin asetuksista, ei toimi enää. Näin pitääkin olla.

![image](https://github.com/user-attachments/assets/96c7c96f-8d62-4404-ad0c-9f68294bac0c)

Testaan saman metasploitablelle,  ei ole yhteydessä verkkoon.

![image](https://github.com/user-attachments/assets/f778a328-1bb2-4039-a5f9-b3c99ffb0f64)

Testaan koneiden välistä yhteyttä, ja pyydän metasploitilta ifconfig-komennolla tämän ip-osoitetta, mutta koneella ei näyttäisi olevan ipv4-osoitetta.
Palaan taas tutkimaan VB host only ethernet adapteria ja tämän asetuksia, ja yritän löytää tähän jotain selitystä. 
Testaan taas vaihtaa yhteyttä adapter#2, no ei toimi. 

Annan molemille koneille ifconfig-komennot. Tarvisin Metasp:n ip-osoitteen, jotta voisin koittaa pingata tätä Kalilla nähdäkseni onko näiden välinen verkko toiminnassa.

![image](https://github.com/user-attachments/assets/e4f5befd-b3f5-4c6d-ab79-f5fc66eece0b)

Metasp ei ole nähdäkseni ip4v-osoitetta, eli joku verkossani nyt mättää. Tämän ei pitäisi olla kovin vaikea osuus kurssitehtävistä, mutta tähän on mennyt jo hyvä määrä aikaa.
Sammutan kaikki koneet ja jatkan myöhemmin uudestaan. Tässä välin pakko kerrata myös hieman ip-osoitteista, sillä tietoverkkojen kurssista on jo aikaa, eikä nämä ole enää parhaiten mielessä.

------

Metasploitable 2:n on vain yksi "Host only ethernet" verkkokortti. Kalissa 2; Adapter 1 NAT jossa kaapeli kiinni/irti tarpeen mukaan, ja adapter2 Host only ethernet adapter.

// Jatkuu seuraavana päivänä.

Yritän luoda virtualisointiympäristöä Vagrantilla, mutta tämäkään ei nyt näytä toimivan enää. 

![image](https://github.com/user-attachments/assets/da8eb9f4-d4f0-4f93-b393-8be1bc98542c)

Tsekkasin BIOSin asetuksista että virtualisointi on päällä, poistin ja asensin Vagrantin uudestaan. Muokkasin Vagrantfilen sisältöä niin, että se vastasi edellisellä palvelinten hallinta-kurssilta tuttua kaavaa, jolloin tämä oli toiminut ihan hyvin, mutta nyt ei jostain syystä mikään Virtualboxiin liittyvä tunnu toimivan koneellani oikein-

Muokkaan virtualboxista host only-verkkoa, poistan tämän ja luon uusiksi, vaihdan host onlyn Kalini adapter1 jos tällä olisi vaikutusta. 
Ei auta.
Asennan Metasploitablen uusiksi, jos auttaisi.
![image](https://github.com/user-attachments/assets/2fee5f51-d4dd-4f42-8827-4c6fcacb5114)

No ei näemmä. Tässä välissä kaivoin toisen koneen kaapista ja ajattelin että testaan Linuxilla, mutta enpä muista sen salasanaa, joten kirjautuminen jäi nyt siihen.

Testaan yhdistää Metasploitablen nyt hetkeksi NAT-verkkoon, josko tämä olisikin pitänyt tehdä ihan alussa. Konfiguroin asetukset tämän jälkeen uudestaan niinkuin näiden pitäisi olla, ja annan ifconfig-komennon.
![image](https://github.com/user-attachments/assets/9a39185b-41a4-451d-b798-1bf116219491)

En vieläkään saa ipv4-osoitetta, jonka tarvitsisin muodossa 192.jotain, jotta verkkoni osoittautuisi toimivaksi. Ei nyt vaan onnistu, ehkä tunnilla tajuan mikä tässä nyt menee pieleen. Loput tehtävistä jää jollekkin toiselle kertaa, koska en voi suorittaa niitä ilman toimivaa verkkoa laitteideni välillä.

// Update 31.10.2024
Päätin nyt vielä kokeilla, kun huomasin että virtualboxissani oli päivitys tekemättä. Päivitin Virtualboxin ja nyt verkko toimiikin kuin ihmeen kaupalla?? 

![image](https://github.com/user-attachments/assets/28488485-1d76-4826-b547-025626938b3c)

Jeee. Testaan vielä koneiden välisen yhteyden, pingaamalla Kalilla tuota Metasploitin ip-osoitetta 192.168.168.3.
Ensiksi ei toimi, mutta käynnistän koneet uudestaan ja viimein toimii täysillä! Note to self, jatkossa tarkista että kaikki softa on ajantasalla ja päivitettynä.

![image](https://github.com/user-attachments/assets/082ca998-c531-4c87-94ab-259ff88e510c)

### g) Etsi Metasploitable porttiskannaamalla (nmap -sn). Tarkista selaimella, että löysit oikean IP:n - Metasploitablen weppipalvelimen etusivulla lukee Metasploitable.

Skannaan Kalilla komennolla nmap -sn, ja tarkistan selaimella että löysin oikean IP:n.

![image](https://github.com/user-attachments/assets/25e45871-e0c4-41e9-9eca-9b8a4e52a216)

![image](https://github.com/user-attachments/assets/56a4f1e8-0175-4ed8-9311-3a20fec1c6bb)

Joo, oikealta näyttää.

### 


## Lähteet

Karvinen 2024: Tunkeutumistestaus. Luettavissa: 

https://terokarvinen.com/tunkeutumistestaus/ Luettu 27.10.2024

KKO KKO:2003:36, 2003. Luettavissa:

https://finlex.fi/fi/oikeus/kko/kko/2003/20030036 Luettu 27.10.2024

https://www.kali.org/docs/virtualization/import-premade-virtualbox/ Luettu 27.10.2024

Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains Luettavissa:

https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf Luettu 27.10.2024

https://www.kali.org/get-kali/#kali-live Luettu 27.10.2024

https://sourceforge.net/projects/metasploitable/files/latest/download Luettu 29.10.2024

Valkamo 2022: Hacking into a Target Using Metasploit. Luettavissa:

https://tuomasvalkamo.com/PenTestCourse/week-2/ Luettu 29.10.2024

https://en.wikipedia.org/wiki/List_of_Unix_daemons Luettu 29.10.2024

€ Santos et al: The Art of Hacking (Video Collection): 4.3 Surveying Essential Tools for Active Reconnaissance. Luettavissa:

https://www.oreilly.com/videos/the-art-of/9780135767849/9780135767849-SPTT_04_00/ Luettu 30.10.2024

https://docs.rapid7.com/metasploit/metasploitable-2-exploitability-guide Luettu 30.10.2024

Tapaus Vastaamo, vieraana Marko Leponen | 0x33. [podcast].

https://hakkerit.libsyn.com/tapaus-vastaamo-vieraana-marko-leponen-0x33 Kuunneltu 30.10.2024

