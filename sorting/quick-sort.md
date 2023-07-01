# Quick sort

<figure><img src="../.gitbook/assets/螢幕擷取畫面 2023-07-01 183357.png" alt=""><figcaption></figcaption></figure>

資料的分佈random且large時，quick sort會比merge sort跟heap sort快一點。

其使用了divide and conquer，藉由選擇一個array內的pivot element，將array分成比pivot小的subarray與比pivot大的subarray之後，再recursively的排序這兩個subarray。因此也被稱作partition-exchange sort。

quick sort為comparison sort，而大部分的實作都使得其不為stable。

## 演算法

```
function quicksort(q)
 {
     var list less, pivotList, greater
     if length(q) ≤ 1 
         return q
     else 
     {
         select a pivot value pivot from q
         for each x in q except the pivot element
         {
             if x < pivot then add x to less
             if x ≥ pivot then add x to greater
         }
         add pivot to pivotList
         return concatenate(quicksort(less), pivotList, quicksort(greater))
     }
 }
```

## 演算法(in-place)

```
function partition(a, left, right, pivotIndex)
 {
     pivotValue = a[pivotIndex]
     swap(a[pivotIndex], a[right]) // 把pivot移到結尾
     storeIndex = left
     for i from left to right-1
     {
         if a[i] < pivotValue
          {
             swap(a[storeIndex], a[i])
             storeIndex = storeIndex + 1
          }
     }
     swap(a[right], a[storeIndex]) // 把pivot移到它最後的地方
     return storeIndex
 }
```

這將使空間複雜度平均達到O(log(n))。

## 實作上的優化

### choice of pivot(median of three)

取array中，第一、中間與最後的index，並取這三者間的median作為pivot。避免取某一特定element可能導致在already sorted array上有worst case time complexity。

### repeated element

若array中的元素都相同，則時間複雜度將來到O(n^2)。因此，我們可以再另外分出跟pivot element相同的subarray，也就是說分成三個subarray，一個是比pivot小(還需recursively sort)，一個跟pivot一樣大(sorted)，一個比pivot大(還需recursively sort)。

## 比較

quick sort其實是bst的空間優化版本，不是依序的插入資料進明確的樹當中，而是快速的組織資料進一個由遞迴所隱含的樹當中，這兩個版本都產生了相同次數的比較。

in-place版本不stable，但其他版本可以透過犧牲效能跟空間來換取stability。

### Heap sort

heap sort通常比quick sort慢，但是heap sort的worst case time complexity總是O(nlog(n))。

而quick sort通常比較快，但除了intro sort版本外，都有wort cast time過慢的問題。

如果已經知道資料的分配，有時用heap sort會較快。

且heap sort只用常數的額外空間，但需要有效率的隨機存取才可行。

而quick sort則需要O(nlogn(n))的額外空間。

### merge sort

merge sort跟heap sort相同，也有最壞時間複雜度O(nlog(n))的優勢。

且不像heap sort或quick sort，merge sort為stable sort。

merge sort還可以輕易的被應用在linked list，或儲存在慢速儲存媒體(如硬碟)的array。

雖然quick sort也能應用在linked list上，但無法隨機存取pivot element，導致有差的pivot選擇。

然而，merge sort的主要缺點，是在最佳情況下需要Ω(n)的儲存空間。
