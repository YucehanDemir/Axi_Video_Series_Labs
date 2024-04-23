# HEDEFLER:
   Bu laboratuvarı tamamladığınızda şunları öğreneceksiniz.
1. AXI4-Stream Protokolünü ne anlama geldiği 
2. AMD FPGA Cihazlarında Video Verilerinin Taşınması:
3. AXI4-Stream IP'nin kullanımı
4. Concat IP kullanımı
5. wr_data_count_i Sinyali ve simülasyon takibi
6. AXI4-Stream ve Video Arayüzü Arasındaki Farklar:
7. hsync_out ve m_axis_video_tlast Sıklığının Kontrolü:

# ADIMLAR:

1. XVES_0002 dosyasını indiriniz.

2. Vivado 2023.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0002  klasörüne kadar) 
(cd <path>/XVES_0002)

4. “ create_proj.tcl ” betiğini “source ./” yazarak giriniz

![" cd komutu ile dosya dizinini girme "](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/b3ee68fe-8efe-42d7-94ab-33ea3d064f9d)


### NOT: 
Vivado sürümünü 2023.1’den başka bir sürümü kullanıyorsanız projeniz tam olarak çalışmayacaktır.Aşağıdaki adımları yaparak tekrardan deneyiniz.
** “create_proj.tcl” dosyasını notepade ya txt dosyası şeklinde açarak  “set scripts_vivado_version "2023.1" ” yazan satırda 2023.1 yerine kullandığınız sürümü yazınız.
** src/tcl/bd.tcl dosyasını notepade ya txt dosyası şeklinde açarak “set scripts_vivado_version "2023.1" ” yazan satırda 2023.1 yerine kullandığınız sürümü yazınız.

5. Tasarım Diagramı penceresi gerekli işlemler bittikten sonra otomatik açılacaktır.Eğer otomatik olarak açılmadıysa blok tasarımına çift tıklayarak açabilirsiniz.
   
6. Diagramdaki IP’leri ve bağlantılarını inceleyiniz.

7. AXI4-Stream arayüzünü anlamak için simülasyonu çalıştırınız. 
(Run Simulation > Run Behavioral Simulation)

8. AXI4-Stream'de Video Girişinin çıkışında geçerli verilere sahip olmaya başladığı zamanı bulun
 (yükselen kenar m_axis_tvalid)

9. wr_data_count_i sinyali, AXI4S IP'ye Video Girişinin dahili bir sinyalidir ve kaç tane veri kelimesinin hazır olduğunu gösterir (dahili FIFO'da).Bu sinyali 16661.664403us ve 16674.716851us simülasyon zamanları arasında kontrol edin.


10. hsync_out ve m_axis_video_tlast sıklığını kontrol edin. Her iki sinyalin de aynı frekansta gerçekleştiğini ve her ikisinin de bir çizginin sınırını gösterdiğini görebilirsiniz.




