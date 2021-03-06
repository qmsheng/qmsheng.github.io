---
layout:     post
title:      "Lua 排序算法 - 归并排序"
subtitle:   "Merge Sort"
date:       2017-03-17
author:     "qmsheng"
header-img: "img/post-bg-miui6.jpg"
catalog:    true
tags:
    - Lua
    - Algorithm
---

归并排序（Merge Sort，台湾译作：合并排序）是建立在归并操作上的一种有效的排序算法。该算法是采用分治法（Divide and Conquer）的一个非常典型的应用。

归并操作(Merge)，也叫归并算法，指的是将两个已经排序的序列合并成一个序列的操作。归并排序算法依赖归并操作。归并排序有多路归并排序、两路归并排序, 可用于内排序，也可以用于外排序。这里仅对内排序的两路归并方法进行讨论。

##### 算法步骤

1. 把 n 个记录看成 n 个长度为 1 的有序子表
2. 进行两两归并使记录关键字有序，得到 n/2 个长度为 2 的有序子表
3. 重复第 2 步直到所有记录归并成一个长度为 n 的有序表为止。

##### 动画演示

![Alt text](/img/in-post/sort/Merge-sort-example-300px.gif)

##### Lua 实现

```lua
local function mergeSort(arr, low, high)
    local low = low
    local high = high
    if high - low < 1 then return end

    local mid = math.floor((low+high)/2)
    -- 递归的拆分子序列
    mergeSort(arr, low, mid)
    mergeSort(arr, mid+1, high)

    -- i, m 代表一个序列中的低高位
    -- m+1，high 代表相邻的另外一个序列（right序列）的低高位
    local i, m = low, mid
    local temp
    while i <= m and m+1 <= high do
        if arr[i] >= arr[m+1] then
            temp = arr[m+1]
            -- 迭代left序列
            -- 之所以这么迭代是因为我们本质上还是在arr中
            for j = m, i, -1 do
                arr[j+1] = arr[j]
            end
            arr[i] = temp
            m = m + 1
        else
            i = i + 1
        end
    end
end

local list = {
    -81, -93, -36.85, -53, -31, 79, 45.94, 36, 94, -95.03, 11, 56, 23, -39,
    14, 1, -20.1, -21, 91, 31, 91, -23, 36.5, 44, 82, -30, 51, 96, 64, -41
}
mergeSort(list, 1, #list)
print(table.concat(list, ", "))
```
