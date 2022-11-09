# Arduino és DS32321 Real Time Clock 1602 LCD kijelzővel

## Leírás
Ebben a projektben, egy DS3231 típusú Real Time Clock modult (RTC modul) építek. De miért is van szükség egy különálló valós idejű órára, miközben az Arduinonak van saját beépített órája? Az RTC modul egy külső akkumulátort működtet és így még akkor is nyomon tudja követni az időt, ha leválasztottuk a tápról a mikrokontrollert.

## Hardware
- Arduino UNO REV3 fejlesztői panel
- DS3231 + AT24C32 I2C RTC valós idejű memória modul
- CR2032 Gombelem
- KC-1602-BB-I2C LCD kijelző
- POM1615 LIN 10K B potenciométer
- HS-005 próbapanel
- RC-40-10/FF v. RC-40-10/MF v. RC-40-10/MM jumper kábel

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

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
