### Cevap 1)
---
```
Console.WriteLine("Pozitif bir sayı giriniz: ");
int sayi = Convert.ToInt32(Console.ReadLine().Trim());

Console.WriteLine("{0} Adet pozitif sayı giriniz: ", sayi);

List<int> arr = Console.ReadLine().TrimEnd().Split(' ').ToList().Select(arrTemp => Convert.ToInt32(arrTemp)).ToList();

foreach (int num in arr) {
    if (num % 2 == 0) {
        Console.WriteLine(num);
    }
}
```

### Cevap 2)
---
```
Console.WriteLine("2 Adet pozitif sayı giriniz: ");
List<int> arr = Console.ReadLine().TrimEnd().Split(' ').ToList().Select(arrTemp => Convert.ToInt32(arrTemp)).ToList();

Console.WriteLine("{0} Adet pozitif sayı giriniz: ", arr[0]);
List<int> arr2 = Console.ReadLine().TrimEnd().Split(' ').ToList().Select(arr2Temp => Convert.ToInt32(arr2Temp)).ToList();
foreach (int num in arr2) {
    if (num % arr[1] == 0 || num == arr[1]) {
        Console.WriteLine(num);
    }
}
```

### Cevap 3)
---
```
Console.WriteLine("Pozitif bir sayı giriniz: ");
int sayi = Convert.ToInt32(Console.ReadLine());
Console.WriteLine("{0} Adet kelime giriniz: ", sayi);
List<string> arr = Console.ReadLine().TrimEnd().Split(' ').ToList();
arr.Reverse();

for (int i = 0; i < sayi; i++) {
    Console.WriteLine(arr[i]);
}
```

### Cevap 4)
---
```
int kelime = 0;
int harf = 0;
Console.WriteLine("Bir cümle giriniz: ");
List<string> arr = Console.ReadLine().TrimEnd().Split(' ').ToList();

kelime = arr.Count;
Console.WriteLine("Cümledeki toplam kelime sayısı: {0}", kelime);

for (int i = 0; i < arr.Count; i++) {
    harf = harf + arr[i].Length;
}
Console.WriteLine("Cümledeki toplam harf sayısı: {0}", harf);
```



