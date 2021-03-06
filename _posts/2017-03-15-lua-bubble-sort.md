---
layout:     post
title:      "Lua 排序算法 - 冒泡排序"
subtitle:   "Bubble Sort"
date:       2017-03-15
author:     "qmsheng"
header-img: "img/post-bg-miui6.jpg"
catalog:    true
tags:
    - Lua
    - Algorithm
---

冒泡排序（Bubble Sort，台湾译为：泡沫排序或气泡排序）是一种简单的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端。

##### 算法步骤

1. 有一个长度为n的序列，一共需要n次外循环
2. 在一次外循环里，比较相邻的元素。如果第一个比第二个大，就交换他们两个。这样可以保证，每次外循环结束，最右边的元素一定是最大的数。
3. 由于每一次外循环都可以确定一个最大的数，所以在一个外循环里一共需要比较n-i次内循环
4. 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

##### 动画演示

![Bubble Sort](/img/in-post/sort/Bubble-sort-example-300px.gif)

##### Lua 实现

```lua
local function bubbleSort(arr)
    for i = 1, #arr, 1 do
        for j = 1, #arr - i, 1 do
            if arr[j] > arr[j+1] then
                arr[j], arr[j+1] = arr[j+1], arr[j]
            end
        end
    end
end

-- test
local list = {
    -81, -93, -36.85, -53, -31, 79, 45.94, 36, 94, -95.03, 11, 56, 23, -39,
    14, 1, -20.1, -21, 91, 31, 91, -23, 36.5, 44, 82, -30, 51, 96, 64, -41
}
bubbleSort(list, 1, #list)
print(table.concat(list, ", "))
```
