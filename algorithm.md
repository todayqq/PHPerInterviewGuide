> 本书的 GitHub 地址：https://github.com/todayqq/PHPerInterviewGuide

算法可以说是大厂的必考题，对于算法，一定要理解其中的精髓、原理。

- 冒泡排序

冒泡排序的原理：一组数据，比较相邻数据的大小，将值小数据在前面，值大的数据放在后面。

```
function bubble_sort($arr)  
{  
    $count = count($arr);  
    if (0 == $count) {
        return false;  
    }

    for($i = 0; $i < $count; $i++){  
        for($j = 0; $j< $count-1-$i; $j++){
          　　if($arr[$j] > $arr[$j+1]){
              　　$temp        = $arr[$j];
              　　$arr[$j]     = $arr[$j+1];
              　　$arr[$j+1]   = $temp;
         　　}
   　　 }
    }  
    return $arr;  
} 
```

这样的一个数组 `array(6, 3, 8, 2, 9, 1)`，排序过程是怎样的？细节问题不在过多论述，有兴趣可以从扩展阅读中寻找答案。

- 快速排序

快速排序是对冒泡排序的一种改进。

实现过程是：

1. 先从数列中取出一个数作为基准数。
2. 分区过程，将比这个数大的数全放到它的右边，小于或等于它的数全放到它的左边。
3. 再对左右区间重复第二步，直到各区间只有一个数。

```	
function quick_sort(array $list) {
    $len = count($list);
    if ($len <= 1) {
        return $list;
    }
    $pivotValue = $list[0];
    $left = array();
    $right = array();
    for ($i = 1; $i < $len; $i++) { 
        if ($list[$i] < $pivotValue) {
            $left[] = $list[$i];
        }else{
            $right[] = $list[$i];
        }
    }
    $left = quick_sort($left);
    $right = quick_sort($right);
    return array_merge($left, array($pivotValue), $right);
}
```

- 二分查找（折半查找）

实现思想：将表中间位置记录的关键字与查找关键字比较，如果两者相等，则查找成功；否则利用中间位置记录将表分成前、后两个子表，如果中间位置记 录的关键字大于查找关键字，则进一步查找前一子表，否则进一步查找后一子表。

```
function binSearch($arr, $target){  
    $height = count($arr)-1;  
    $low = 0;  

    while($low <= $height){  
        $mid = floor(($low+$height)/2);//获取中间数

        //两值相等，返回 
        if($arr[$mid] == $target){  
            return $mid; 

        //元素比目标大，查找左部 
        } elseif ($arr[$mid] < $target){
            $low = $mid + 1;  

        //元素比目标小，查找右部
        } elseif ($arr[$mid] > $target){  
            $height = $mid - 1;  
        }  
    }  
    return "查找失败";  
}
```

### 扩展阅读

- [PHP 冒泡排序](https://www.cnblogs.com/wgq123/p/6529450.html)
- [php四种基础算法](http://www.php100.com/html/php/rumen/2013/1029/6333.html)
- [PHP实现各种经典算法](https://www.cnblogs.com/hellohell/p/5718175.html)
- [PHP常见算法-面试篇](http://www.cnblogs.com/zswordsman/p/5824599.html)
- [php实现二分查找法](https://www.cnblogs.com/wangjingwangjing/p/5206711.html)
