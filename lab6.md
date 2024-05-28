# AXI4-Stream'den Yerel Videoya
## HEDEFLER:
Bu laboratuvarı tamamladığınızda şunları öğreneceksiniz.

1. AXI4-Stream ve Native Video Arasındaki Köprünün Oluşturulması

2.Video Timing Controller (VTC) IP Kullanımı

3.Simülasyon sonuçlarının analiz edilmesi, özellikle AXI4-Stream verisinin kilitlendiği (locked) ve native video çıktısının başladığı zamanların belirlenmesi

## ADIMLAR:

### Projeyi aç

1. XVES_0006 dosyasını indiriniz.

2. Vivado 2023.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0006  klasörüne kadar) 
(cd <path>/XVES_000)

4. “ create_proj.tcl ” betiğini “source ./” yazarak giriniz.

### Block Diagram Penceresinin Açılması ve İncelenmesi

5. Tasarım Diagramı penceresi gerekli işlemler bittikten sonra otomatik açılacaktır.Eğer otomatik olarak açılmadıysa blok tasarımına çift tıklayarak açabilirsiniz.
   
6. AXI4-Stream video çıkışını TPG IP'den yerel videoya dönüştürmek için bir AXI4-Stream to Video Out IP'ye ekleyin.
   - BD'ye sağ tıklayın ve IP Ekle… öğesine tıklayın.
     
     ![1](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/e577994c-c4cb-4cf2-8f94-d231ce0bf3eb)

   - Video çıkışını arayın ve AXI4-Stream to Video Out'a çift tıklayın.
  
     ![2](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/0aad1505-20c1-48f7-876a-bafc72e3c35d)

7. AXI4-Stream'in video_in girişini Video Çıkışına ve TPG'nin m_axis_video çıkışına bağlayınız.

8. AXI4-Stream'in ack ve aresetn girişlerini Video Çıkışına, aclk_40MHz ve aresetn_0'a bağlayın.

![5](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/466b15b2-b38f-4738-9d90-0db238c1e50b)

9. +”ya tıklayarak AXI4-Stream'in vo_io_out arayüzünü Video Çıkışına genişletin ve alt sinyalleri karşılık gelen BD çıkışlarına bağlayınız.
    
![6](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/9fb086ad-d264-4b3d-bef8-f43f90a160c2)

### Zamanlama Sinyallerinin Oluşturulması

AXI4-Stream to Video Out IP, zamanlama sinyallerini üretmez. Jeneratör olarak yapılandırılmış bir Video Zamanlama Denetleyicisi (VTC) IP'si ile paralel olarak kullanılmak üzere tasarlanmıştır.

10. Tasarıma bir Video Zamanlama Denetleyicisi ekleyin.

 -  BD'ye sağ tıklayın ve IP Ekle… öğesine tıklayın.
     
 - IP'yi eklemek için zamanlamayı arayın ve Video Zamanlama Denetleyicisine çift tıklayın.

Bu eğitimde TPG (ve çıkış çerçevesi) için 800 x 600 @60Hz'lik sabit bir çözünürlük kullanacağız.

11. Yapılandırmak için Video Zamanlama Denetleyicisine çift tıklayınız.

a. Algılama/Oluşturma sayfasında

- AXI4-Lite Arayüzünü Dahil Etmeyi Devre Dışı Bırak
  
- Algılamayı Etkinleştir'i Devre Dışı Bırak

![7](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/4c423d7d-9fce-4478-9970-0fe23dbe4501)

    

