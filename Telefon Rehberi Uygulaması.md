## Telefon Rehberi Uygulaması
```
using System.Collections;


    //"RehberListesi" adlı liste oluşturuluyor
    List<Kisi> RehberListesi = new List<Kisi>();

    //Rehbere 5 kişinin numarası varsayılan olarak ekleniyor
    RehberListesi.Add(new Kisi("Gürbey", "Bozdemir", 1112223344));
    RehberListesi.Add(new Kisi("Ali", "Bozdemir", 2223334455));
    RehberListesi.Add(new Kisi("Veli", "Bozdemir", 3334445566));
    RehberListesi.Add(new Kisi("Süleyman", "Tezuran", 4445556677));
    RehberListesi.Add(new Kisi("Nuran", "Tezuran", 5556667788));


start:
try
{
    //Uygulama ilk başladığındaki işlem menüsü
    Console.WriteLine("Lütfen yapmak istediğiniz işlemi seçiniz :)");
    Console.WriteLine("*******************************************");
    Console.WriteLine("(1) Yeni Numara Kaydetmek");
    Console.WriteLine("(2) Varolan Numarayı Silmek");
    Console.WriteLine("(3) Varolan Numarayı Güncelleme");
    Console.WriteLine("(4) Rehberi Listelemek");
    Console.WriteLine("(5) Rehberde Arama Yapmak");

    //Kullanıcının seçimi alınır
    string secim = Console.ReadLine();

    //Seçime göre yönlendirme yapılır
    if (secim == "1")
    {
        Console.WriteLine("Lütfen isim giriniz             :");
        string isim = Console.ReadLine();
        Console.WriteLine("Lütfen soyisim giriniz          :");
        string soyisim = Console.ReadLine();
        Console.WriteLine("Lütfen telefon numarası giriniz :");
        Int64 telNo = Convert.ToInt64(Console.ReadLine());

        //Girilen bilgiler yeni bir kişi olarak rehbere eklenir.
        RehberListesi.Add(new Kisi(isim, soyisim, telNo));
        Console.WriteLine(isim + " " + soyisim + " " + "Kişisi rehbere eklendi");
        Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
        Console.ReadKey();
        goto start;
    }
    if (secim == "2")
    {
    silmeSorgu:
        Console.WriteLine("Lütfen numarasını silmek istediğiniz kişinin adını ya da soyadını giriniz:");
        string silinecekIsim = Console.ReadLine();

        //Silinecek kişi rehberde aranır
        var aranan = RehberListesi.Find(item => item.ad == silinecekIsim);
        var arananSoyad = RehberListesi.Find(item => item.soyad == silinecekIsim);
        if (aranan == null && arananSoyad == null)
        {
            Console.WriteLine("Aradığınız krtiterlere uygun veri rehberde bulunamadı. Lütfen bir seçim yapınız.");
            Console.WriteLine("* Silmeyi sonlandırmak için : (1)");
            Console.WriteLine("* Yeniden denemek için      : (2)");
            string yanit = Console.ReadLine();
            if (yanit == "2")
                goto silmeSorgu;
            else
            {
                Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
                Console.ReadKey();
                goto start;
            }
        }
        Console.WriteLine(silinecekIsim + " isimli kişi rehberden silinmek üzere, onaylıyor musunuz ? (y / n)");
        string cevap = Console.ReadLine();
        if (cevap == "y" && arananSoyad == null)
        {
            RehberListesi.Remove(aranan);
            Console.WriteLine(silinecekIsim + " silindi");
            goto start;
        }
        if (cevap == "y" && aranan == null)
        {
            RehberListesi.Remove(arananSoyad);
            Console.WriteLine(silinecekIsim + " silindi");
            Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
            Console.ReadKey();
            goto start;
        }
        if (cevap == "n")
        {
            Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
            Console.ReadKey();
            goto start;
        }
    }
    if (secim == "3")
    {
    degistirmeSorgu:
        Console.WriteLine("Lütfen numarasını güncellemek istediğiniz kişinin adını ya da soyadını giriniz:");
        string degistirilecekIsim = Console.ReadLine();

        //Numarası değiştirilecek kişi rehberde aranır
        var arananAd = RehberListesi.Find(item => item.ad == degistirilecekIsim);
        var arananSoyad = RehberListesi.Find(item => item.soyad == degistirilecekIsim);
        if (arananAd == null && arananSoyad == null)
        {
            Console.WriteLine("Aradığınız krtiterlere uygun veri rehberde bulunamadı. Lütfen bir seçim yapınız.");
            Console.WriteLine("* Silmeyi sonlandırmak için : (1)");
            Console.WriteLine("* Yeniden denemek için      : (2)");
            string yanit = Console.ReadLine();
            if (yanit == "2")
                goto degistirmeSorgu;
            else
            {
                Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
                Console.ReadKey();
                goto start;
            }
        }
        Console.WriteLine(degistirilecekIsim + " kişisinin yeni numarasını giriniz:");
        Int64 yeniNo = Convert.ToInt64(Console.ReadLine());
        Console.WriteLine(degistirilecekIsim + " isimli kişinin numarası güncellenmek üzere, onaylıyor musunuz ? (y / n)");
        string cevap = Console.ReadLine();
        if (cevap == "y" && arananAd == null)
        {
            var soyadi = arananSoyad.soyad;
            RehberListesi.Remove(arananSoyad);
            RehberListesi.Add(new Kisi(degistirilecekIsim, soyadi, yeniNo));
            Console.WriteLine(degistirilecekIsim + " numarası değiştirildi.");
            Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
            Console.ReadKey();
            goto start;
        }
        if (cevap == "y" && arananSoyad == null)
        {
            var adi = arananAd.ad;
            RehberListesi.Remove(arananAd);
            RehberListesi.Add(new Kisi(adi, degistirilecekIsim, yeniNo));
            Console.WriteLine(degistirilecekIsim + " numarası değiştirildi.");
            Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
            Console.ReadKey();
            goto start;
        }
        if (cevap == "n")
        {
            Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
            Console.ReadKey();
            goto start;
        }
    }
    
    if (secim == "4")
    {
        //Rehberin tümü yazdırılır
        Yazdir.TumunuYazdir(RehberListesi);
        Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
        Console.ReadKey();
        goto start;
    }
    if (secim == "5")
    {
    arama:
        Console.WriteLine("Arama yapmak istediğiniz tipi seçiniz.");
        Console.WriteLine("**********************************************");
        Console.WriteLine("İsim veya soyisime göre arama yapmak için: (1)");
        Console.WriteLine("Telefon numarasına göre arama yapmak için: (2)");

        string tercih = Console.ReadLine();
        if (tercih == "1")
        {
            //Ada göre rehberde arama yapılır, eşleşme olursa aranan kişi bilgileri yazdırılır.
            Console.WriteLine("Aranacak ismi yazın: ");
            string aranan = Console.ReadLine();
            var arananAd = RehberListesi.Find(item => item.ad == aranan);
            var arananSoyad = RehberListesi.Find(item => item.soyad == aranan);
            if (arananAd != null && arananSoyad == null)
            {
                KisiYazdir.KisiyiYazdir(arananAd);
            }
            if (arananSoyad != null && arananAd == null)
                KisiYazdir.KisiyiYazdir(arananSoyad);
            if (arananSoyad == null && arananAd == null)
            {
                Console.WriteLine("Aradığınız krtiterlere uygun veri rehberde bulunamadı. Lütfen bir seçim yapınız.");
                Console.WriteLine("* Aramayı sonlandırmak için    : (1)");
                Console.WriteLine("* Yeniden denemek için         : (2)");
                string yanit = Console.ReadLine();
                if (yanit == "2")
                    goto arama;
                else
                {
                    Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
                    Console.ReadKey();
                    goto start;
                }

            }
            else
            {
                Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
                Console.ReadKey();
                goto start;
            }
        }
        if (tercih == "2")
        {
            Console.WriteLine("Aranacak numarayı girin: ");

            Int64 arama = Convert.ToInt64(Console.ReadLine());

            var arananKisi = RehberListesi.Single(s => s.no == arama);

            KisiYazdir.KisiyiYazdir(arananKisi);
            Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
            Console.ReadKey();
            goto start;
        }
        
    }
    else
    {
        Console.WriteLine("Hatalı seçim yaptınız, başlangıç menüsüne dönmek için bir tuşa basınız.");
        Console.ReadKey();
        goto start;
    }
}

catch (Exception e)
{
    Console.WriteLine(e.Message);
    Console.WriteLine("Başlangıç ekranına dönmek için bir tuşa basınız.");
    Console.ReadKey();
    goto start;
}

//Rehberin tümü ekrana yazdırılır.
class Yazdir
{

    public static void TumunuYazdir(IList liste)
    {
        Console.WriteLine("Telefon Rehberi");
        Console.WriteLine("**********************************************");
        foreach (Kisi kisi in liste)
        {
            Console.WriteLine("isim: {0}", kisi.ad);
            Console.WriteLine("Soyisim: {0}", kisi.soyad);
            Console.WriteLine("Telefon Numarası: {0}", kisi.no);
            Console.WriteLine("-");
        }
    }
}

//Aranan kişiyi yazdırma
class KisiYazdir
{

    public static void KisiyiYazdir(Kisi arananKisi)
    {
        Console.WriteLine("Arama Sonuçlarınız:");
        Console.WriteLine("**********************************************");
        Console.WriteLine("isim: {0}", arananKisi.ad);
        Console.WriteLine("Soyisim: {0}", arananKisi.soyad);
        Console.WriteLine("Telefon Numarası: {0}", arananKisi.no);
        Console.WriteLine("-");
    }
}

//"Kisi" adlı rehber sınıfı oluşturuluyor.
class Kisi
{
    public Kisi(string ad, string soyad, Int64 no)
    {
        this.ad = ad;
        this.soyad = soyad;
        this.no = no;
    }

    public string ad { get; set; }
    public string soyad { get; set; }
    public Int64 no { get; set; }
}
```
