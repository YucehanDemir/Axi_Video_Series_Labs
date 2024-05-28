# Test Modeli Oluşturucu (TPG) IP ile Simülasyon
## HEDEFLER:
Bu laboratuvarı tamamladığınızda şunları öğreneceksiniz.

1.Video Test Modeli Oluşturucu (TPG) ve AXI VIP IP'lerini Anlama:

2.AXI4-Lite Arayüzü Kullanarak TPG'nin Yapılandırılması:

3.Simülasyon dalga formlarını ve AXI4-Lite sinyallerini yorumlama

4.Test tezgahı dosyasını (tb_tpg.sv) anlama ve ayarlarını doğrulama.

## ADIMLAR:

### Projeyi aç

1. XVES_0004 dosyasını indiriniz.

2. Vivado 2023.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0004  klasörüne kadar) 
(cd <path>/XVES_0004)

4. “ create_proj.tcl ” betiğini “source ./” yazarak giriniz.

### Block Diagram Penceresinin Açılması ve İncelenmesi

5. Tasarım Diagramı penceresi gerekli işlemler bittikten sonra otomatik açılacaktır.Eğer otomatik olarak açılmadıysa blok tasarımına çift tıklayarak açabilirsiniz.

![1](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/89fb8ddc-8915-45c4-a13a-68438a7fa833)

6. Diagramdaki IP’leri ve bağlantılarını inceleyiniz.

7. Tasarımda yalnızca, doğrudan TPG IP'ye bağlanan Master olarak yapılandırılmış ve aşağıdaki TPG kayıtlarını yapılandırmak için kullanılan bir AXI VIP bulunur:
- ACTIVE_HEIGHT (Adres 0x0010)
- ACTIVE_WIDTH (Adres 0x0018)
- BACKGROUND_PATTERN_IP (Adres 0x0020)
> Bu simülasyonda, arka plan deseni kimliği için ayarlanan değer, bir renk çubukları desenine karşılık gelen 9'dur.
- BACKGROUND_PATTERN_IP (Adres 0x0020)

### Simülasyonun Çalıştırılması ve Analizi

8. AXI4-Stream arayüzünü anlamak için simülasyonu çalıştırınız. (Run Simulation > Run Behavioral Simulation)

9. Simülasyonu 6 ms boyunca çalıştırın.

10. İlk karenin çıktısı TPG IP'den tamamen çıktığında simülasyon duracaktır. Test tezgahı, TPG tarafından çıkarılan çerçeve boyutunun yapılandırılana uygun olup olmadığını kontrol edecektir.

11. Simülasyon süresi 550ns'ye gidin. AXI4-Lite'ın yazma adresi kanalında 0x10 adresinin ayarlandığını görebilirsiniz. (s_axi_CTRL_AWADDR)

![2](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/f6367075-9d11-4af6-b147-8cdb9affd41c)

12. Simülasyon zamanı 1.876401'den itibaren, AXI4-Stream Arayüzünde TPG çıkış verilerini görebilirsiniz. (m_axis_video_TVALID = '1')

![3](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/ee4226c2-52d8-44c5-aab8-d4846d6d652b)


