# Java Collection

## 關於Collection

在Java裡頭除了陣列可以幫我們處理資料以外，再來就是Collection API中的元件了。Collection(集合)就是一個設計用來處理多個資料物件，而存放在集合中的物件我們把他稱之為Elements(元素)，在程式運行時，有時需要一個地方暫存產生出來的物件，這個地方我們就稱為Container(容器)。然而在java.util.Collection介面中定義了所有集合最基本的存取方式如下圖:</br>
![image](https://github.com/leoa12412a/Java_Collection/blob/master/1.PNG)</br></br>

## 解析 Collection interface

Collection interface分別繼承了另外3個interface分別是Set(集合)、List、Queue(佇列)，下面對這三個interface也有簡單的介紹:</br>

  * Set : 不允許相同物件存在的集合結構ex:HashSet、TreeSet
  * List : 循序索引的串列結構ex:ArrayList、LinkedList
  * Queue : 使用 Key-Value(鍵-值) 方式儲存的結構ex:HashMap、TreeMap
  
## Collection - List 

List算是在應用程式裡最常見的，List代表的就是所謂清單列表，最大的特點就是依序的放入以及取出，且具有順序性，List的實作類別有ArrayList、LinkedList、Vector

 * ArrayList : 安全不線程(不同步)，查詢速度快，但增加刪除慢，使用陣列
 * LinkedList : 安全不線程(不同步)，增刪速度快，查詢慢，使用鏈結串列
 * Vector : 安全線程(同步)，Vector與ArrayList唯一的區別是，Vector是線程安全的。在擴展容量的時候，Vector是擴展為原來的2倍，而ArrayList是擴展為原來             的1.5倍。
 
### 線程的安全性

 * 安全線程 : 多線程訪問時，採用了加鎖機制，當一個線程訪問該類的某個數據時，進行保護，其他線程不能進行訪問直到該線程讀取完，其他線程才可使用。                    不會出現數據不一致或者數據污染。
 
 * 安全不線程 :  不提供數據訪問保護，有可能出現多個線程先後更改數據造成所得到的數據是髒數據。

### ArrayList 和 LinkedList 的差異
所以List有的功能，ArrayList與LinkedList全都有；而這二個List的差別在於，尋找下一節點的位置與切換下一個節點的位置。下面以實際例子來解釋兩者差異。

假設今天三個物件分別要儲存在ArrayList 和 LinkedList會以下圖的方式進行儲存
ArrayList會按照順所有的物件，所以要選取特定(第N個)元素時，非常方便快速，而LinkedList則是以指標的方式指向下一個，所以如果要選取特定之元素必須一個一個數，速度相對地就會比較慢。<br>
![image](https://github.com/leoa12412a/Java_Collection/blob/master/2.PNG)</br></br>
而今天如果要在物件1後面再插入一個物件A，則會如下圖。
ArrayList必須所有A物件後方的物件都後移一個位置，好放入A物件，而LinkedList只需要讓物件1指向物件A和物件A指向物件2，如果今天List內的數量很多，ArrayList會影響到被插入的index後的每一個，而LinkedList只會影響到二個。<br>
![image](https://github.com/leoa12412a/Java_Collection/blob/master/3.PNG)</br>

### ArrayList

ArrayList的宣告與基本使用

```
    public static void LinkedList_List() {
        LinkedList<Integer> myList = new LinkedList<Integer>(); //可以忽略型態不寫

        myList.add(1);  //加入元素
        myList.add(3);
        myList.add(5);

        int count = myList.size(); //查詢myList大小

        boolean isset = myList.contains(2); //查詢特定元素，上面沒有2所以回傳false

        int number = myList.indexOf(3); //查詢特定元素在第幾個

        boolean empty = myList.isEmpty(); //查詢ArrayList是否為空

        myList.remove(1); //刪除第1個所以3被刪除 所以5變成第一個 第0個不變還是1

        myList.set(1, 4); //修改第一個物件的元素5=>4

        myList.add(1, 2); //在第一個位置插入元素2

        for (int i = 0; i < myList.size(); i++) 
        {
            System.out.println(myList.get(i));
        }
    }
```

ArrayList的二維陣列

```
    public static void Array_List_for_2() {

        ArrayList<ArrayList<Integer>> myList = new ArrayList<ArrayList<Integer>>();  //型態為ArrayList

        for(int i=0;i<10;i++)  // 假設第一層有10個
        {
            ArrayList<Integer> myList2 = new ArrayList<Integer>();  //每個第一層都新增一個第二層ArrayList
            myList2.add(1);  //為第二層ArrayList添加元素
            myList2.add(2);
            myList.add(myList2); //為第一層ArrayList添加第二層ArrayList
        }

        System.out.println(myList.get(0).get(1));  //獲得第一層第0個裡的第二層第1個
    }
```

### LinkedList

基本上語法ArrayList幾乎一模一樣，只多了可以對First跟Last進行動作

```
     public static void LinkedList_List() {
        LinkedList<Integer> myList = new LinkedList<Integer>(); //可以忽略型態不寫

        myList.add(1);  //加入元素
        myList.add(3);
        myList.add(5);

        int count = myList.size(); //查詢myList大小

        boolean isset = myList.contains(2); //查詢特定元素，上面沒有2所以回傳false

        int number = myList.indexOf(3); //查詢特定元素在第幾個

        boolean empty = myList.isEmpty(); //查詢ArrayList是否為空

        myList.remove(1); //刪除第1個所以3被刪除 所以5變成第一個 第0個不變還是1

        myList.set(1, 4); //修改第一個物件的元素5=>4

        myList.add(1, 2); //在第一個位置插入元素2

        for (int i = 0; i < myList.size(); i++)
        {
            System.out.println(myList.get(i));
        }

        System.out.println(myList.getFirst());  // 獲得第一個元素
        System.out.println(myList.getLast());   // 獲得最後一個元素
    }
```

## Collection - Set

Set繼承Collection介面，是用於存放不重複的元素，所以Set裡的元素都是唯一值，如果添加重複元素會被忽略掉。Set裡對於重複值的判斷並不是用 '==' 而是equals，而equeals 和 == 之間的差異在於下面幾點<br>

以A、B兩個變數來舉例:<br>

* ==是判斷A.B兩個變數分別指向同一個記憶體空間，equals是判斷A.B個別指向的記憶體空間裡頭的值是否一樣
* ==是拿記憶體的位置做比較，equals是對A、B的內容作比較

而Set裡有幾種實現的方式:<br>

* HashSet
* TreeSet
* LinkedHashSet

### HashSet
HashSet是基於數據結構中的哈希表(Hash table)來實現的，哈希表又稱為雜湊表是一種根據Key直接查詢在內存儲存位置的資料結構，也就是可以透過一個關鍵的值
(Key)來查找資料，簡單來說這種方式可以提高查找的效率。HashSet裡頭也可以是空值(Null)，但只能有一個空值，另外HashSet裡頭的元素不能保證排列的順序，順序有可能發生變化。


下面是一個簡單的範例，我們在hashset添加(add)幾個值
```
public class HashSet_example {

    public static HashSet hashset;

    public static void main(String[] args) {
        hashset = new HashSet();
        ex1();
    }

    public static void ex1()
    {
        hashset.add("1");
        hashset.add("2");
        hashset.add("3");
        hashset.add("1");
        hashset.add("");
        hashset.add("");
        System.out.println(hashset);
    }
   
```
產生結果
```
[, 1, 2, 3]
```
觀察產生的結果我們可以知道如果有同樣的元素並不會存入HashSet裡頭，空值亦只能存在一個。<br><br>

再來看下面的範例，我們這次讓HashSet內每次新增一個new產生出來的Student，並重複輸入一樣的學生
```
public class HashSet_example {

    public static HashSet hashset;

    public static void main(String[] args) {
        hashset = new HashSet();
        ex2();
    }
  
    public static void ex2()
    {
        hashset.add(new Student("1","Leo"));
        hashset.add(new Student("2","Eric"));
        hashset.add(new Student("3","Jerry"));
        hashset.add(new Student("1","Leo"));
        System.out.println(hashset);
    }
}



class Student {
    private String id;
    private String name;
    Student(String id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public String toString()  {
        return String.format("(%s, %s)", id, name);
    }

}
```
產生結果
```
[(3, Jerry), (2, Eric), (1, Leo), (1, Leo)]
```
這是理所當然的結果，因為你並沒有告訴Set，什麼樣的Student實例才算是重複，以HashSet為例，會使用物件的hashCode()與equals()來判斷物件是否相同，HashSet
的實作概念是，在記憶體中開設空間，每個空間會有個雜湊編碼（Hash code）：
![image](https://github.com/leoa12412a/Java_Collection/blob/master/hashset1.PNG)</br></br>
這些空間稱為雜湊桶（Hash bucket），如果物件要加入HashSet，則會呼叫物件的hashCode()取得雜湊碼，並嘗試放入對應號碼的雜湊桶中，如果雜湊桶中沒物件，則直接放入，如上圖所示；如果雜湊桶中有物件呢？會再呼叫物件的equals()進行比較：</br>
![image]()</br></br>

所以我們要自己實作不重複的Student的時候，就必須實作hashCode()與equals()方法
```
public class HashSet_example {

    public static HashSet hashset;

    public static void main(String[] args) {
        hashset = new HashSet();
        ex3();
    }

    

    public static void ex3()
    {
        hashset.add(new Student1("1","Leo"));
        hashset.add(new Student1("2","Eric"));
        hashset.add(new Student1("3","Jerry"));
        hashset.add(new Student1("1","Leo"));
        System.out.println(hashset);
    }
}



class Student1 {
    private String id;
    private String name;
    Student1(String id, String name) {
        this.id = id;
        this.name = name;
    }

    // NetBeans自動產生的equals()與hashCode()

    @Override
    public int hashCode() {
        // Objects 有 hash() 方法可以使用
        // 以下可以簡化為 return Objects.hash(id, name);
        int hash = 7;
        hash = 47 * hash + Objects.hashCode(this.id);
        hash = 47 * hash + Objects.hashCode(this.name);
        return hash;
    }

    @Override
    public boolean equals(Object obj) {
        if (obj == null) {
            return false;
        }
        if (getClass() != obj.getClass()) {
            return false;
        }
        final Student1 other = (Student1) obj;
        if (!Objects.equals(this.id, other.id)) {
            return false;
        }
        if (!Objects.equals(this.name, other.name)) {
            return false;
        }
        return true;
    }

    @Override
    public String toString()  {
        return String.format("(%s, %s)", id, name);
    }
}

```
產生結果
```
[(3, Jerry), (1, Leo), (2, Eric)]
```
這邊比起上一個範例程式多了hashCode()來判斷雜湊桶中是否有物件，並且在equals()裡判斷如果有的話就判斷是否相同，沒有的話就直接存入。
