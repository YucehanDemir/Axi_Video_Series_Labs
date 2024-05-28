# YUV and YCbCr color space

## Konu Anlatımı:

### Renk Uzayı Nedir? 
 
Renk uzayı renkleri temsil etmenin bir yoludur. Bir bilgisayarda sıklıkla RGB (Kırmızı Yeşil Mavi için) hakkında konuşacaksınız. Bunu insan beyni için görselleştirmek, tıpkı boyayla oynamak gibi kolaydır. Biraz Kırmızı acıyı biraz mavi acıyla karıştırırsanız, bir Menekşe rengi elde edersiniz (buna katkı renkleri denir).
Bu, RGB renk uzayındaki bir piksel için aynıdır. Mavi ve kırmızı bileşenleri yüksek, yeşil bileşeni düşük ise piksel mor olacaktır.

### YUV Renk Uzayı:

İlk televizyonlar Siyah Beyaz (Siyah Beyaz) idi. İlk renkli televizyon geldiğinde renk bilgisi alabilmenin yanı sıra siyah-beyaz TV altyapısına da uyumlu olması gerekiyordu. Siyah-Beyaz sistemi yalnızca parlaklık bilgisini kullandı (Y ile temsil edilir). Bunun üzerine renk bilgisi (krominans adı verilen ve U ve V ile temsil edilen) eklendi.

### YCbCr: 

YCbCr, YUV renk alanının ölçeklendirilmiş ve dengelenmiş bir versiyonudur. Y ayrıca parlaklığı temsil eder ve Cb ve Cr, renk bilgisini içeren koma bileşenlerini temsil eder.
ITU-R BT601, ITU-R BT709 veya ITU-R BT.2020 örneğine göre YCbCr'yi tanımlayan farklı standartlar vardır.

## ADIMLAR:

### Projeyi aç

1. XVES_0009 dosyasını indiriniz.

2. Vivado 2018.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0009  klasörüne kadar) 
(cd <path>/XVES_0009)

4. “ create_proj.tcl ” betiğini “source ./” yazarak giriniz.
   
### Block Diagram Penceresinin Açılması ve İncelenmesi

5. Tasarım Diagramı penceresi gerekli işlemler bittikten sonra otomatik açılacaktır.Eğer otomatik olarak açılmadıysa blok tasarımına çift tıklayarak açabilirsiniz.

6. BD tasarımını açın. Yalnızca VIP IP tarafından kontrol edilen bir test modeli oluşturucu içerdiğini görebilirsiniz.

   ![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/2b0d674c-ee56-4144-ad81-0fb46d9eba39)

## RGB çıkışını alın

7. Simülasyonu 6 ms boyunca çalıştırın.

8. Bir çıktı görüntüsü proj_1/proj_1.sim/sim_1/behav/xsim/TPG_RGB.ppm oluşturuldu. GIMP ile açın. Bunun TGB renk uzayındaki renk çubuğu deseni olduğunu görebiliriz.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/28103f6e-8b25-40e9-8ff9-d9d94dffc5aa)

## YUV verilerinin çıktısını almak için TPG IP'yi yapılandırma

9. YUV çıkışı için TPG IP'sini yapılandırın. Test tezgahı dosyasını tb_YUV_RGB.sv açın ve 184-185 satırlarını bulun:
- //TPG çıkışı renk alanını ayarlayın
master_agent.AXI4LITE_WRITE_BURST(TPG_COLOR_FORMAT_REG,0,TPG_RGB_OUT,resp);
185. satırı şu şekilde değiştirin: master_agent.AXI4LITE_WRITE_BURST(TPG_COLOR_FORMAT_REG,0,TPG_ YUV _OUT,resp);
  
10. Ek olarak, çıktı dosyasının adını 230. satırda TPG_YUV.ppm olarak değiştirin.

11. Test tezgahı dosyasını kaydedin ve simülasyonu 6 ms boyunca yeniden çalıştırın.

12. Proj_1/proj_1.sim/sim_1/behav/xsim/TPG_YUV.ppm kasalı yeni görüntü dosyasını açarsak, aynı desene benzediğini ancak farklı renklerde göründüğünü görebiliriz. Bunun nedeni, GIMP'nin RGB olduğunu düşünmesine rağmen bizim YUV renklerini göstermeye çalışmamızdır.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/03ef9a06-a075-4aec-ab73-ec96d0a7a37b)

13. Buna bakmanın daha iyi bir yolu, her bir katmana bakmak olacaktır. GIMP'de Renkler > Bileşenler > Ayrıştır'a tıklayın


14. Ayrıştırma penceresinde , Renk Modeli olarak RGB'yi seçin , Katmanlara ayrıştırın seçeneğinin işaretini kaldırın ve Tamam'a tıklayın.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/af245cdf-198c-49ca-9dba-c3b6132e7972)

> Not: RGB'yi seçmemizin nedeni GIMP'in girişimizin RGB olduğunu düşünmesidir. Ayrıştırma, RGB ayarlarıyla (giriş RGB ise) görüntüyü yalnızca 3 farklı görüntüye (her bileşen için 1) böler.
 
15. Her bileşen için bir tane olmak üzere 3 yeni pencere açılacaktır.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/d7374a81-8cdd-4555-bdc5-a11eb0287467)

16. YUV-red.ppm adı verilen pencere Y bileşenine, YUV-green.ppm ve YUV-blue.ppm ise Cb ve Cr bileşenlerine karşılık gelir.

### AXI4-Stream YUV verilerini RGB'ye dönüştürme

17. Blok tasarımını açın.

18. AXI4_Stream_out çıkışı ile TPG arasındaki kabloyu silin.

19. BD'ye sağ tıklayın ve IP Ekle… öğesine tıklayın . Ycrcb2rgb'yi arayın ve ENTER tuşuna basın.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/874ca29f-d53b-479d-9eee-7dc7c5271b83)

Yapılandırma GUI'sini açmak için YCrCb'den RGB IP'ye çift tıklayın. Aşağıdaki parametreleri değiştirin:
- Tarama Çizgisi Başına Piksel: 640
- Çerçeve Başına Tarama Sayısı: 400
- Standart Seçim: HD ITU 709 1250 PAL
- Çıkış Aralığı Seçimi: Bilgisayar Grafiği için 0 ila 255
  
![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/15c32d67-f947-49e0-b4f9-d61ad1cf8a56)

20. Video_in girişini TPG m_axis_video çıkışına ve video_out'u BD AXI4_Stream_out çıkışına bağlayın.

21. Ack ve aresetn'i aclk_50MHz ve aresetn_0 bağlantı noktalarına bağlayın.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/b1cd385c-6665-4608-a5ff-083c687b572f)

22. BD'yi doğrulayın ve kaydedin.

23. Test tezgahı dosyasını açın ve çıktı dosyasının adını Convert_RGB.ppm olarak değiştirin. Test tezgahı dosyasını kaydedin

24. Simülasyonu başlatın ve 6 ms boyunca çalıştırın.

25. Oluşturulan görüntüyü proj_1/proj_1.sim/sim_1/behav/xsim/converted_RGB.ppm açın. Çıktıda RGB desenine sahip olduğumuzu görebiliriz.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/5782cda8-1b25-4e48-aa5f-f5df0ba225ba)








