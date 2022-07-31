```
int total_cost;
        double tax_cost = meal_cost * tip_percent / 100;
        double tip_cost = meal_cost * tax_percent / 100;
        total_cost = Convert.ToInt32(meal_cost + tax_cost + tip_cost);
        Console.WriteLine(total_cost);
```
