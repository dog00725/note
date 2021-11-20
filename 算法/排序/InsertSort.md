### InsertSort

#### 基本思路

将排序序列分为排序序列和未排序列，选择为排序列的元素插入到排序序列中对应的位置

#### 实现

```java
    public static void sort(Comparable[] comparables){
        if (null == comparables || comparables.length == 0){
            return;
        }
        int length = comparables.length;
        for(int i = 0; i<length;i++){
            for(int j = 0;j<i;j++){
                if (!less(comparables[j],comparables[i])){
                    exch(comparables,i,j);
                }
            }
        }
	}
```

