# Testlerin açıklamaları


## İyileştirilen alanlar 
+ Constant dosyası oluşturması sayesinde magic string'lerden kurtulduk. Ayrıca bir değişkenin değişmesi durumunda constants dosyasından müdahale ederek değişimi saniyeler içerisinde kontrol edebilir hale geldik. 

+ Getdata() sayesinde aynı test içerisinde kullanacağımız farklı parametreleri magic string etmekten kurtulmanın yanı sıra parametrize decorator'ünün kullanıldığı alanlarda'da yazımı ve okumayı kolaylaştırdık. 

+ Parametrize decorator'ünün bulunduğu alanlarda her parametrenin screenshot'ını dosya adının aynı olması sebebiyle ayrı ayrı alamazken, fonksiyonu yazarken kullandığımız değişkenleri koda ekleyerek her bir parametre değişikliğinde farklı ss almasını sağladık. 

        BEFORE 
        self.driver.save_screenshot(f"{self.folderpath}\{inspect.currentframe().f_code.co_name}.png") 

        AFTER
         self.driver.save_screenshot(f"{self.folderpath}\{inspect.currentframe().f_code.co_name}{user,secret}.png") 
     

+ 5'i test olmak üzere 6 yeni test eklendi.


## Eklenen fonksiyonlar 

## Getdata():
Öncelikle var olan dosyamıza path vererek erişiyoruz. Satır sayısını bir değişkene atayıp bu sayıyla bir for döngüsü yazıyoruz. Satırları okuyup tuple'lar halinde for döngüsünden hemen önce oluşturduğumuz boş listeye ekleyip listeyi return'lüyoruz. Parametrize decoratorunu kullanacağımız testlerde oldukça işimize yarayacak ve zaman kaybını önleyecek fonksiyonumuz hazır.

## test_none_user("kullaniciadi,sifre",Getdata())
Bu testte kayıtlı olmayan kullanıcı ad ve şifrelerii girerek kullanıcıya verilen uyarı mesajının doğruluğu test ediliyor. Önceikle id'si ile username kutucuğunu bekliyoruz. Sonrasında
elementin üzerine gelip, tıklayıp kullanıcı adını girmekten oluşan action chaini oluşturup perform ediyoruz. Aynı işlemleri password kısmı için de tekrarladıktan sonra login butonunu bulup tıklatıyoruz. Assert işleminden önce ekran görüntümüzü alıyoruz. Ekrana gelen uyarı mesajı ile bizim beklediğimiz mesajı assertlüyüruz. Fonksiyondan önce tanımladığımız parametrize decorator'ü içerisindegi Getdata() sayesinde çok kez farklı ikilileri bu testten geçirebiliyoruz.

## test_twitter_btn_ctrl(self):
Bu testte içerideki twitter butonunun ilgili sayfaya yönlendirip yönlendirmediğini kontrol ediyoruz. Önceikle id'si ile username kutucuğunu bekliyoruz. Sonrasında
elementin üzerine gelip, tıklayıp kullanıcı adını girmekten oluşan action chaini oluşturup perform ediyoruz. Aynı işlemleri password kısmı için de tekrarladıktan sonra login butonunu bulup tıklatıyoruz. Twitter butonunun gelmesini bekledikten sonra butona tıklatıyoruz. Yeni sayfanın açılmasını beklemek için webdriverwait yapısını ve koşullardan number_of_windows_to_be()'yi kullanıyoruz. Ardından for döngüsü ile bulunduğumuz sekmede isek sekmeyi değiştirmesini istediğimiz bir if yapısı kuruyoruz.
Current_url adında bir değişken oluşturup anlık olarak driver'ın bulunduğu sayfanın url'ini burata atıyoruz. Sayfanın screenshot'ını aldıktan sonra Current_url, constants dosyamızda önceden atamış olduğumuz beklenen url ile mi başlıyor kontrol etmek için assert'lüyoruz.

## test_fb_btn_ctrl(self):
Bu testte içerideki facebook butonunun ilgili sayfaya yönlendirip yönlendirmediğini kontrol ediyoruz. Önceikle id'si ile username kutucuğunu bekliyoruz. Sonrasında
elementin üzerine gelip, tıklayıp kullanıcı adını girmekten oluşan action chaini oluşturup perform ediyoruz. Aynı işlemleri password kısmı için de tekrarladıktan sonra login butonunu bulup tıklatıyoruz. Facebook butonunun gelmesini bekledikten sonra butona tıklatıyoruz. Yeni sayfanın açılmasını beklemek için webdriverwait yapısını ve koşullardan number_of_windows_to_be()'yi kullanıyoruz. Ardından for döngüsü ile bulunduğumuz sekmede isek sekmeyi değiştirmesini istediğimiz bir if yapısı kuruyoruz.
Current_url adında bir değişken oluşturup anlık olarak driver'ın bulunduğu sayfanın url'ini burata atıyoruz. Sayfanın screenshot'ını aldıktan sonra Current_url, constants dosyamızda önceden atamış olduğumuz beklenen url ile mi başlıyor kontrol etmek için assert'lüyoruz.

## test_linkedin_btn_ctrl(self):
Bu testte içerideki linkedin butonunun ilgili sayfaya yönlendirip yönlendirmediğini kontrol ediyoruz. Önceikle id'si ile username kutucuğunu bekliyoruz. Sonrasında
elementin üzerine gelip, tıklayıp kullanıcı adını girmekten oluşan action chaini oluşturup perform ediyoruz. Aynı işlemleri password kısmı için de tekrarladıktan sonra login butonunu bulup tıklatıyoruz. Linkedin butonunun gelmesini bekledikten sonra butona tıklatıyoruz. Yeni sayfanın açılmasını beklemek için webdriverwait yapısını ve koşullardan number_of_windows_to_be()'yi kullanıyoruz. Ardından for döngüsü ile bulunduğumuz sekmede isek sekmeyi değiştirmesini istediğimiz bir if yapısı kuruyoruz.
Current_url adında bir değişken oluşturup anlık olarak driver'ın bulunduğu sayfanın url'ini burata atıyoruz. Sayfanın screenshot'ını aldıktan sonra Current_url, constants dosyamızda önceden atamış olduğumuz beklenen url ile mi başlıyor kontrol etmek için assert'lüyoruz.

## test_item_names(self):
Bu testte inventory alanındaki her ürün "Sauce labs" ile mi başlıyor kontrolü yapıyoruz. Önceikle id'si ile username kutucuğunu bekliyoruz. Sonrasında
elementin üzerine gelip, tıklayıp kullanıcı adını girmekten oluşan action chaini oluşturup perform ediyoruz. Aynı işlemleri password kısmı için de tekrarladıktan sonra login butonunu bulup tıklatıyoruz. Ürün adları adında bir değişken yanımlayıpiçerisinde class name ile ürünleri bulduruyoruz. Sayfamızın screenshot'ını aldıktan sonra for döngüsü ile her ürünün adını gezmek için .text kullanarak startswith ile beklenen veriyi assert'lüyoruz.
