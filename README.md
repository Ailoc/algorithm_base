📋这是一个记录自己偶尔算法练习的代码仓库，有时间练一练，开发一下大脑
# 🧠 LeetCode Algorithm Notes

本项目用于整理和记录我的 LeetCode 刷题代码与思路，按照**数据结构**与**算法类型**分类展示。  
点击表格中的题目可以直接跳转到该题的详细代码实现。

---

## 
## 📘 数组 (Array)

| #    | 题目                                                         | 类型     | LeetCode                                                     | 难度   |
| ---- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ | ------ |
| 1    | [两数之和 (Two Sum)](#两数之和-two-sum)                      | 哈希表   | [LeetCode 1](https://leetcode.com/problems/two-sum/)         | 🟢 Easy |
| 2    | [最大子数组和 (Maximum Subarray)](#最大子数组和-maximum-subarray) | 动态规划 | [LeetCode 53](https://leetcode.com/problems/maximum-subarray/) | 🟢 Easy |

### 🧩 两数之和 (Two Sum)

```go
func twoSum(nums []int, target int) []int {
    m := make(map[int]int)
    for i, n := range nums {
        if j, ok := m[target-n]; ok {
            return []int{j, i}
        }
        m[n] = i
    }
    return nil
}
```

---
## 
## 📘 链表 (LinkedList)
| #    | 题目                                                         | 类型     | LeetCode                                                     | 难度   |
| ---- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ | ------ |
| 1    | [反转链表](#反转链表)                      | 链表   | [206. 反转链表 - 力扣（LeetCode）](https://leetcode.cn/problems/reverse-linked-list/description/?envType=problem-list-v2&envId=linked-list)        | 🟢 Easy |
| 2    | [两两交换链表中的节点](#两两交换链表中的节点)                      | 链表   | [24. 两两交换链表中的节点 - 力扣（LeetCode）](https://leetcode.cn/problems/swap-nodes-in-pairs/description/?envType=problem-list-v2&envId=linked-list)        | 🟢 Easy |

### 🧩 反转链表

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    prev := (*ListNode)(nil)
    cur := head
    for cur != nil {
        head = head.Next
        cur.Next = prev
        prev = cur
        cur = head
    }
    return prev
}
```

---

### 🧩 两两交换链表中的节点

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func swapPairs(head *ListNode) *ListNode {
    if head == nil || head.Next == nil {
        return head
    }
    prevHead := &ListNode{0, head}
    cur, swapNode := head, head.Next
    rt := swapNode
    for {
        prevHead.Next = swapNode
        cur.Next = swapNode.Next
        swapNode.Next = cur
        prevHead = cur
        if cur.Next != nil && cur.Next.Next != nil {
            cur = cur.Next
            swapNode = cur.Next
        }else {
            break
        }
    }
    return rt
}
```

---
