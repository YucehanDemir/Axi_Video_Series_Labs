# YCbCr Chroma alt örneklemesi/yeniden örneklemesi

### Chroma alt örneklemesi nedir?
 
Renk alt örneklemesi, görüntüdeki Renk örneklerinin sayısını azaltarak (tüm parlaklık örnekleri korunurken) bir görüntüyü kodlama uygulamasıdır. İnsan görsel sistemi parlaklıktaki değişikliklere renkten daha duyarlı olduğundan, alt örnekleme insan gözü için neredeyse hiçbir görsel fark yaratmaz.
 
Chroma alt örneklemesini kullanan yaygın YCbCr renk formatı YCbCR422 ve YCbCr420'dir. Chroma alt örneklemesi olmayan YCbCr'nin YCbCr444 olarak adlandırılabileceğini unutmayın.
 
Chroma yeniden örnekleme, eksik Chroma bilgilerinin yeniden oluşturulması uygulamasıdır.
  
### YCbCr422
 
YCbCr422'de Chroma bilgisi, parlaklık bilgisinin örnekleme hızının yarısı kadar örneklenir. Bu, her iki yatay Y numunesi için yalnızca bir Cb ve bir Cr numunesi olduğu anlamına gelir.
AXI4-Stream arayüzünde, Cb ve Cr bileşeni dönüşümlü olarak her piksel için bir Chroma bilgisi gönderilir.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/37792704-2208-4042-aec8-5772f0fc004e)

### YCbCr420
 
YCbCR422'de olduğu gibi YCbCr420'de de Chroma bilgileri parlaklık bilgisinin örnekleme hızının yarısı kadar örneklenir. Ancak Chroma bilgisi dikey olarak da örneklenir.
 
AXI4-Stream arayüzünde, her piksel için bir Chroma bilgisi, yalnızca çift satırlarda Cb ve Cr bileşenini değiştirerek gönderilir.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/e68e9346-821e-4c50-87fe-d948508448a7)

##ADIMLAR  

> Note 1: This tutorial is intended to be used only with Vivado 2018.1 and only in simulation
> Note 2: A valid license for the Test Pattern Generator is required to build the design.
 
## Projeyi aç

1. XVES_00010 dosyasını indiriniz.

2. Vivado 2018.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0008 klasörüne kadar) (cd /XVES_00010)

4. “ create_proj.tcl ” betiğini “source ./” yazarak giriniz.
 
### Add a Chroma Resampler IP
 
5. Chroma Resampler IP'si ekleyin
 
6. BD tasarımını açın.

7. AXI4_Stream_out çıkışı ile TPG arasındaki kabloyu silin

8. BD'ye sağ tıklayın ve IP Ekle… öğesine tıklayın. Kroma yeniden örnekleyiciyi arayın ve ENTER'a basın.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/9aa3b593-3f43-4205-b2ac-d54726eaca19)

9.  Yapılandırma GUI'sini açmak için Chroma Resampler IP'sine çift tıklayın. Aşağıdaki parametreleri değiştirin:
- Tarama Çizgisi Başına Piksel: 640
- Çerçeve Başına Tarama Sayısı: 400
- Yeniden Örnekleme Kaynağı: YCbCr444
- Yeniden Örnekleme: YCbCr422

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/a5381a1c-ae7a-48b2-9434-fbdf8264e5c5)

10. Video_in girişini TPG m_axis_video çıkışına ve video_out'u BD AXI4_Stream_out çıkışına bağlayın

11. Ack ve aresetn'i aclk_50MHz ve aresetn_0 bağlantı noktalarına bağlayınız.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/2b91fcb3-fe2f-42be-8ef7-ab50744ccb72)

12. Tanımsız seçeneğine tıklayarak BD'yi doğrulayın.

13. Kaynaklar penceresinde BD'ye sağ tıklayıp Çıktı Ürünleri Oluştur'a tıklayarak BD çıktı ürünlerini oluşturun.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/4162a156-2bdd-46a7-8e66-bda83e759ea4)

14. Simülasyonda YCbCr444 ila YCbCr422 alt örneklemesini analiz edin

15. Davranışsal simülasyonu başlatın ve 1 ms boyunca çalıştırın.
  
16. Simülasyon zamanı 1.43us'ta TPG'nin video çıkışı vermeye başladığını ve simülasyon zamanı 1.57us'ta Chroma Resampler'ın YCbCr422 alt örneklenmiş video çıkışı vermeye başladığını görebiliriz.

![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/ff268191-172d-40ad-b766-e3d85f300443)
 
17. Chroma Resampler'ın çıkışında, TPG'nin çıkışıyla karşılaştırıldığında, Cb ve Cr Chroma örneklerinin (bitler [15:8]) değişimini görebiliriz, Y örnekleri ise (bitler [7:0]) TPG çıkışındakiyle aynı

18. Simülasyonu kapat

### Simülasyonda YCbCr444 ila YCbCr420 alt örneklemesini analiz edin

19. Blok tasarımını aç Yapılandırma GUI'sini açmak için Chroma Resampler IP'sine çift tıklayın. Çıkış formatını YCbCr420 olarak değiştirin.

 ![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/fea2636b-7053-4059-9ecb-44e7dd61faad)

20. Blok Tasarımını doğrulayın ve kaydedin.

21. Blok tasarımı için çıktı ürünlerini oluşturun

22. Davranışsal simülasyonu başlatın ve 1 ms boyunca çalıştırın.

23. Simülasyon zamanı 1.43us'ta TPG'nin video çıkışı vermeye başladığını ve simülasyon zamanı 1.65us'ta Chroma Resampler'ın YCbCr420 alt örneklenmiş video çıkışı vermeye başladığını görebiliriz.

23. Chroma Resampler tarafından çıkarılan veriler, YCbCr422 formatındaki çıktıyla önceki simülasyona benzer görünüyor.
Ancak ikinci satıra gidersek (simülasyon zamanı 14.59us'tan başlayarak, son 1'den sonra) tdata çıkışının MSB bitlerinin ([15:8]) artık her piksel için 0 değerine sahip olduğunu görebiliriz. satırı, YcbCr420 çıkışıyla beklenen satırda gönderilen Chroma bilgisinin olmadığı anlamına gelir.



 



