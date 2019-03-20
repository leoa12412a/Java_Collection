# Java Collection

## 關於Collection

在Java裡頭除了陣列可以幫我們處理資料以外，再來就是Collection API中的元件了。Collection(集合)就是一個設計用來處理多個資料物件，而存放在集合中的物件我們把他稱之為Elements(元素)，在程式運行時，有時需要一個地方暫存產生出來的物件，這個地方我們就稱為Container(容器)。然而在java.util.Collection介面中定義了所有集合最基本的存取方式如下圖:</br>
![image]()</br></br>

## 解析 Collection interface

Collection interface分別繼承了另外3個interface分別是Set(集合)、List、Queue(佇列)，下面對這三個interface也有簡單的介紹:</br>

  * Set : 不允許相同物件存在的集合結構ex:HashSet、TreeSet
  * List : 循序索引的串列結構ex:ArrayList、LinkedList
  * Queue : 使用 Key-Value(鍵-值) 方式儲存的結構ex:HashMap、TreeMap
  
## Collection - List 

List算是在應用程式裡最常見的，List代表的就是所謂清單列表，最大的特點就是依序的放入以及取出，且具有順序性，List的實作類別有ArrayList、LinkedList、Vector

### ArrayList
