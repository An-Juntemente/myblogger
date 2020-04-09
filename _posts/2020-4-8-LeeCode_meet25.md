---
layout: post
title: LeeCode算法题库
date: 2020-4-8
Author: Ain
tags: [Java, 算法]
comments: true
---
## 面试题25. 合并两个排序链表

### 题干

> **输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。**



### 算法演示

​	先贴一下代码

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode pre = new ListNode(0);
        ListNode cur = pre;
        while(l1 != null && l2 != null){    //l1 与 l2 不能通过 || 进行遍历 若两个链表一个为空 则不能进行val的比较
            if(l1.val<l2.val){                 
                cur.next = new ListNode(l1.val);
                l1 = l1.next;
            }
            else{
                cur.next =new ListNode(l2.val);              
                l2 = l2.next;
            }
            cur = cur.next;
        }
        cur.next = (l1 != null) ? l1:l2;    //一个链表为空 则cur下个节点等于非空链表的剩下节点的第一个即可，因为链表有序 且后续节点的信息通过next指针相连
        return pre.next;
    }
}
```



### 算法思路

​	因为两个链表已经有序，通过比较两个链表中的元素，小的存储到新链表，并且指针后移即可

​	当一个链表为空时，因为链表有序，把剩余的链表一并存储到新链表即可



### tip：

1. 对于循环控制条件的选择，这道题并没选着链表加法  || 控制， 因为如果链表为null，循环内的比较大小不能进行。
2. 在有链表为null后，跳出循环将非空链表的第一个节点赋值给新链表，因为链表的剩余信息地址都存储在next中。





