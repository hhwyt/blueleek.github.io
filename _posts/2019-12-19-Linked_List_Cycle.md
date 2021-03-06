---
layout: post
title:  "141. Linked List Cycle"
categories: 算法
tags: LeetCode Algorithm LinkedList
author: blueleek
---

这两天沉浸在链表的算法中，这道链表题的思路依然是使用快慢指针，但很有意思的是遇到一个数学证明问题，需要证明有环链表中，快指针每次前进 2 步，慢指针前进一步，最终快慢指针一定会相遇 <br/>
晚上一直想不通这个问题，最后用图解法证明了这个问题，还是图解大法好









### Problem Description

>Given a linked list, determine if it has a cycle in it.
>
> To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.
>
>Example 1:
```
 Input: head = [3,2,0,-4], pos = 1
 Output: true
 Explanation: There is a cycle in the linked list, where tail connects to the second node.
 ```
 
![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)
 
>Example 2:
```
Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)
 
 
>Example 3:
```
Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.
```
 
![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)
 
 
 
 
 
### 快慢指针法
  定义快慢指针，`slow`，`fast`，慢指针每向前移动一步，快指针移动两步<br/>
  循环条件： `fast.next !== null ` && `fast.next.next !== null`<br/>
  终止条件： `fast` 和 `slow` 相遇，即证明链表中存在环
  
### 代码示例

 ```
var hasCycle = function(head) {
    if (head === null) {
        return false;
    }
    var slow = head; var fast = head;
    while (fast.next !== null && fast.next.next !== null) {
        slow = slow.next
        fast = fast.next.next
        if (slow === fast) {
            return true
        }
    }
    return false;
     
 ```
 
### 彩蛋：快慢指针相遇图解证明
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191220002514390.jpeg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hodGh3eA==,size_16,color_FFFFFF,t_70)
 

