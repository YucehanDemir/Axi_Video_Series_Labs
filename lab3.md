# Bir görüntü dosyasından (PPM) girişle RTL simülasyonu:


## HEDEFLER:
Bu laboratuvarı tamamladığınızda şunları öğreneceksiniz.

1.PPM Dosya Formatı ve Yapısı

2.GIMP Kullanımı ile PPM Görüntüleme

3.VHDL-Verilog ile Dosya Okuma

4.PPM dosyasındaki piksel verilerini okuyarak bu verileri RTL simülasyonunda kullanma

## ADIMLAR:
### Projeyi aç
1. XVES_0003 dosyasını indiriniz.

2. Vivado 2023.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0003  klasörüne kadar) 
(cd <path>/XVES_0003)

4.
   - VHDL Projesi için;
   
   ``` create_proj_VHDL.tcl (source ./create_proj_VHDL.tcl)    ```
 
   - Verilog Projesi için; 
   
   ``` create_proj_Verilog.tcl (source ./create_proj_Verilog.tcl)    ```

   > ### NOT: 
> Vivado sürümünü 2023.1’den başka bir sürümü kullanıyorsanız projeniz tam olarak çalışmayacaktır.Aşağıdaki adımları yaparak tekrardan deneyiniz.
> - “create_proj.tcl” dosyasını notepade ya txt dosyası şeklinde açarak  “set scripts_vivado_version "2023.1" ” yazan satırda 2023.1 yerine kullandığınız sürümü yazınız.

![create_proj_tcl](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/94c04af6-2875-4774-b3e2-6d276821eb6f)

  
> - "src/tcl/bd.tcl" dosyasını notepade ya txt dosyası şeklinde açarak “set scripts_vivado_version "2023.1" ” yazan satırda 2023.1 yerine kullandığınız sürümü yazınız.

![bd_tcl](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/7d76b814-60ad-4244-b7c3-ea5f005ee9c3)

### Giriş dosyasını projeye ekleyin 

5. XVES_0003/img/image_2.ppm dosyasını bir metin düzenleyiciyle açınız.
> Notlar:

> - Bu, yorum satırı olmadan image_1.ppm ile aynı dosyadır. (bu test tezgahı, giriş dosyasındaki yorum satırını desteklemez).

> - Bu bir P3 PPM dosyasıdır. (ASCII kodlu PPM)

> - Genişlik ve yükseklik aynı satırda boşluk karakteriyle ayrılmıştır.

> - Her satırda yalnızca bir bileşen vardır.

6. Vivado'da bu dosyayı simülasyon kaynak dosyalarına ekleyin.

I. Dosya > Kaynak Ekle… > Simülasyon kaynakları ekle veya oluştur öğesine tıklayın.
![1-](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/c95c4394-c968-41e2-b66a-05b8a0b89e99)

II. Dosya ekle'yi tıklayın.

III. Dosya türünü Tüm Dosyalar olarak değiştirin ve image_2.ppm öğesini seçin . Tamam'ı tıklayın.

![2](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/ab2be932-58b8-442c-a081-e46dbb9a2e4a)

### Simülasyonun Çalıştırılması ve Analizi

7. AXI4-Stream arayüzünü anlamak için simülasyonu çalıştırınız. 
(Run Simulation > Run Behavioral Simulation)

8. Tcl konsolunda test tezgahı tarafından yazdırılan bilgileri “Not:” ile başlayarak bulabilirsiniz.
- Piksel 1 değerini yazdıran satırı bulun (Not: Piksel #1: …). İlk piksele ait kırmızı (255), yeşil (0) ve mavi (0) bileşenlerin değerlerinin olduğunu görebiliriz. Bu değerler GIMP'de gözlemlediklerimizle eşleşen kırmızı bir piksele karşılık gelir.

9. Simülasyonu kapat

###Giriş dosyasını değiştirin

10. XVES_0003/img/image_3.ppm dosyasını proje simülasyon kaynak dosyalarına ekleyin.
    
11.Test tezgahı dosyasını metin düzenleyicide açın ve aşağıdaki satırı bulun.

VHDL
constant    file_path_c : string := "image_2.ppm";
Verilog
reg[8*11:1] file_name = "image_2.ppm";

![4-](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/c3c398f0-db04-45cb-be8b-5c3c85cd4b0f)

Yukarıdaki kodu aşağıdaki gibi değiştiriniz.
- VHDL
constant    file_path_c : string := "image_3.ppm";
- Verilog
reg[8*11:1] file_name = "image_3.ppm";

![5-](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/8806b1e2-8904-4a9e-8925-98ec5b189b68)

12. Davranışsal simülasyonu başlatın.

13. Dalga formu penceresinde, yeni görüntü girişinin boyutunu sinyal değerleri olarak görebilirsiniz.

![6-](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/ddc90161-c74d-4852-9f7c-95efe2f4b2a3)

