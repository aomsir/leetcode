# 删除链表倒数第N个元素

## 链接

[leetcode](https://leetcode.cn/problems/remove-nth-node-from-end-of-list/)

## 题解

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummyNode = new ListNode(0);
        dummyNode.next = head;
        ListNode fast = dummyNode;
        ListNode slow = dummyNode;

        for (int i = 0;i < n;i++) {
            fast = fast.next;
        }

        while(fast.next != null) {
            slow = slow.next;
            fast = fast.next;
        }

        slow.next = slow.next.next;

        return dummyNode.next;
    }
}
```

## 思路

> - 思路很简单！使用快慢指针
> - 先定义头节点缓存位置
> - 然后定义快慢指针，快指针在慢指针前n个位置(n位倒数第n个的n)
> - 这样同时循环快慢指针，快指针到尾巴上，慢指针正好指在待删除的位置
> - 注意：要删除某个节点，操作指针一定记得指在该节点的前面

