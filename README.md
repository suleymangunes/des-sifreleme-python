# DES Şifreleme
Des simetrik şifreleme algoritmasıdır. Gizli anahtarlı bir şifreleme türüdür ve büyük boyutlu verilerin şifrelenmesinde kullanılır.
- 64 bit uzunluğundaki blokları şifreler. 
- Simetrik şifreleme şifrelemede ve şifre çözmede aynı anahtarı kullanılır. 
- 56 bitlik anahtar değeri kullanır. 
- Feistel yapıdadır.
- Aynı işlemleri yapan 16 Rounddan oluşur. 
- Her Roundda kullanılan farklı alt anahtar başlangıç anahtarından üretilir.
 
<img src="https://raw.githubusercontent.com/suleymangunes/des-sifreleme-python/main/gorseller/des1.jpg" height="500">

## Claude Shannon ile Güçlü Şifreleme
Güçlü şifreleme algoritmaları inşa edebilmek için iki temel işlem vardır.
1. Confusion (Karıştırma): Bir şifreleme işleminde şifreli metin ile anahtar arasında bir ilişki olmamalıdır. Günümüzde bu yapıyı sağlayan en yaygın işlem (subsitotuon) yer değiştirmedir.
2. Diffusion (yayma): Sabit yaklaşımları engellemek amacıyla düz metindeki bir sembolün şifreli metindeki bir çok sembolü etkilemesi işlemidir. Sıklıkla kullanılan yapı permutasyondur.
İki işlem kendi başına güvenliği sağlayamazlar. Buradaki amaç bu iki işlemi art arda kullanarak güvenli şifreler oluşturmaktır. Des bu iki işlemi de içermesiyle güvenliği arttırmıştır.
   
## DES Şifreleme Algoritmasi
Düz metin onaltılık formatta olmalıdır. Eger degilse donusturme islemi yapılır.
64 bitlik anahtar degeri tanimlanir.
  
### Şifreleme
1. İlk permutasyon islemi permutasyon tablosu yardımıyla yapılır.
  
<img src="https://raw.githubusercontent.com/suleymangunes/des-sifreleme-python/main/gorseller/ilk_perm.jpg" height="500">
  
2. Feistel yapısı gereği 16 rounddan oluşan işlemler uygulanır.
64 bitlik metin sag ve sol olmak üzere iki parçaya ayrılır ve her defasında bir parçanın ve roundkey değerinin F fonksiyonuna tabi tutulup diğer parçayla XOR işlemine tabi tutulması ve sonra yer değiştirmesi sağlanır.
    
    """
    L = R - 1
    R = L - 1 XOR F(R -1, k)
    """
    
   #### F Fonksiyonu
   - 32 bitlik sağ parça expand tablosu yardımıyla 48 bit olarak genisletilir. (Diffusion)
   - Sag parca anahtar degeri ile XOR'lanır. (confusion)
   - S-box yardımıyla 48 bitlik metin 32 bite indirgenir. Bunu yaparken 48 biti 6 bitlik 8 parçaya ayırır. 6 bitin ilk 2 bitinin toplamı sıra sayısını geri kalan 4 bitin toplamı ise sutun sayısını verir. S-box tabloları yardımıyla satir ve sutun sayıları kullanılarak 4 bitlik degerler bulunur. (diffusion)
   - 4 bitlik değerlere permutasyon tablosu yardımıyla permutasyon işlemi uygulanır. (confisuon)
3. Son yer değiştirmeden sonra sağ ve sol parçalar kombinasyon işleminden geçirilir.
4. Final permutasyon işlemi final permutasyon tablosu yardımıyla uygulanır.
Şifreli metin oluşturuldu.
  
  ### Anahtar Oluşturma
  1. Parity bit bırakma tablosu yardımıyla 64 bitlik anahtar permutasyon işleminden geçirilerek 56 bite indirgenmesi sağlanır. Bu ilk permutasyon işleminde parity bitleri (8, 16, 24, 32, 40, 48, 56, 64) kaldirilir. Parity bitleri kontrol bitleridir.
  2. 56 bitlik anahtar ikiye bolünür.
  3. Kaydırma tablosundan yararlanılarak 1, 2, 9 ve 16. bitler 1 kez, geri kalan bitler ise 2 kez sola kaydırılır. Kaydırma isleminden sonra anahtarlar tekrar birleştirilir.
  4. Anahtar sıkıştırma tablosu kullanılarak 56 bitlik anahtarın 48 bite indirgenmesi sağlanır. Her round için ayrı anahtar oluşturulur.
  ### Şifre Çözme
  Feistel şifrelemede şifre çözmek için sadece anahtar tarifesi değiştirilir. Aynı 16 anahtar ters çevrilerek üretilir. Ters anahtarlarla şifrelenmiş metin şifreleme fonksiyonuna tabi tutulur. Bu sayede şifre çözme işlemi gerçekleştirilir.
