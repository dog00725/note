### QuickSort ###

#### 基本思路

​		在排列对象中选择一个基准数，小于基准数的放在它左边，大于放在它右边。左右两边的数据继续按照此方式执行。

#### 代码实现

代码中会使用到的工具方法参看文末

```java

    public void sort(Comparable[] array){
        if (null == array || array.length == 0){
            return;
        }
        partition(array,0,array.length-1);
    }


    public void partition(Comparable[] array, int start, int end){
        if(start >= end){
            return;
        }
        //选择第一个数作为基准数
        Comparable key = array[start];
        int left = start+1;
        int right = end;
        while(left <= right){
            while(less(array[left],key)){
                if(++left >= end) break;
            }
            while(less(key,array[right])){
                if(--right <= start) break;
            }
            if (left >= right) break;
            exch(array,left,right);
        }
        //退出循环时，right > left  
        exch(array,start,right);
        partition(array,start,right-1);
        partition(array,right+1,end);
    }
```



#### 优化

* 上面实现对于重复的元素会出现划分不均的情况

  改进方式：三路划分

  实现：

```java
    public void partition(Comparable[] array, int start, int end){
        if(start >= end){
            return;
        }
        //选择第一个数作为基准数
        Comparable key = array[start];
        int lt = start;
        int i = lt + 1;
        int gt = end;
        while(i <= gt){
            int temp = array[i].comparareTo(key);
            if (temp < 0){
                exch(array,lt++,i++);
            }
            if(temp > 0){
                exch(array,i,lt--);
            }else{
                i++;
            }
        }
        partition(array,start,lt-1);
        partition(array,gt+1,end);
    }
```

* 当子序列较小可以适用插入排序

#### 工具方法

```Java
    private static boolean less(Comparable a, Comparable b){
        return a.compareTo(b) < 0;
    }

    private static void exch(Comparable[] a, int i, int j){
        Comparable temp = a[i];
        a[i] = a[j];
        a[j] = temp;
    }

    private static void show(Comparable[] a){
        for (int i = 0; i < a.length; i++) {
            System.out.print(a[i] + " ");
        }
        System.out.println();
    }
```

