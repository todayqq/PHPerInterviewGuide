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

实现思想是：每次选择一个相应的元素，然后将其放到指定的位置

```	
function select_sort($arr) {
//实现思路 双重循环完成，外层控制轮数，当前的最小值。内层 控制的比较次数
    //$i 当前最小值的位置， 需要参与比较的元素
    for($i=0, $len=count($arr); $i<$len-1; $i++) {
        //先假设最小的值的位置
        $p = $i;
        //$j 当前都需要和哪些元素比较，$i 后边的。
        for($j=$i+1; $j<$len; $j++) {
            //$arr[$p] 是 当前已知的最小值
            if($arr[$p] > $arr[$j]) {
     //比较，发现更小的,记录下最小值的位置；并且在下次比较时，
 // 应该采用已知的最小值进行比较。
                $p = $j;
            }
        }
        //已经确定了当前的最小值的位置，保存到$p中。
 //如果发现 最小值的位置与当前假设的位置$i不同，则位置互换即可
        if($p != $i) {
            $tmp = $arr[$p];
            $arr[$p] = $arr[$i];
            $arr[$i] = $tmp;
        }
    }
    //返回最终结果
    return $arr;
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
