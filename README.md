ScTurkey (Software Craftsmanship Turkey) topluluğu 27 Mayıs 2018 yılında SoCraTes (Software Craftsmanship and Testing) konferansı düzenlemeye karar verir.

Grup organizatörleri biletlerin fiyatlarını şöyle belirlemiştir.

| Tarih                | Tip           | Fiyat   |
| ---------------------|:------------- | :-------|
| 1 Aralık - 15 Ocak   | Blind Bird    | 250 TL  |
| 16 Ocak  - 28 Şubat  | Early Bird    | 500 TL  | 
| 1 Mart   - 30 Nisan  | Regular       | 750 TL |
| 1 Mayıs  - 27 Mayıs  | Laggard       | 1000 TL | 


Topluluk ayrıca özel günlerde özel kodlar ile indirimler planlamaktadır. Fakat kodlar gizlidir.Bilet alanların günün anlam ve önemini bilmeleri ve kodu tahmin etmeleri gerekmektedir.
Tanımlanan kodlar şu şekildedir.

| Günün Önemi                    | Kod           | Tarih       | İndirim Oranı
| -------------------------------|:------------- | ----------- |----------------|
|Erich Gamma'nın doğum günü      | GAMMA         | 13 Mart     | %10            | 
|Kent Beck'in doğum günü         | BECK          | 31 Mart     | %15            |
|Ward Cunningham'ın doğum günü   | CUNNINGHAM    | 26 Mayıs    | %5             |
|Agile Manifestonun yıl dönümü   | AGILE         | 11-13 Şubat | %20            |

Bilet satışlarını kendi siteleri üzerinden yapmak isteyen organizatörler bilet satışının ciddi bir iş olduğunu farkettiklerinde ödeme kısmını üçüncü parti bir yazılım ile yapmaya karar verir ve uzun araştırmalar sonucunda
[iyzico'da](https://www.iyzico.com/en/)'da karar kılar.

https://dev.iyzipay.com 'daki api yardımıyla bilet satmak isteyen ScTurkey'in önünde bazı kısıtlamalar vardır:

1. Sadece Garanti Bankası, İş Bankası,Akbank ve Finansbank'a ait kredi kartlarına satış yapılabiliyordur.
2. Debit kartlara satış yapılamıyordur fakat Halk Bankası'na ait Debit kartları istisnadır.

Yolcular farklı tarihlerde sisteme kart numaralarını girerler. İndirim kodunu doğru ya da yanlış girebilirler veya girmeyebilirler.
ScTurkey yazılımı iyzico'nun kart sorgulama servisini kullanarak işlemin mümkün olup olmadığına karar verir. Mümkünse biletten gelen kazancı kaydeder.

**Yazılımın girdileri:**

* inputs.txt  : işlem kodu, işlem tarihi, kart numarası, indirim kodu

**Yazılımın çıktıları:**

* outputs.txt :  işlem kodu, "SUCCESS" ya da "FAIL", kazanç
* logs.txt    :  iyzico api'sini çağırma zamanı, işlem kodu, kart numarası

**Yazılımın Geliştirme Biçimi:**
* Yazılım Pair Programming yapılarak geliştirilecektir.
* Test Driven Development uygulanarak geliştirilecektir.
* Yazılım SOLID prensiplerine uygun şekilde geliştirilecektir.
* Yazılım herhangi bir dilde geliştirilebilir. Herhangi bir dil/araç kısıtlaması yoktur.


**Test Kartları**

| Kart Bin         | Kod | Banka  İsmi        |  Kart Tipi   | Kart Birliği     |  Kart Ailesi      |
| -----------------| :-- | :----------------- | :------------| :--------------- |:------------------|
| 5890040000000016 | 46  | Akbank             | DEBIT_CARD   | MASTER_CARD      | Neo               |
| 5526080000000006 | 46  | Akbank             | CREDIT_CARD  | MASTER_CARD      | Axess             |
| 4766620000000001 | 134 | Denizbank          | DEBIT_CARD   | VISA             | Denizbank DC      |
| 4603450000000000 | 134 | Denizbank          | CREDIT_CARD  | VISA             | Denizbank CC      |
| 4987490000000002 | 111 | Finansbank         | DEBIT_CARD   | VISA             | Cardfinans DC     |
| 5311570000000005 | 111 | Finansbank         | CREDIT_CARD  | MASTER_CARD      | Cardfinans        |
| 9792020000000001 | 111 | Finansbank         | DEBIT_CARD   | TROY             | Cardfinans DC     |
| 9792030000000000 | 111 | Finansbank         | CREDIT_CARD  | TROY             | Cardfinans        |
| 5170410000000004 | 62  | Garanti Bankası    | DEBIT_CARD   | MASTER_CARD      | Paracard          |
| 5400360000000003 | 62  | Garanti Bankası    | CREDIT_CARD  | MASTER_CARD      | Bonus             |
| 374427000000003  | 62  | Garanti Bankası    | CREDIT_CARD  | AMERICAN_EXPRESS | American Express  |
| 4475050000000003 | 12  | Halk Bankası       | DEBIT_CARD   | VISA             | Halkbank DC       |
| 5528790000000008 | 12  | Halk Bankası       | CREDIT_CARD  | MASTER_CARD      | Paraf             1|
| 4059030000000009 | 123 | HSBC               | DEBIT_CARD   | VISA             | Advantage DC      |
| 5504720000000003 | 123 | HSBC               | CREDIT_CARD  | MASTER_CARD      | Advantage         |
| 5892830000000000 | 64  | İş Bankası         | DEBIT_CARD   | MASTER_CARD      | Bankamatik        |
| 4543590000000006 | 64  | İş Bankası         | CREDIT_CARD  | VISA             | Maximum           |
| 4910050000000006 | 15  | Vakıfbank          | DEBIT_CARD   | VISA             | Vakıfbank DC      |
| 4157920000000002 | 15  | Vakıfbank          | CREDIT_CARD  | VISA             | World             |
| 5168880000000002 | 67  | Yapı Kredi Bankası | DEBIT_CARD   | MASTER_CARD      | Tlcard            |
| 5451030000000000 | 67  | Yapı Kredi Bankası | CREDIT_CARD  | MASTER_CARD      | World             |
