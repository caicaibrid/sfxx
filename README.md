# sfxx
算法学习

## 二分查找 

假设要在电话簿中找一个名字以K打头的人，（现在谁还用电话簿！）可以从头开始翻页，直到进入以K打头的部分。但你很可能不这样做，而是从中间开始，因为你知道以K打头的名字在电话簿中间。

又假设要在字典中找一个以O打头的单词，你也将从中间附近开始。

现在假设你登录Facebook。当你这样做时，Facebook必须核实你是否有其网站的账户，因此必须在其数据库中查找你的用户名。如果你的用户名为karlmageddon，Facebook可从以A打头的部分开始查找，但更合乎逻辑的做法是从中间开始查找。

这是一个查找问题，在前述所有情况下，都可使用同一种算法来解决问题，这种算法就是二分查找。

### 算法复杂度

最优 log2n

最差 n

```
function binary_search (arr, search){
    let low = 0;
    let max = arr.length;
    
    while(low <= max){
        let mid = Math.floor((low + max)/2);
        if (arr[mid] === search){
            return mid;
        } else if (arr[mid] > search) {
            max = mid - 1
        } else {
            low = mid + 1;
        }
    }
    return -1
}

```
## 选择排序

在给定的列表中，找出最小值，放入新数组，直到列表里没有元素或只有一个

### 链表

链表里的元素除了第一个和最后一个都有两个部分组成，一个是元素的数据域 一个是指向的下一个地址（指针）

链表是一种物理存储单元上非连续、非顺序的存储结构，数据元素的逻辑顺序是通过链表中的指针链接次序实现的。链表由一系列结点（链表中每一个元素称为结点）组成，结点可以在运行时动态生成。每个结点包括两个部分：一个是存储数据元素的数据域，另一个是存储下一个结点地址的指针域。 相比于线性表顺序结构，操作复杂。由于不必须按顺序存储，链表在插入的时候可以达到O(1)的复杂度，比另一种线性表顺序表快得多，但是查找一个节点或者访问特定编号的节点则需要O(n)的时间，而线性表和顺序表相应的时间复杂度分别是O(logn)和O(1)。

### 数组和链表的区别

数组 读取快，插入 删除慢，因为需要移动后边的元素

链表 读取慢，插入 删除快，因为修改前一个的访问地址就可以了

```
function selectSort (arr) {
    let newArr = [];
    while (arr.length) {
        let min = arr[0];
        let index = 0;
        for (let i = 1; i<= arr.length; i++) {
            if (arr[i] < min) {
                min = arr[i]
                index = i
            }
        }
        newArr.push(min)
        arr.splice(index, 1)
    }
    return newArr
}

```

## 快速排序

选取一个基准值，然后进行细小分割，直到数组里只有一个元素

```
function quickSort (arr) {
    if (arr.length < 2) {
        return arr
    }
    let base = arr[0];
    
    let leftArr = [], rightArr = [];

    for (let i = 1; i< arr.length; i++){
        if (arr[i] <= base) {
            leftArr.push(arr[i])
        } else {
            rightArr.push(arr[i])
        }
    }
    return quickSort(leftArr).concat(base).concat(quickSort(rightArr))
}
```
## 冒泡排序

相邻的两个进行比较，然后交换顺序，每次循环到最后的一个为最大值，下一次不需要比较

```
function maopaoSort (arr) {
    for (let i=0; i< arr.length; i++){
        for (let j=0; j<arr.length - i - 1; j++){
            if (arr[j] > arr[j+1]) {
                let temp = arr[j]
                arr[j] = arr[j+1]
                arr[j+1] = temp
            }
        }
    }
    return arr
}
```



                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                