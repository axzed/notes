## 法一：无脑暴力

上来就排序，与位序不等就是缺的。

```go
func missingNumber(nums []int) int {
    sort.Ints(nums)
    for i, num := range nums {
        if num != i {
            return i
        }
    }
    return len(nums)
}
```



## 法二：异或

数组nums中本应该有n个数，这个时候我们把从0 ~ n的完整的n + 1个数加入到数组中。

这个时候数组中的个数有2 * n + 1个

缺少的数字只在后面新加的数组中出现一次

所以全部异或后就得出来缺少的那个数了

```go

func missingNumber(nums []int) (xor int) {
    for i, num := range nums {
        xor ^= i ^ num
    }
    return xor ^ len(nums)
}
```

