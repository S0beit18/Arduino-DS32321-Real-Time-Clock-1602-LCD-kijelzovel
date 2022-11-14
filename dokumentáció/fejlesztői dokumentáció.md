# Arduino UNO vezérlésű digitális óra fejlesztői dokumentációja.

## Specifikációk, követelmények:
Arduino vagy Raspberry Pi alapú mikroelektronikai rendszer létrehozása.

### Értékelési szempontok:
- Elégtelen: nem felel meg a minimális kritériumoknak, akár tartalmilag vagy minőségben
- Elégséges: viszonylag egyszerűbb a feladat, és készül hozzá fejlesztői dokumentáció és használati útmutató
- Közepes: bonyolultabb a feladat, amely kiegészül még valamilyen mérő/adatgyűjtő rendszerrel (adatbázis) és egyaránt készül hozzá fejlesztői dokumentáció és használati útmutató
- Jó: a közepes szint elvárásait még ki kell egészíteni valamilyen adatvizualizálási rendszerrel
- Jeles: a jó osztályzat elvárásait még ki kell egészíteni valamilyen plusz kommunikációs csatornával. Ez lehet pl.: tweet, facebook post, email notification, push üzenet a telefonon, stb. (csak a képzelet szabhat határokat)

## Tervezési fázis:
Eleinte sokat gondolkozam, hogy mit is tudnék megvalósítani és nagyon nem jutott eszembe semmi. Rájöttem, hogy körül kell néznem a saját környezetemben, ahhoz, hogy legyen bármi elképzelésem arról, hogy mit is akarok megvalósítani. Itthon van egy digitális órám, ami ugyan ezen az elven működik. Bedugjuk a tápot, az óra kiírja az időt szép világosan, Ezzel csak az a baj, hogy ez az óra napokkal később már több mint nyolc perces sietéssel jár, illetve, hogy a kijelző fényereje nem állítható. Így esett a választásom erre a projektre, hiszen szeretnék egy használhatót a szobámba. Sikerült a szükséges modulokat is egy oldalról beszereznem ,így jöval megkönnyítve és lerövidítve a projekt menetét.

## Futási környezet
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

## A fejlesztői környezet
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

## Felhasznált modulok
- [Arduino UNO REV3 fejlesztői panel](https://www.hestore.hu/prod_10035528.html)
- [DS3231 + AT24C32 I2C RTC valós idejű memória modul](https://www.hestore.hu/prod_10038042.html)
- [CR2032 Gombelem](https://www.hestore.hu/prod_10042619.html)
- [KC-1602-BB-I2C LCD kijelző](https://www.hestore.hu/prod_10042987.html)
- [POM1615 LIN 10K B potenciométer](https://www.hestore.hu/prod_10027737.html)
- [HS-005 próbapanel](https://www.hestore.hu/prod_10043091.html)
- [RC-40-10/FF jumper kábel](https://www.hestore.hu/prod_10036627.html)
- [RC-40-10/MF jumper kábel](https://www.hestore.hu/prod_10036628.html)
- [RC-40-10/MM jumper kábel](https://www.hestore.hu/prod_10036629.html)

## A fontosabb modulok leírása
### DS3231 RTC
A modul egy valós idejű óra ( Real time clock vagy másképp RTC modul), amely képes kezelni órát, percet és másodpercet rendkívül nagy pontossággal. Ugyancsak képes kezelni a napokat hónapokat éveket. A pontosságért a DS3231 típusú chip felell, míg az adattárolásért AT24C32, amely 32kBit nagyságú.

Az óra pontossága +/- 2ppm (0-50°C). Ez annyit jelent, hogy szélsőséges esetekben 1.2 másodperc lehet a késés havonta. Normál kvarckristályos órák esetén ez 30 másodperc is lehet.

A modul 3,3 vagy 5 V-os feszültséggel is képes működni, ami sok fejlesztői platformra, mikrokontrollerre alkalmassá teszi a használatát. Az akkumulátor bemenete 3V-os (CR2032 típusú akkumulátor), amely elősegíti, hogy a modul több mint egy évig megtarthatja az információkat.

A modul az I2C kommunikációs protokollt használja, amely megkönnyíti az összeköttetést az Arduinoval.

### KC-1602-BB-I2C LCD kijelző
Ez az LCD képernyő 16 karaktert képes megjeleníteni két sorban (1602).
Kék színű háttérvilágítással rendelkezik, az I2C kommunikációnak köszönhetően könnyedén
(két adatvezeték segítségével) használható Arduino projekthez.

### POM1615 LIN 10K B potenciométer
- Ellenállás-100 kΩ	
- Ellenállás lefolyás-Lineáris
- Terhelhetőség-200 mW
- Forgatási szög (mechanikus)-300 °

## Az algoritmusok és a kódok:
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

## Kapcsolási rajz
<details>
  <summary>Kapcsolási rajz</summary>
    <p>
      <picture>
        <img alt="Kapcsolási rajz" src="https://user-images.githubusercontent.com/117828931/201667191-d593dcd2-0a1c-4f0d-ab35-1dba5b52b161.png">
      </picture>
    </p>
</details>

## Fellépő hibák a tervezés, tesztelés során:
A tervezés közben egy olyan -számomra- hibát találtam, ami mellett nem tudtam dönteni. Mivel ezelőtt nem tanultam semmi ilyesmit, ezért persze internetes oldalakon, próbáltam kapcsolási rajzot összerakni. Sikerült is, kisebb nagyobb sikerrel.

Az első példa azt mutatja be, hogy itt a kapcsolási rajz teljesen kész állapotban van, viszont nem tudom lefuttatni szimuláció céljából.
<details>
  <summary>Kapcsolási rajz szimuláció nélkül</summary>
    <p>
      <picture>
        <img alt="Kapcsolási rajz" src="https://user-images.githubusercontent.com/117828931/201672997-ee8c3753-b1f6-4421-ab91-1f7e56ebf1a3.png">
      </picture>
    </p>
</details>

A második példa pedig


## Működési vázlat, szimuláció online
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

## Fejlesztési lehetőségek:
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

## Képek és videók a kész robotkarról:
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
