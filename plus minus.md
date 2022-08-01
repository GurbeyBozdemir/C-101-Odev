```
public static void plusMinus(List<int> arr)
    {
        int pos = 0;
        int neg = 0;
        int zer = 0;
        int count = 0;
        foreach (int i in arr) {
            if (i < 0) {
                neg++;
                count++;
            } else if (i > 0) {
                pos++;
                count++;
            } else {
                zer++;
                count++;
            }
        }
        string a = ((double)pos/count).ToString("F6", CultureInfo.InvariantCulture);
        string b = ((double)neg/count).ToString("F6", CultureInfo.InvariantCulture);
        string c = ((double)zer/count).ToString("F6", CultureInfo.InvariantCulture);
        Console.WriteLine(a);
        Console.WriteLine(b);
        Console.WriteLine(c);

    }
```
