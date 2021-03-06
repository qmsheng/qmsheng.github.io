---
layout:     post
title:      "Lua 排序算法 - 插入排序"
subtitle:   "Insertion Sort"
date:       2017-03-23
author:     "qmsheng"
header-img: "img/post-bg-miui6.jpg"
catalog:    true
tags:
    - Lua
    - Algorithm
---

设有一组关键字｛K1， K2，…， Kn｝；排序开始就认为 K1 是一个有序序列；让 K2 插入上述表长为 1 的有序序列，使之成为一个表长为 2 的有序序列；然后让 K3 插入上述表长为 2 的有序序列，使之成为一个表长为 3 的有序序列；依次类推，最后让 Kn 插入上述表长为 n-1 的有序序列，得一个表长为 n 的有序序列。

##### 算法步骤

1. 从第一个元素开始，该元素可以认为已经被排序
2. 取出下一个元素，在已经排序的元素序列中从后向前扫描
3. 如果该元素（已排序）大于新元素，将该元素移到下一位置
4. 重复步骤 3，直到找到已排序的元素小于或者等于新元素的位置
5. 将新元素插入到该位置后
6. 重复步骤 2~5

##### 动画演示

![Alt text](/img/in-post/sort/Insertion-sort-example.gif)

##### Lua 实现

```lua
local function insertionSort(arr)
    for i = 2, #arr, 1 do
        local tmp = arr[i]
        local j = i - 1
        while j >= 1 and tmp < arr[j] do
            arr[j+1] = arr[j]
            j = j - 1
        end
        arr[j+1] = tmp
    end
end

local list = {
    -81, -93, -36.85, -53, -31, 79, 45.94, 36, 94, -95.03, 11, 56, 23, -39,
    14, 1, -20.1, -21, 91, 31, 91, -23, 36.5, 44, 82, -30, 51, 96, 64, -41
}
insertionSort(list)
print(table.concat(list, ", "))
```
