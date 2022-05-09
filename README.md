# DES Şifreleme
  Des simetrik şifreleme algoritmasıdır. Gizli anahtarlı bir şifreleme türüdür ve büyük boyutlu verilerin şifrelenmesinde kullanılır.
  - 64 bit uzunluğundaki blokları şifreler. 
  - Simetrik şifreleme şifrelemede ve şifre çözmede aynı anahtarı kullanılır. 
  - 56 bitlik anahtar değeri kullanır. 
  - Feistel yapıdadır.
  - Aynı işlemleri yapan 16 Rounddan oluşur. 
  - Her Roundda kullanılan farklı alt anahtar başlangıç anahtarından üretilir.
 
 ## Claude Shannon ile Güçlü Şifreleme
   Güçlü şifreleme algoritmaları inşa edebilmek için iki temel işlem vardır.
   1. Confusion (Karıştırma): Bir şifreleme işleminde şifreli metin ile anahtar arasında bir ilişki olmamalıdır. Günümüzde bu yapıyı sağlayan en yaygın işlem (subsitotuon) yer değiştirmedir.
   2. Diffusion (yayma): Sabit yaklaşımları engellemek amacıyla düz metindeki bir sembolün şifreli metindeki bir çok sembolü etkilemesi işlemidir. Sıklıkla kullanılan yapı permutasyondur.
   İki işlem kendi başına güvenliği sağlayamazlar. Buradaki amaç bu iki işlemi art arda kullanarak güvenli şifreler oluşturmaktır. Des bu iki işlemi de içermesiyle güvenliği arttırmıştır.
   
