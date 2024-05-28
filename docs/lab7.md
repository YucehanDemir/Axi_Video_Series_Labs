# Debugging the AXI4-Stream to Video Out

## HEDEFLER:

Bu laboratuvarı tamamladığınızda şunları öğreneceksiniz.

## ADIMLAR:
> - Note 1: This tutorial is intended to be used only with Vivado 2018.1 and only in simulation
> - Note 2: A valid license for the Test Pattern Generator is required to build the designs.

  ### Projeyi aç

1. XVES_0008 dosyasını indiriniz.

2. Vivado 2018.1’i çalıştırınız.

3. Açılan pencerede “Tcl Console” kısmında “Type a Tcl Command here” yazan yere indirmiş olduğumuz dosyanın dizinini “cd” yazarak giriniz.( XVES_0008  klasörüne kadar) 
(cd <path>/XVES_0008)

4. “ create_proj.tcl ” betiğini “source ./” yazarak giriniz.

   ### Simülasyonun Çalıştırılması ve Analizi

6. Davranışsal simülasyonu başlatın ( Simülasyonu Çalıştır > Davranışsal Simülasyonu Çalıştır )

7. Simülasyonu 150 ms boyunca çalıştırın.

8. Düşük akış sinyalinin değiştiğini (bazı zamanlar yüksek) ve AXI4-Stream to Video out IP'nin birinci çeyrekte kilitlenmediğini görebiliriz.

   ![image](https://github.com/YucehanDemir/Axi_Video_Series_Labs/assets/144496589/108fc98f-ddf7-4372-9836-2a55d65a87f9)




