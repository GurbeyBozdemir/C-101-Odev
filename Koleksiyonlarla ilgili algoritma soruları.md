### Soru 1
---
```
using System.Collections;

ArrayList asal = new ArrayList();
ArrayList asalDegil = new ArrayList();

Console.WriteLine("Aralarında boşluk bırakarak 20 adet pozitif sayı giriniz; ");
while (true)
{
start:
    try
    {
        int[] numbers = Console.ReadLine().Split(new Char[] { ' ' }, StringSplitOptions.RemoveEmptyEntries).Select(item => int.Parse(item)).ToArray();


        foreach (int number in numbers)
        {
            if (number < 0)
            {
                Console.WriteLine("Negatif sayı girdiniz, 20 adet pozitif sayı giriniz: ");
                goto start;
            }
        }
        for (int i = 0; i < numbers.Length; i++)
        {
            if (IsPrime(numbers[i]))
            {
                asal.Add(numbers[i]);
            }
            else
            {
                asalDegil.Add(numbers[i]);
            }
        }

        static bool IsPrime(int number)
        {
            if (number <= 1) return false;
            if (number == 2) return true;
            if (number % 2 == 0) return false;

            var boundary = (int)Math.Floor(Math.Sqrt(number));

            for (int i = 3; i <= boundary; i += 2)
                if (number % i == 0)
                    return false;

            return true;
        }





        asal.Sort();
        asalDegil.Sort();
        Array asalA = asal.ToArray();
        Array asalDegilA = asalDegil.ToArray();
        


        Console.WriteLine("Asal Sayılar: ");

        foreach (int j in asalA)
        {
            Console.WriteLine(j);
        }
        Console.WriteLine("Asal Olmayan Sayılar: ");
        foreach (int j in asalDegilA)
        {
            Console.WriteLine(j);
        }
        Console.WriteLine("Toplam {0} adet asal sayı bulundu.", asalA.Length);
        Console.WriteLine("Toplam {0} adet asal olmayan sayı bulundu.", asalDegilA.Length);

        int asalTop = 0;
        int asalDegilTop = 0;
        


        foreach (int x in asalA)
        {
            asalTop = asalTop + x;
        }
        foreach (int x in asalDegilA)
        {
            asalDegilTop = asalDegilTop + x;
        }
        int asalOrt = asalTop / asalA.Length;
        int asalDegilOrt = asalDegilTop / asalDegilA.Length;

        Console.WriteLine("Asal sayıların ortlaması: " + asalOrt);
        Console.WriteLine("Asal olmayan sayıların ortlaması: " + asalDegilOrt);



        Console.ReadLine();
        break;
    }
    catch (FormatException)
    {
        Console.WriteLine("Hatalı giriş yaptınız, 20 adet pozitif sayı giriniz: ");
        goto start;
    }
    catch (DivideByZeroException)
    {
        Console.WriteLine("Asal veya asal olmayan sayı olmadığından ortalama hesaplanamıyor, 20 adet pozitif sayı giriniz: ");
        asal.Clear();
        asalDegil.Clear();
        goto start;
    }
}
```
---
### Soru 2:
---
```
using System.Collections;

ArrayList buyukler = new ArrayList();
ArrayList kucukler = new ArrayList();
ArrayList sayilar = new ArrayList();

Console.WriteLine("Aralarında boşluk bırakarak 20 adet sayı giriniz; ");
while (true)
{
start:
    try
    {
        int[] numbers = Console.ReadLine().Split(new Char[] { ' ' }, StringSplitOptions.RemoveEmptyEntries).Select(item => int.Parse(item)).ToArray();

        for (int i = 0; i < numbers.Length; i++)
        {
            sayilar.Add(numbers[i]);
        }
        sayilar.Sort();
        buyukler.Add(sayilar[19]);
        buyukler.Add(sayilar[18]);
        buyukler.Add(sayilar[17]);
        kucukler.Add(sayilar[0]);
        kucukler.Add(sayilar[1]);
        kucukler.Add(sayilar[2]);





        buyukler.Sort();
        kucukler.Sort();
        Array buyuklerA = buyukler.ToArray();
        Array kucuklerA = kucukler.ToArray();



        Console.WriteLine("En büyük sayılar: ");

        foreach (int j in buyuklerA)
        {
            Console.WriteLine(j);
        }
        Console.WriteLine("En küçük sayılar: ");
        foreach (int j in kucuklerA)
        {
            Console.WriteLine(j);
        }

        int buyuklerTop = 0;
        int kucuklerTop = 0;



        foreach (int x in buyuklerA)
        {
            buyuklerTop = buyuklerTop + x;
        }
        foreach (int x in kucuklerA)
        {
            kucuklerTop = kucuklerTop + x;
        }
        int buyukOrt = buyuklerTop / buyuklerA.Length;
        int kucukOrt = kucuklerTop / kucuklerA.Length;
        int ortTop = buyukOrt + kucukOrt;

        Console.WriteLine("En büyük sayıların ortalaması: " + buyukOrt);
        Console.WriteLine("En küçük sayıların ortlaması: " + kucukOrt);
        Console.WriteLine("Ortalamaların toplamı: " + ortTop);

        Console.ReadLine();
        break;
    }
    catch (FormatException)
    {
        Console.WriteLine("Hatalı giriş yaptınız, 20 adet pozitif sayı giriniz: ");
        goto start;
    }
}
```
---
### Soru 3:
---
```
using System.Collections;

ArrayList sesli = new ArrayList();

Console.WriteLine("Bir cümle giriniz: ");

char[] girdi = (Console.ReadLine()).ToCharArray();

foreach (char c in girdi)
{
    if (c == 'a' || c == 'e' || c == 'ı' || c == 'i' || c == 'o' || c == 'ö' || c == 'u' || c == 'ü')
    {
        if (sesli.Contains(c))
        {
            break;
        }
        
        sesli.Add(c);
    }
}

sesli.Sort();
Console.WriteLine("Girilen cümledeki sesli harfler: ");
foreach (char c in sesli)
{
    Console.WriteLine(c);
}
```
