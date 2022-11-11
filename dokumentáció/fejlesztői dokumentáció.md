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

## Kapcsolási rajz
