
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

