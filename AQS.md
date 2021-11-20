#### AQS

**重要的字段**

```java
//同步状态state>0则有锁，每次加锁+1，解锁-1
private volatile int state;
//等待队列的头节点(可理解为当前执行的节点)
private transient volatile Node head;
//等待队列的尾部节点
private transient volatile Node tail;
```



**获取锁**

```java
public final void acquire(int arg) {
    if (!tryAcquire(arg) && acquireQueued(addWaiter(Node.EXCLUSIVE), arg))
        selfInterrupt();
}
```

上述代码执行流程：

1. `tryAcquire()`尝试获取锁
2. 当获取锁失败时，`addWaite()`封装等待结点。`acquireQueued()`加入等待队列。
3. 线程终端阻塞

