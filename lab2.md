# Yerel Video'dan AXI4-Stream'e:

## HEDEFLER:
   Bu laboratuvarı tamamladığınızda şunları öğreneceksiniz.
1. AXI4-Stream Protokolünü ne anlama geldiği 
2. AMD FPGA Cihazlarında Video Verilerinin Taşınması:
3. AXI4-Stream IP'nin kullanımı
4. Concat IP kullanımı
5. wr_data_count_i Sinyali ve simülasyon takibi
6. AXI4-Stream ve Video Arayüzü Arasındaki Farklar:
7. hsync_out ve m_axis_video_tlast Sıklığının Kontrolü:

## ADIMLAR:

### Projeyi aç
1. XVES_0002 dosyasını indiriniz.

2. Vivado 2023.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0002  klasörüne kadar) 
(cd <path>/XVES_0002)

4. “ create_proj.tcl ” betiğini “source ./” yazarak giriniz

!["tcl1"](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/b3ee68fe-8efe-42d7-94ab-33ea3d064f9d)

*cd komutu ile dosya dizini girme* 

![tcl2](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/14b98711-9b2f-4aa5-a20c-d46810486cbb)

*source ile projeyi çalıştırma* 

> ### NOT: 
> Vivado sürümünü 2023.1’den başka bir sürümü kullanıyorsanız projeniz tam olarak çalışmayacaktır.Aşağıdaki adımları yaparak tekrardan deneyiniz.
> - “create_proj.tcl” dosyasını notepade ya txt dosyası şeklinde açarak  “set scripts_vivado_version "2023.1" ” yazan satırda 2023.1 yerine kullandığınız sürümü yazınız.

![create_proj_tcl](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/94c04af6-2875-4774-b3e2-6d276821eb6f)

  
> - "src/tcl/bd.tcl" dosyasını notepade ya txt dosyası şeklinde açarak “set scripts_vivado_version "2023.1" ” yazan satırda 2023.1 yerine kullandığınız sürümü yazınız.

![bd_tcl](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/7d76b814-60ad-4244-b7c3-ea5f005ee9c3)

### Block Diagram Penceresinin Açılması ve İncelenmesi

5. Tasarım Diagramı penceresi gerekli işlemler bittikten sonra otomatik açılacaktır.Eğer otomatik olarak açılmadıysa blok tasarımına çift tıklayarak açabilirsiniz.

![block_design](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/28591132-786e-497c-af74-57f2aa417409)
 
6. Diagramdaki IP’leri ve bağlantılarını inceleyiniz.

### Simülasyonun Çalıştırılması ve Analizi

7. AXI4-Stream arayüzünü anlamak için simülasyonu çalıştırınız. 
(Run Simulation > Run Behavioral Simulation)

9. AXI4-Stream'de Video Girişinin çıkışında geçerli verilere sahip olmaya başladığı zamanı bulun
 (yükselen kenar m_axis_tvalid)


![sim_1](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/86c8bb88-0511-4364-9c1a-661cae309875)


10. wr_data_count_i sinyali, AXI4S IP'ye Video Girişinin dahili bir sinyalidir ve kaç tane veri kelimesinin hazır olduğunu gösterir (dahili FIFO'da).Bu sinyali 16661.664403us ve 16674.716851us simülasyon zamanları arasında kontrol edin.


11. hsync_out ve m_axis_video_tlast sıklığını kontrol edin. Her iki sinyalin de aynı frekansta gerçekleştiğini ve her ikisinin de bir çizginin sınırını gösterdiğini görebilirsiniz.

![sim2](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/681fb843-59d1-490c-91bc-14b03076c3f3)




