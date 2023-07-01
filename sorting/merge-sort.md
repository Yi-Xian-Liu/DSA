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

## 遞迴法（Top-down）

1. 申請空間，使其大小為兩個已經排序序列之和，該空間用來存放合併後的序列
2. 設定兩個指標，最初位置分別為兩個已經排序序列的起始位置
3. 比較兩個指標所指向的元素，選擇相對小的元素放入到合併空間，並移動指標到下一位置
4. 重複步驟3直到某一指標到達序列尾
5. 將另一序列剩下的所有元素直接複製到合併序列尾

## 迭代法（Bottom-up）

1. 將序列每相鄰兩個數字進行合併操作，形成![{\displaystyle ceil(n/2)}](https://wikimedia.org/api/rest\_v1/media/math/render/svg/284284713ad8f1ba13458b896c87efc4b9b7df9c)個序列，排序後每個序列包含兩/一個元素
2. 若此時序列數不是1個則將上述序列再次合併，形成![{\displaystyle ceil(n/4)}](https://wikimedia.org/api/rest\_v1/media/math/render/svg/0f7b6be8e0c402e981a78d573dc3072c3d24a3c4)個序列，每個序列包含四/三個元素
3. 重複步驟2，直到所有元素排序完畢，即序列數為1
