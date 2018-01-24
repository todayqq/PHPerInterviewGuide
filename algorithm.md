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

实现思想是：通过一趟排序将待排记录分割成独立的两部分，其中一部分的关键字均比另一部分记录的关键字小，则可分别对这两部分记录继续进行快速排序，整个排序过程可以递归进行，以达到整个序列有序的目的。

简单来说就是：找到当前数组中的任意一个元素（一般选择第一个元素），作为标的，新建两个空数组，遍历整个数组元素，如果遍历到的元素比当前的元素要小，那么就放到左边的数组，否则放到右面的数组，然后再对新数组进行同样的操作。

```
function quick_sort($arr) {
    $count = count($arr);
    if(1 >= $count) {
        return arr;
    }

    $base_num = $arr[0]; //选择标的
    $left_array = array();//小于标的
    $right_array = array();//大于标的

    for($i = 1; $i < $count; $i++) {
        if($base_num > $arr[$i]) {
            $left_array[] = $arr[$i];
        } else {
            $right_array[] = $arr[$i];
        }
    }
    //再分别对左边和右边的数组，进行相同的排序处理方式
    $left_array = quick_sort($left_array);
    $right_array = quick_sort($right_array);

    //最终合并
    return array_merge($left_array, array($base_num), $right_array);
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
- [php实现快速排序](https://www.cnblogs.com/wangjingwangjing/p/5241486.html)
- [PHP实现各种经典算法](https://www.cnblogs.com/hellohell/p/5718175.html)
- [PHP常见算法-面试篇](http://www.cnblogs.com/zswordsman/p/5824599.html)
- [php实现二分查找法](https://www.cnblogs.com/wangjingwangjing/p/5206711.html)
