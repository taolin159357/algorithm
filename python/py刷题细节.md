* py的join函数返回通过指定字符连接序列中元素后生成的新字符串。

  ```python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-
   
  str = "-";
  seq = ("a", "b", "c"); # 字符串序列
  print str.join( seq );
  ```

* py的for in用法：经常用于遍历字符串、列表，元组，字典与迭代器等，还能直接生成列表

* py的格式化字符串函数str.format()，它增强了字符串格式化的功能，基本语法是通过{}和:来代替以前的%

* py3类型检查一般使用typing模块，关键字有int,long,float,bool,str,List, Tuple, Dict, Set,Iterable,Iterator,Generator

* 语法糖：for _ in range(n)中_ 是占位符

* deque类是python标准库collections模块中的一项，pop与popleft,append与appendleft,extendleft与extend；除此之外，还有queue模块，示例如下

  ```python
  import queue
  class MaxQueue:
  
      def __init__(self):
          self.deque = queue.deque()
          self.queue = queue.Queue()
  
      def max_value(self) -> int:
          return self.deque[0] if self.deque else -1
  
  
      def push_back(self, value: int) -> None:
          while self.deque and self.deque[-1] < value:
              self.deque.pop()
          self.deque.append(value)
          self.queue.put(value)
  
      def pop_front(self) -> int:
          if not self.deque:
              return -1
          ans = self.queue.get()
          if ans == self.deque[0]:
              self.deque.popleft()
          return ans
  ```

* str.split(str="", num=string.count(str))；num -- 分割次数，默认为 -1, 即分隔所有。

* py的排序：list.sort( key=None, reverse=False)；sorted(iterable, key=None, reverse=False)  ；key对应的都可以多级排序，如

  ```python
  new_para = sorted(para.items(), key=lambda x: (x[1], x[0]))
  # key仅仅支持一个参数，就无法实现两个参数之间的对比，采用cmp_to_key 函数，可以接受两个参数，将两个参数做处理
  from functools import cmp_to_key 
  L=[9,2,23,1,2]
   
  sorted(L,key=cmp_to_key(lambda x,y:y-x))
  输出：
  [23, 9, 2, 2, 1]
  # 可使用tuple依次排序，力扣937
  def reorderLogFiles(self, logs: List[str]) -> List[str]:
      def compare(log):
          a, b = log.split(" ", 1)
          return (0, b, a) if b[0].isalpha() else (1,)
      logs.sort(key = compare)
      return logs
  ```

* infinty和-infinty

* Python itertools.chain(*iterable)：chain函数参数加\*表示去除 iterable 里的内嵌 iterable，不加\*表示合并

* py中的小根堆：heapq.heapify(q)；若要建大根堆，可以加负号。往里塞元素：heapq.heappush(q,1)；往外弹元素：heapq.heappop(q)；

* python bisect模块的使用

  ```python
  import bisect
   
  L = [1,3,3,6,8,12,15]
  x = 3
   
  x_insert_point = bisect.bisect_left(L,x)　　#在L中查找x，x存在时返回x左侧的位置，x不存在返回应该插入的位置..这是3存在于列表中，返回左侧位置１
  print x_insert_point
   
  x_insert_point = bisect.bisect_right(L,x)  #在L中查找x，x存在时返回x右侧的位置，x不存在返回应该插入的位置..这是3存在于列表中，返回右侧位置３
   
  print x_insert_point
   
  x_insort_left = bisect.insort_left(L,x)  #将x插入到列表L中，x存在时插入在左侧
  print L
   
  x_insort_rigth = bisect.insort_right(L,x) #将x插入到列表L中，x存在时插入在右侧　　　　
   
  print L
  
  结果：
  1
  3
  [1, 3, 3, 3, 6, 8, 12, 15]
  [1, 3, 3, 3, 3, 6, 8, 12, 15]
  ```


* zip() 函数用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的列表。

  ```python
  >>> a = [1,2,3]
  >>> b = [4,5,6]
  >>> c = [4,5,6,7,8]
  >>> zipped = zip(a,b)     # 打包为元组的列表
  [(1, 4), (2, 5), (3, 6)]
  >>> zip(a,c)              # 元素个数与最短的列表一致
  [(1, 4), (2, 5), (3, 6)]
  >>> zip(*zipped)          # 与 zip 相反，*zipped 可理解为解压，返回二维矩阵式
  [(1, 2, 3), (4, 5, 6)]
  ```

  
