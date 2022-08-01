```
class Solution
{
    public static void Main(string[] args)
    {
        int N = Convert.ToInt32(Console.ReadLine().Trim());
        if (N % 2 != 0) {
            Console.WriteLine("Weird");
        } else if (2 <= N && N <= 5) {
            Console.WriteLine("Not Weird");
        } else if (6 <= N && N <= 20) {
            Console.WriteLine("Weird");
        } else {
            Console.WriteLine("Not Weird");
        }
    }
}
```
