### BubbleSort

#### 基本思路

两两比较，每次循环都将最大移动到最右边

```java
    public static void sort(Comparable[] comparables){
        if (null == comparables || comparables.length == 0){
            return;
        }
        int length = comparables.length;
        for(int i=0;i < comparables.length-1;i++){
            for(int j=0;j<comparables.length-1-i;j++){
                if(less(comparables[j+1],comparables[j])){
                    exch(comparables,j,j+1);
                }
            }
        }
    }
```

#### 优化

