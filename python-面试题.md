## python

1. \_\_new\_\_和\_\_init\_\_区别

   ```python
   class object:
      	@staticmethod 
       def __new__(cls, *more): 
           """创建并返回对象"""
           pass
   	  def __init__(self): # known special case of object.__init__
           """ 初始化对象"""
           pass
         
   # @staticmethod 将方法转换为静态方法
   ```

   

2. 列出5个标准库

   ```python
   haslib math random re functools
   ```

   

3. 字典删除一个键

   ![image-20200225145008555](/Users/xuyingjie/Library/Application Support/typora-user-images/image-20200225145008555.png)

   ```
   将 dict[key] 从 dict 中移除。如果映射中不存在 key 则会引发KeyError。
   ```

4. 合并两个字典

   ![image-20200225150623374](/Users/xuyingjie/Library/Application Support/typora-user-images/image-20200225150623374.png)

5. 列表去重

   ```
   set([11,22,33,44,55,66,11])
   ```

6. 将两个数组转化为一个字典

   ![image-20200225153740637](/Users/xuyingjie/Library/Application Support/typora-user-images/image-20200225153740637.png)

7. python内建数据类型

   ```
   数字类型: int,float,complex
   迭代器类型: 
   序列类型:list, tuple, range
   文本序列类型: str
   二进制序列类型:
   集合类型: set, frozenset
   映射类型: dict
   上下文管理类型:
   ```

8. Flask定义一个路由接口的几种方式

   

9. 合并两个有序数组

   

10. 交集,差集,并集

    ![image-20200225153029626](/Users/xuyingjie/Library/Application Support/typora-user-images/image-20200225153029626.png)

11. 读取excel文件

12. 读取csv文件

    ```python
    import csv
    with open('names.csv', newline='') as csvfile:
        reader = csv.DictReader(csvfile) 
        for row in reader:
        		print(row['first_name'], row['last_name'])
    ```

    

13. pandas如何处理特定行累加及列累加

14. pandas如何处理数据中的空行及空值

15. 业务("题目看不懂")

    ```python
    
    ```

    

16. 服务器文件查找

17. http状态码

    ```
    1**	信息，服务器收到请求，需要请求者继续执行操作
    2**	成功，操作被成功接收并处理
    3**	重定向，需要进一步的操作以完成请求
    4**	客户端错误，请求包含语法错误或无法完成请求
    5**	服务器错误，服务器在处理请求的过程中发生了错误
    ```

    

18.常见传输协议

```
FTP HTTP SMTP DNS
TCP UDP
IP
```

19. Linux服务器性能查看

    ```shell
    # 1. 查看物理cpu个数：
    cat /proc/cpuinfo |grep "physical id"|sort|uniq|wc -l
    # 2. 查看每个物理cpu中的core个数：
    cat /proc/cpuinfo |grep "cpu cores"|wc -l
    # 3. 逻辑cpu的个数：
    cat /proc/cpuinfo |grep "processor"|wc -l
    # 物理cpu个数*核数=逻辑cpu个数（不支持超线程技术的情况下）
    
    # 4. 查看内存使用情况：
    free -m
    # 5. 查看硬盘及分区信息：
    fdisk -l
    # 6. 查看文件系统的磁盘空间占用情况：
    df -h
    # 7. 查看硬盘的I/O性能（每隔一秒显示一次，显示5次）：
    iostat -x 1 5
    # 8. 查看linux系统中某目录的大小：
    du -sh /root
    
    ```

     

20. 查看linux占用内存/cpu最多的进程

    ```shell
    # 使用内存最多的10个进程     
    ps -aux | sort -k4nr | head -n 10
     
    # 使用CPU最多的10个进程     
    ps -aux | sort -k3nr | head -n 10
    ```

21. 防火墙iptables配置如何限定入站和出站

    ```
    第一种情况：入站数据流向
           从外界到达防火墙的数据包，先被PREROUTING规则链处理（是否修改数据包地址等），之后会进行路由选择（判断该数据包应该发往何处），如果数据包 的目标主机是防火墙本机（比如说Internet用户访问防火墙主机中的web服务器的数据包），那么内核将其传给INPUT链进行处理（决定是否允许通 过等），通过以后再交给系统上层的应用程序（比如Apache服务器）进行响应。
           
     第二冲情况：转发数据流向
           来自外界的数据包到达防火墙后，首先被PREROUTING规则链处理，之后会进行路由选择，如果数据包的目标地址是其它外部地址（比如局域网用户通过网 关访问QQ站点的数据包），则内核将其传递给FORWARD链进行处理（是否转发或拦截），然后再交给POSTROUTING规则链（是否修改数据包的地 址等）进行处理。
           
    第三种情况：出站数据流向
           防火墙本机向外部地址发送的数据包（比如在防火墙主机中测试公网DNS服务器时），首先被OUTPUT规则链处理，之后进行路由选择，然后传递给POSTROUTING规则链（是否修改数据包的地址等）进行处理。
    
    ```

22. Docker容器如何互相网络访问

    ```
    
    ```

23. Nginx负载均衡有哪些策略

    ```
    1. 轮询
    　　最基本的配置方法，上面的例子就是轮询的方式，它是upstream模块默认的负载均衡默认策略。每个请求会按时间顺序逐一分配到不同的后端服务器。
    2. weight
    　　权重方式，在轮询策略的基础上指定轮询的几率
    3. ip_hash(访客都固定访问一个后端服务器)
    　　指定负载均衡器按照基于客户端IP的分配方式，这个方法确保了相同的客户端的请求一直发送到相同的服务器，以保证session会话。这样每个访客都固定访问一个后端服务器，可以解决session不能跨服务器的问题。
    4. least_conn
    　　把请求转发给连接数较少的后端服务器。轮询算法是把请求平均的转发给各个后端，使它们的负载大致相同；但是，有些请求占用的时间很长，会导致其所在的后端负载较高。这种情况下，least_conn这种方式就可以达到更好的负载均衡效果。
    5. 第三方策略
    　　第三方的负载均衡策略的实现需要安装第三方插件。
    　　①fair
    　　    按照服务器端的响应时间来分配请求，响应时间短的优先分配。
    　　②url_hash
           按访问url的hash结果来分配请求，使每个url定向到同一个后端服务器，要配合缓存命中来使用。同一个资源多次请求，可能会到达不同的服务器上，导致不必要的多次下载，缓存命中率不高，以及一些资源时间的浪费。而使用url_hash，可以使得同一个url（也就是同一个资源请求）会到达同一台服务器，一旦缓存住了资源，再此收到请求，就可以从缓存中读取。
       
    ```

    