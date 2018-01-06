# comparing-monthly-revenue

## 寫法一:用foreach的寫法

```php
function compareRevenue($thisYear, $lastYear)
{
    $deltas = [];
    foreach ($lastYear as $month => $monthlyRevenue) {
        $deltas[] = $thisYear[$month] - $monthlyRevenue;
    }
    return $deltas;
}
```

## 寫法二:用zip的寫法
```php
function compareRevenue($thisYear, $lastYear)
{
    return collect($thisYear)->zip($lastYear)->map(function ($thisAndLast) {
        return $thisAndLast[0] - $thisAndLast[1];
    }); 
}
```