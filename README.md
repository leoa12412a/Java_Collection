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

 * ArrayList : 執行緒不安全(不同步)，查詢速度快，但增加刪除慢，使用陣列
 * LinkedList : 增刪速度快，查詢慢，使用鏈結串列
 * Vector : 執行緒安全(同步)，但速度慢，已被 ArrayList替代

### ArrayList 和 LinkedList 的差異
所以List有的功能，ArrayList與LinkedList全都有；而這二個List的差別在於，尋找下一節點的位置與切換下一個節點的位置。下面以實際例子來解釋兩者差異。

假設今天三個物件分別要儲存在ArrayList 和 LinkedList會以下圖的方式進行儲存
ArrayList會按照順所有的物件，所以要選取特定(第N個)元素時，非常方便快速，而LinkedList則是以指標的方式指向下一個，所以如果要選取特定之元素必須一個一個數，速度相對地就會比較慢。<br>
![image]()</br></br>
而今天如果要在物件1後面再插入一個物件A，則會如下圖。
