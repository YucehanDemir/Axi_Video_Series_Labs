## HEDEFLER:
Bu laboratuvarı tamamladığınızda şunları öğreneceksiniz.

1.AXI4-Stream veri akışını simülasyondan PPM dosyasına yazma.

2.SystemVerilog'da dosya işlemleri ve formatlı string kullanımı.

3.Üretilen PPM dosyasını GIMP kullanarak açma ve inceleme.

4.TPG arka plan deseni ayarlarını değiştirme ve farklı desenler üretme.

## ADIMLAR:

### Projeyi aç

1. XVES_0005 dosyasını indiriniz.

2. Vivado 2023.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0004  klasörüne kadar) 
(cd <path>/XVES_0004)

4. “ create_proj.tcl ” betiğini “source ./” yazarak giriniz.
### Block Diagram Penceresinin Açılması ve İncelenmesi

5. Tasarım Diagramı penceresi gerekli işlemler bittikten sonra otomatik açılacaktır.Eğer otomatik olarak açılmadıysa blok tasarımına çift tıklayarak açabilirsiniz.

![2](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/3b0e470d-5bdc-4473-9a06-833a18e886a2)
   
### Simülasyonun Çalıştırılması ve Analizi

6. Davranışsal simülasyonu başlatın ( Simülasyonu Çalıştır > Davranışsal Simülasyonu Çalıştır )

7. Simülasyonu 6 ms boyunca çalıştırın.

8. Simülasyon, TPG IP'den ilk karenin çıktısı tamamen alındığında duracaktır. Test tezgahı, TPG tarafından çıkarılan çerçeve boyutunun yapılandırılana uygun olup olmadığını kontrol edecektir.

9. Simülasyon bittiğinde Tcl konsolunda aşağıdaki mesajları görmelisiniz:

``` Görüntü yazılı Yapılandırılmış ve çıktı çözünürlüğü eşleşiyor, test başarılı ```

![3](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/91ec3fa3-9dbd-426d-8dd5-bdbe19b42dcb)

PPM görüntü dosyasının görüntü verileriyle oluşturulduğunu ve simülasyonun başarılı olduğunu gösterir.

### GIMP ile Görüntüyü Açmak

10.Terminalinizde Vivado'nun dışında,``` XVES_0005/proj_1/proj_1.sim/sim_1/behav/xsim``` 'de oluşturulan __image_out_1.ppm__ görüntü dosyasını bulun ve GIMP ile açın. 

![5](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/db0eb7bc-5311-457b-89bf-aa5dc7e32e2b)

11.TPG tarafından oluşturulan modelin şunu görebilirsiniz.Bu desene __“renk çubukları”__ adı verilir

![6](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/958e909a-7b8e-46cb-97bc-eb1d2815c508)

### Oluşturulan Deseni Değiştirme

12. Test tezgahı dosyasını açın ( Vivado metin düzenleyicisinde tb_tpg.sv )

13. TPG Arka Plan Deseni ayarına karşılık gelen satırı bulun.

////////////////////////////////////////////////// //////////////////////////////// 
// TPG yapılandırması 
// Seçilen Arka Plan Deseni 
// Bu Değer 0 ile arasında olmalıdır. 19 
tamsayı model_id = 8'h09;

![7](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/ba5e9b2c-39e8-493a-9325-b55c13d3b889)

14. Pattern_id değerini __0x0B__ olarak değiştirin

tamsayı model_id = 8'h0B;

![8](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/fb37ea58-e92d-44e1-b8fc-0cc05eca2fa1)

### Simülasyonun Çalıştırılması ve Analizi

15. Davranışsal simülasyonu başlatın ( Simülasyonu Çalıştır > Davranışsal Simülasyonu Çalıştır )

16. Simülasyonu 6 ms boyunca çalıştırın.

17. Oluşturulan görüntüyü GIMP kullanarak açın.

![9](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/7b5fc49a-95ff-4b95-95a2-d1d5010ad38a)

19. Artık bir __Tartan Renk Çubuğu__ deseni göreceksiniz.

![10](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/9023f649-3538-4e4d-a5cc-91662ca5148b)



