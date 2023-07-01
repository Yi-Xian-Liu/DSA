# Merge sort

<figure><img src="../.gitbook/assets/螢幕擷取畫面 2023-07-01 200834.png" alt=""><figcaption></figcaption></figure>

其使用divide and conquer。

* 將資料從中間分成兩份，對每份都再進行merge sort
* 將sort好的兩份資料進行合併

可能是最佳解

## Time complexity

<table data-full-width="false"><thead><tr><th>worst</th><th>average</th><th>best</th></tr></thead><tbody><tr><td>O(nlog(n))</td><td>O(nlog(n))</td><td>O(nlog(n))</td></tr></tbody></table>

## Space complexity

O(n)

