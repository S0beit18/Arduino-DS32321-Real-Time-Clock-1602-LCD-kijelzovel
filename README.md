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
