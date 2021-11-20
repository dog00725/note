### SelcetSort

#### 基本思路

和插入排序类似，将序列分为排序序列和未排序序列。在未排序序列中选取最小的元素插入到排序序列的末尾

#### 实现

```java
    public static void sort(Comparable[] comparables){
        if (null == comparables || comparables.length == 0){
            return;
        }
        int length = comparables.length;
        for(int i=0;i<length;i++){
            int min = i;
            for(int j=i;j<length;j++){
                if(less(comparables[j],comparables[min])){
                    min = j;
                }
            }
            exch(comparables,i,min);
        }
    }
```

