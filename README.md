# seher_samsum_goruntuisleme_vize
Bu kod da ilk başta MediaPipe kütüphanesi kullanarak el tespiti ve el parmaklarının konumlarını belirleme işlemi yaptık.
Daha sonra Parmak Hareketleriyle Ekran Parlaklığı Kontrolü için koda ekleme yaptım.
Başparmak ile işaret parmak arasındaki mesafeye bağlı olarak bilgisayar ekranının parlaklığını ayarlamasını yaptım.
▪ Mesafe küçüldüğünde: Parlaklık azalacak.
▪ Mesafe büyüdüğünde: Parlaklık artacak.

İlk önce screen_brightness_control kütüphanesini ekledim.
Sonrasında try-except bloğunu kullandım.
Çünkü hataları yakalayıp programın çökmesini önlemek için kullandım.
Except kullandım çünkü  oluşan hatayı atlayıp programın çalışmasına devam etmesini sağlar.

Kullandığım kod ise şu şekilde:

İki Parmak Arasındaki Mesafeyi Hesaplama 
# uzaklik = int(np.hypot(x2-x1, y2-y1))
(Bu satırda x1, y1 işaret parmağının ucu, 
x2, y2 başparmağın ucu)

Parlaklığı Hesaplama ve Ayarlama
# parlaklik = int(np.interp(uzaklik, [min_uzaklik, max_uzaklik], [0, 100]))
(np.interp() fonksiyonunu kullandım .Bu satırda, mesafe arttıkça parlaklık da artar.)
# sbc.set_brightness(int(parlaklik))


Parlaklığı Ekrana Yazdırma
# cv2.putText(annotated_image, f"Parlaklik: {parlaklik}%",(xort, yort),cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 255, 0), 2)
(Görüntü üzerinde parlaklık değerini yazdırmak için.)

