# Bildiğim bütün küarlar... Paramparça ! - Forensic200

### Soru
> Pelinsu'nun uğradığı birçok lokasyonda kod parçaları bulunmaktaydı. İpucu neydi ? 
> ![Dosyayı indir](https://github.com/xugurercan/DKHOS_Writeups/blob/master/Forensics/Forensic200/5e4d6213453b23d161887fc099062bcf9be57e26.zip)


### Çözüm
Dosyayı indirdiğimizde soru başlığında da belirtildiği gibi bizi bir QR koda air resim parçaları karşılıyor. 

![Qr Parçaları](https://github.com/xugurercan/DKHOS_Writeups/blob/master/Forensics/Forensic200/EkranGoruntusu1.png)

Tüm resimleri birleştirip bir QR kod elde etmeyi deneyip işe yaramadığını görünce, ilk yaptığımız QR standartına uyacak bir şekilde resimleri ayırmak oldu. 

Şu şekilde;
* Sol Üst Köşe: pn9
* Sağ Üst Köşe: bk5 
* Sol Alt Köşe: bi4 

çünkü aşağıdaki örnek QR kodu veya herhangi bir QR kodu incelersek bu kısımlar hep aynı oluyordu.

![Örnek QR](https://github.com/xugurercan/DKHOS_Writeups/blob/master/Forensics/Forensic200/OrnekQR.png)

Bunu yaptıktan sonra bu sıralamaya uyacak şekilde bir sıralama algoritması üretmeye çalıştık. Örneğin resimlerin hepsi aynı boyutta değildi aynı boyuttaki resimleri bu elimizdeki sıraya göre dizmeye çalıştık, sondaki sayıya göre tersten sıraladık pn9 başta olması gerektiği için, ortadaki harfe göre bir deneme yaptık ama hiç bir şekilde başarılı bir sonuç elde edemedik. Sonra bir ipucu yayınlandı.

**İpucu**
> İpucu Sorunun içinde saklı.

İpucunu görüp soruyu tekrar okuyunca bir aydınlanma geldi, oda ne bizim sorunun içerisindeki ilk kelime p ile başlıyor n ile bitiyor son kelimemizde n ile başlıyor i ile bitiyor. 

**İpucundan Sonra**
> **P**elinsu'nu**n** **u**ğradığ**ı** **b**irço**k** **l**okasyond**a** **k**o**d** **p**arçalar**ı** **b**ulunmaktayd**ı**. **İ**puc**u** **n**eyd**i** ? 

Hemen bu kelimelerin sırasına göre resimlerimizi sıraladık arada türkçe karakterler var onlarıda ingilizceye çevirdik. Aşağıdaki gibi bir çıktı elde ettik.

![Sıralanmış QRlar](https://github.com/xugurercan/DKHOS_Writeups/blob/master/Forensics/Forensic200/EkranGoruntusu2.png)

Bu oluşturduğumuz sıralamaylada resimleri birleştirdik.

**Komut**
> montage \*.jpg qr.pdf

![QR Sonuc](https://github.com/xugurercan/DKHOS_Writeups/blob/master/Forensics/Forensic200/EkranGoruntusu3.png)

Elde ettiğimiz QR kodunu ![Web QR](https://online-barcode-reader.inliteresearch.com/) okuyucudan ne var baktık hemen.

![QR Sonuc](https://github.com/xugurercan/DKHOS_Writeups/blob/master/Forensics/Forensic200/EkranGoruntusu4.png)

Flagi elde etmiş olduk.

**Flag**
> DKHOS{Bunl4r_h3p_M0ntaj}
