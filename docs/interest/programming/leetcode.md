
### 1. Two Sum

```py title="brute force.py"
class Solution: # (1)
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]
```

1.  :man_raising_hand: 2025/03/26


```py title="hash table.py"
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashtable = dict()
        for i, num in enumerate(nums):
            if target - num in hashtable:
                return [hashtable[target - num], i]
            hashtable[nums[i]] = i
```

### 2. Add Two Numbers

```py title="linked list.py" 
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution: # (1)
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode(0)
        current = dummy
        carry = 0
        while l1 or l2 or carry:
            val1 = l1.val if l1 else 0
            val2 = l2.val if l2 else 0
            sum = val1 + val2 + carry
            carry = sum // 10
            current.next = ListNode(sum % 10)
            current = current.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        return dummy.next
```

1.  :man_raising_hand: 2025/03/27


```py title="create linked list.py" 
# Remark: 思想一致
def create_linked_list(values): 
    dummy = ListNode()
    current = dummy
    for val in values:
        current.next = ListNode(val)
        current = current.next
    return dummy.next

l1 = create_linked_list([2, 4, 3])
l2 = create_linked_list([5, 6, 4])

while l1:
    print(l1.val) # 2\n 4\n 3
    l1 = l1.next

```

```c title="linked list.c"
// typedef struct ListNode {
//     int val;
//     struct ListNode* next;
// } ListNode;
// 避免一直写struct, 直接用typedef

ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    ListNode* dummy = (ListNode*)malloc(sizeof(ListNode));
    dummy->next = NULL;
    ListNode* current = dummy;
    int carry = 0;
    while (l1 || l2 || carry) {
        int a = l1 ? l1->val : 0;
        int b = l2 ? l2->val : 0;
        int sum = a + b + carry;
        carry = sum / 10;
        current->next = (ListNode*)malloc(sizeof(ListNode));
        current->next->val = sum % 10;
        current->next->next = NULL;
        current = current->next;
        if (l1) l1 = l1->next;
        if (l2) l2 = l2->next;
    }
    ListNode* result = dummy->next;
    free(dummy); // 避免内存泄漏
    return result;
}
```

```c title="create linked list.c"
// Remark: 思想一致
ListNode* createNode(int val) {
    ListNode* newNode = (ListNode*)malloc(sizeof(ListNode));
    newNode->val = val;
    newNode->next = NULL;
    return newNode;
}

ListNode* createList(int* nums, int size) {
    ListNode* dummy = createNode(0);
    ListNode* current = dummy;
    for (int i = 0; i < size; i++) {
        current->next = createNode(nums[i]);
        current = current->next;
    }
    return dummy->next;
}

int main() {
    int nums[] = {2, 4, 3};
    int nums[] = {5, 6, 4};
    ListNode* l1 = createList(nums, 3);
    ListNode* l2 = createList(nums, 3);
    ListNode* result = addTwoNumbers(l1, l2);
    free(l1);
    free(l2);
    free(result);
    return 0;
}
```

### 3. Longest Substring Without Repeating Characters

```py title="brute force.py"
class Solution: # (1) 运行提交笑嘻嘻，一看击败百分七:(
    def lengthOfLongestSubstring(self, s: str) -> int:
        countset = []
        for num, i in enumerate(s):
            count = 1
            ls = [i]
            for j in range(num+1, len(s)):
                if s[j] not in ls:
                    ls.append(s[j])
                    count += 1
                else:
                    break
            countset.append(count)
        if countset == []:
            return 0
        else:
            return max(countset)
```

1.  :man_raising_hand: 2025/03/27

```py title="sliding window.py"
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
            window_chars = set()
            n = len(s)
            left = 0
            max_len = 0
            for right in range(n):
                while s[right] in window_chars:
                    window_chars.remove(s[left])
                    left += 1
                window_chars.add(s[right])
                max_len = max(max_len, right - left + 1)
            return max_len
```

### 4. Median of Two Sorted Arrays

```py title="sorted array.py"
# 合并排序秒了，但合并时间复杂度为O(m+n), 排序采用Timsort算法，时间复杂度变为O((m+n)log(m+n))
class Solution:  # (1)
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        combine = sorted(nums1 + nums2)
        n = len(combine)
        if n % 2 == 0:
            output = (combine[int(n/2 - 1)] + combine[int(n/2)]) / 2
        else:
            output = combine[n//2]
        return output
```

1.  :man_raising_hand: 2025/03/27

```py title="binary search.py"
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        def getKthElement(k):
            """
            - 主要思路：要找到第 k (k>1) 小的元素，那么就取 pivot1 = nums1[k/2-1] 和 pivot2 = nums2[k/2-1] 进行比较
            - 这里的 "/" 表示整除
            - nums1 中小于等于 pivot1 的元素有 nums1[0 .. k/2-2] 共计 k/2-1 个
            - nums2 中小于等于 pivot2 的元素有 nums2[0 .. k/2-2] 共计 k/2-1 个
            - 取 pivot = min(pivot1, pivot2)，两个数组中小于等于 pivot 的元素共计不会超过 (k/2-1) + (k/2-1) <= k-2 个
            - 这样 pivot 本身最大也只能是第 k-1 小的元素
            - 如果 pivot = pivot1，那么 nums1[0 .. k/2-1] 都不可能是第 k 小的元素。把这些元素全部 "删除"，剩下的作为新的 nums1 数组
            - 如果 pivot = pivot2，那么 nums2[0 .. k/2-1] 都不可能是第 k 小的元素。把这些元素全部 "删除"，剩下的作为新的 nums2 数组
            - 由于我们 "删除" 了一些元素（这些元素都比第 k 小的元素要小），因此需要修改 k 的值，减去删除的数的个数
            """
            
            index1, index2 = 0, 0
            while True:
                # 特殊情况
                if index1 == m:
                    return nums2[index2 + k - 1]
                if index2 == n:
                    return nums1[index1 + k - 1]
                if k == 1:
                    return min(nums1[index1], nums2[index2])

                # 正常情况
                newIndex1 = min(index1 + k // 2 - 1, m - 1)
                newIndex2 = min(index2 + k // 2 - 1, n - 1)
                pivot1, pivot2 = nums1[newIndex1], nums2[newIndex2]
                if pivot1 <= pivot2:
                    k -= newIndex1 - index1 + 1
                    index1 = newIndex1 + 1
                else:
                    k -= newIndex2 - index2 + 1
                    index2 = newIndex2 + 1
        
        m, n = len(nums1), len(nums2)
        totalLength = m + n
        if totalLength % 2 == 1:
            return getKthElement((totalLength + 1) // 2)
        else:
            return (getKthElement(totalLength // 2) + getKthElement(totalLength // 2 + 1)) / 2
```

### 5. Longest Palindromic Substring