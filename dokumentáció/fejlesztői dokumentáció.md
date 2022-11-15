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
Demo kód:
```
    void setup()
    {
    Serial.begin(115200); // Setup Serial connection
    rtc.begin();
    //A követkető 3 sort kikommentálva lehet az időt beállítani.
    //rtc.setDOW(MONDAY);       //Nap beállítása
    //rtc.setTime(12, 0, 0);    //Idő beállítása 12:00:00 (24 órás formátum)
    //rtc.setDate(11, 14, 2022)  //Dátum beállítása 2022.11.14
    }
          
    void loop()
    {
    Serial.print(rtc.getDOWStr());    //Elküldi a hét napját
    Serial.print(" ");
    Serial.print(rtc.getDateStr());   //Elküldi a dátumot
    Serial.print(" -- ");
    Serial.println(rtc.getTimeStr()); //Elküldi az időt
    delay (1000);                     //Vár 1 másodpercet az ismétlés előtt
```
Ha megnézzük a loop szekciót a mintakódban akkor látható hogy 3 különböző függvényt használok, hogy információt kapjunk az RTC modultól, majd ezeket az információkat írjuk ki a Serial Monitorra. A képen látható az illusztráció:
KELL KÉP!!!!!!

Mintakód:
```
##include <DS3231.h>
#include <LiquidCrystal.h>

DS3231  rtc(SDA, SCL);
LiquidCrystal lcd(1, 2, 4, 5, 6, 7);
void setup() { 
 rtc.begin();
 lcd.begin(16,2);
}
void loop() { 
 lcd.setCursor(0,0);
 lcd.print("Time:  ");
 lcd.print(rtc.getTimeStr());
 
 lcd.setCursor(0,1);
 lcd.print("Date: ");
 lcd.print(rtc.getDateStr());
 
 delay(1000); 
}
```
A második példában egy I2C kommunikációs két soros LCD kijelzőt fogok használni, hogy vizuálisan is megjelenítsem az időt és a dátumot. A alábbi kapcsolási rajzon is ez az ábra látható.

          
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
A tervezés közben egy olyan -számomra- hibát találtam, ami mellett nem tudtam dönteni. Mivel ezelőtt nem tanultam semmi ilyesmit, ezért persze internetes oldalakon, próbáltam kapcsolási rajzot összerakni. Sikerült is, kisebb nagyobb sikerrel. Csak 2 oldalon próbáltam és mindegyiken más-más sikerrel sikerült megcsinálni.

Az első példa azt mutatja be, hogy itt a kapcsolási rajz teljesen kész állapotban van, viszont nem tudom lefuttatni szimuláció céljából.
<details>
  <summary>Kapcsolási rajz oldal szimulációs rész nélkül</summary>
    <p>
      <picture>
        <img alt="Kapcsolási rajz" src="https://user-images.githubusercontent.com/117828931/201676388-f618406e-e969-4263-8880-d7b3b376548a.png">
      </picture>
    </p>
</details>

A második példa, pedig azt mutatja be, hogy az RTC modul híján teljes az ábra. Sajnos ezen az oldalon nem volt megtalálható az RTC modul, pedig ezt az oldalt találtam csak ahol le is lehet szimulálni a projekt működését.
<details>
  <summary>Kapcsolási rajz szimulációs oldalon, RTC modul nélül</summary>
    <p>
      <picture>
        <img alt="Kapcsolási rajz" src="https://user-images.githubusercontent.com/117828931/201980402-ea353a26-3f52-424f-9a11-afed00cd1db6.png">
      </picture>
    </p>
</details>

## Működési vázlat, szimuláció online
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

## Fejlesztési lehetőségek:
Mivel ez nem egy végleges verzió, így rengeteg tovább fejlesztési lehtőség rejlik ebben a projektben.
Ezek közül pár:
- Konnektorból, esetleg akkumulátorról való működtetés
- Óra vázának kialakítása
- Óra/dátum átállítása gombokkal

## Képek és videók az óráról:
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

## Szerző:
- Név: Játékos Ádám Csaba
- Neptun-kód: DLHKIJ
- Email: jatekadi@gmail.com
- Tantárgy kódja: GKNB_INTM020
- Neve: Mikroelektromechanikai rendszerek
