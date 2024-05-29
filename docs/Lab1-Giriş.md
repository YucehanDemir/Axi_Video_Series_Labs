# Dijital Videoya Giriş

### Videoya Giriş

Video, belirli bir frekansta (genellikle saniyede 50 veya 60 kez) değişen bir dizi görüntüdür.

Bir kaynaktan monitöre aktarıldığında video her seferinde bir görüntü gönderilir. Her görüntü en üst satırdan başlayarak satır satır, her satır ise sol pikselden başlayarak piksel piksel gönderilir.

Örneğin aşağıdaki şekilde 3x3 piksellik bir görüntünün 3 veri hattı (Kırmızı Yeşil Mavi) kullanılarak bir monitöre nasıl gönderilebileceği gösterilmektedir.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/06195745-50f6-44f3-a9c4-2ddbf4336e40)


Piksel değerleriyle birlikte, video karesi zamanlamasını tanımlamak için zamanlama bilgisi (zamanlama sinyalleri tarafından taşınan) gönderilir. Bir video çerçevesi (bir videonun tek bir görüntüsü), aktif video (actieve)ve karartma (blanking) periyotlarından oluşur.

Zamanlama sinyalleri, boşluk periyodunu (genellikle hblank ve vblank olarak adlandırılır) ve boşluk periyodu sırasında meydana gelen yatay ve dikey senkronizasyonu (genellikle hsync ve vsync olarak adlandırılır) temsil eden yatay ve dikey boşluktur ve yeni bir hattın (hsync) ne zaman geldiğini belirtmek için kullanılır. ) veya yeni bir kare (vsync) başlıyor.

Aşağıdaki şekilde senkronizasyon sinyalleriyle birlikte bir video karesi örneği gösterilmektedir.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/6afca920-94fb-4a5d-a09e-8ad2b40228da)

Video sistemleri, çeşitli kutuplara sahip farklı körleme, senkronizasyon veya aktif sinyal kombinasyonlarını kullanabilir. Örneğin, bir VGA arayüzü yalnızca hsync ve vsync'i kullanıyor.
