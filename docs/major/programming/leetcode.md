
### 1. Two Sum

=== "Python: brute force"

    ```py
    class Solution: # (1)
        def twoSum(self, nums: list[int], target: int) -> list[int]:
            for i in range(len(nums)):
                for j in range(i+1, len(nums)):
                    if nums[i] + nums[j] == target:
                        return [i, j]
    ```

    1.  :man_raising_hand: 2025/03/26

=== "hash table"

    ```py
    class Solution:
        def twoSum(self, nums: List[int], target: int) -> List[int]:
            hashtable = dict()
            for i, num in enumerate(nums):
                if target - num in hashtable:
                    return [hashtable[target - num], i]
                hashtable[nums[i]] = i
    ```

### 2. Add Two Numbers

=== "Python: linked list"

    ```py
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

=== "create linked list"

    ```py
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

=== "C: linked list"

    ```c
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

=== "create linked list"

    ```c
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


=== "Python: brute force"

    ```py
    class Solution: # (1) 运行提交笑嘻嘻，一看击败百分七🤡
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

=== "sliding window"

    ```py
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

=== "Python: sorted array"

    ```py
    # 合并排序秒了，但合并时间复杂度为O(m+n), 排序采用Timsort算法，时间复杂度变为O((m+n)log(m+n))
    class Solution:  # (1)
        def findMedianSortedArrays(self, nums1: list[int], nums2: list[int]) -> float:
            combine = sorted(nums1 + nums2)
            n = len(combine)
            if n % 2 == 0:
                output = (combine[int(n/2 - 1)] + combine[int(n/2)]) / 2
            else:
                output = combine[n//2]
            return output
    ```

    1.  :man_raising_hand: 2025/03/27

=== "binary search"

    ```py
    class Solution:
        def findMedianSortedArrays(self, nums1: list[int], nums2: list[int]) -> float:
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

=== "Python: expand around center"

    ```py
    class Solution: # (1)
        def longestPalindrome(self, s: str) -> str:
            n = len(s)
            if n == 0:
                return ""
            maxlen = 1
            maxstring = s[0]
            for i in range(n):
                # 奇数长度回文
                l, r = i, i
                while l >= 0 and r < n and s[l] == s[r]:
                    if r - l + 1 > maxlen:
                        maxlen = r - l + 1
                        maxstring = s[l:r+1]
                    l -= 1
                    r += 1

                # 偶数长度回文
                l, r = i, i+1
                while l >= 0 and r < n and s[l] == s[r]:
                    if r - l + 1 > maxlen:
                        maxlen = r - l + 1
                        maxstring = s[l:r+1]
                    l -= 1
                    r += 1
                
            return maxstring
    ```

    1.  :man_raising_hand: 2025/03/28


### 6. ZigZag Conversion

=== "Python: Indexing regularity"

    ```py
    class Solution: # (1)
        def convert(self, s: str, numRows: int) -> str:
            if numRows == 1:
                return s
            output = []
            n = len(s)
            gap = numRows + (numRows - 2) # 完整“Z”字形的列间距

            for row in range(numRows):
                i = row
                while i < n:
                    output.append(s[i])
                    # 处理中间行（非首尾行）
                    if row != 0 and row != numRows - 1:
                        j = i + gap - 2*row
                        if j < n:
                            output.append(s[j])
                    i += gap 
            return "".join(output)
    ```

    1.  :man_raising_hand: 2025/03/28

=== "Python: 巧设flag, 行索引递增递减不断转折"

    ```py
    class Solution: # 真是甜菜🤏
        def convert(self, s: str, numRows: int) -> str:
            if numRows < 2:
                return s
            res = ["" for _ in range(numRows)]
            i, flag = 0, -1
            for c in s:
                res[i] += c
                if i == 0 or i == numRows - 1:
                    flag = -flag
                i += flag
            return "".join(res)
    ```


### 7. Reverse Integer

=== "Python: reverse the string"

    ```py
    class Solution: # (1)
        def reverse(self, x: int) -> int:
            if x > 0:
                s = reversed(str(x))
                result = int("".join(s))
            elif x == 0:
                result = 0
            else:
                s = reversed(str(x)[1:])
                result = int("-" + "".join(s))
            
            if result < -2**31 or result > 2**31 - 1:
                return 0
            else:
                return result
    ```
    
    1.  :cheese: 2025/03/29

=== "Digit Reversal"

    ```py
    class Solution:
        def reverse(self, x: int) -> int:
            INT_MIN, INT_MAX = -2**31, 2**31 - 1
            sign = -1 if x < 0 else 1
            x_abs = abs(x)

            reversed_num = 0
            while x_abs != 0:
                digit = x_abs % 10
                x_abs = x_abs // 10

                # 检查反转后的数字是否可能溢出
                if sign == 1 and (reversed_num > (INT_MAX - digit) // 10):
                    return 0
                if sign == -1 and (reversed_num > (abs(INT_MIN) - digit) // 10):
                    return 0

                reversed_num = reversed_num * 10 + digit
            
            reversed_num *= sign
            return reversed_num
    ```

### 8. ASCII to Integer (atoi)

=== "Python: DFA, deterministic finite automaton 确定有限状态机"

    ```py
    INT_MAX = 2**31 - 1
    INT_MIN = -2**31

    class Solution: # (1) 基本方法if else判断的shit mountain 就不写了，太烂了
        def myAtoi(self, s: str) -> int:
            automation = Automation()
            for c in s:
                automation.read(c)
            return automation.sign * automation.ans
    
    class Automation:
        def __init__(self):
            self.state = "start"
            self.sign = 1
            self.ans = 0
            self.table = {
                "start" : ["start", "signed", "in_number", "end"],
                "signed" : ["end", "end", "in_number", "end"],
                "in_number" : ["end", "end", "in_number", "end"],
                "end" : ["end", "end", "end", "end"]
            }
        
        def get_col(self, c):
            if c.isspace():
                return 0
            if c == "+" or c == "-":
                return 1
            if c.isdigit():
                return 2
            return 3

        def read(self, c):
            self.state = self.table[self.state][self.get_col(c)]
            if self.state == "in_number":
                self.ans = self.ans * 10 + int(c)
                self.ans = min(self.ans, INT_MAX) if self.sign == 1 else min(self.ans, -INT_MIN)
            elif self.state == "signed":
                self.sign = 1 if c == "+" else -1
    ```

    1.  :white_check_mark: 2025/03/31

=== "Regex"

    ```py
    class Solution:
    def myAtoi(self, s: str) -> int:
        return max(min(int(*re.findall('^[\+\-]?\d+', s.lstrip())), 2**31 - 1), -2**31)
    ```
    `^`: start of string

    `[\+\-]`: a single character of: +, -

    `?`: zero or one

    `+`: one or more

    `\d`: Any digit

    For more information: [regex101](https://regex101.com/){:target="_blank"}


### 9. Palindrome Number

=== "Python: reverse half of the number"

    ```py
    class Solution: # (1)
        def isPalindrome(self, x: int) -> bool:
            # 反转一半数字法
            # 特殊情况
            # 当x<0时，x不是回文数
            # 当数字的最后一位是0时，除非这个数字是0，否则都不满足回文性
            if x < 0 or (x % 10 == 0 and x != 0):
                return False
            
            revertednumber = 0
            while x > revertednumber:
                revertednumber = revertednumber * 10 + x % 10
                x = x // 10
            # 当数字长度为奇数时，我们可以通过revertednumber // 10去除处于中间位置的数字
            # 例如，当输入为12321时，在while循环的末尾我们可以得到 x = 12, revertednumber = 123
            # 因此我们可以将中位数字去除
            return x == revertednumber or x == revertednumber // 10
    ```

    1.  :white_check_mark: 2025/04/01

### 10. Regular Expression Matching

=== "Python: Dynamic programming"

    ```py
    class Solution: # (1) index非常绕，然后还有动态规划的思想，多琢磨吧
        def isMatch(self, s: str, p: str) -> bool:
            m, n = len(s) + 1, len(p) + 1
            dp = [[False] * n for _ in range(m)]
            dp[0][0] = True
            # 初始化首行
            for j in range(2, n, 2):
                dp[0][j] = dp[0][j - 2] and p[j - 1] == "*"
            # 状态转移
            for i in range(1, m):
                for j in range(1, n):

                    if p[j - 1] == "*": # 当前字符为*时
                        if dp[i][j - 2]:
                            dp[i][j] = True
                        elif dp[i - 1][j] and s[i - 1] == p[j - 2]:
                            dp[i][j] = True
                        elif dp[i - 1][j] and p[j - 2] == ".":
                            dp[i][j] = True

                    else: # 当前字符不为*时
                        if dp[i - 1][j - 1] and s[i - 1] == p[j - 1]:
                            dp[i][j] = True
                        elif dp[i - 1][j - 1] and p[j - 1] == ".":
                            dp[i][j] = True
            return dp[-1][-1]
    ```

    1. :white_check_mark: 2025/04/01

    多看多想：[k神图解](https://leetcode.cn/problems/regular-expression-matching/solutions/2361807/10-zheng-ze-biao-da-shi-pi-pei-dong-tai-m5z1i){:target="_blank"}

### 11. Container With Most Water

=== "Python: Two pointers"

    ```py
    class Solution: # (1) 指针移动的基本原则是短板动。本题目为贪心算法的一种
        def maxArea(self, height: list[int]) -> int:
            left, right = 0, len(height) - 1
            res = 0
            while left < right:
                area = (right - left) * min(height[left], height[right])
                res = max(res, area)
                if height[left] < height[right]:
                    left += 1
                else:
                    right -= 1
            return res
    ```

    1. :white_check_mark: 2025/04/03


### 12. Integer to Roman

=== "Python: 模拟"

    ```py
    class Solution: # (1)
        VALUE_SIMPLES = [
            (1000, "M")，
            (900, "CM"),
            (500, "D"),
            (400, "CD"),
            (100, "C"),
            (90, "XC"),
            (50, "L"),
            (40, "XL"),
            (10, "X"),
            (9, "IX"),
            (5, "V"),
            (4, "IV"),
            (1, "I"),
        ]

        def intToRoman(self, num: int) -> str:
            roman = list()
            for value, symbol in Solution.VALUE_SIMPLES:
                while num >= value:
                    num -= value
                    roman.append(symbol)
                if num == 0:
                    break
            return "".join(roman)
    ```

    1. :white_check_mark: 2025/04/03

=== "按照高位到低位，每位处理"

    ```py
    class Solution:
        def intToRoman(self, num: int) -> str: # 1 <= num <= 3999
            REF = [
                ["I", "II", "III", "IV", "V", "VI", "VII","VIII", "IX"],
                ["X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"],
                ["C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"],
                ["M", "MM", "MMM"]
            ]
            digit = 0
            flag = 0
            s = ""
            for i in range(3, -1, -1):
                num = num - digit * flag
                flag = 10**i
                digit = num // flag
                if digit == 0:
                    continue
                else:
                    s = s + REF[i][digit - 1]
            return s
    ```

### 13. Roman to Integer

=== "Python: 模拟"

    ```py
    class Solution: # (1) 
        SYMBOL_VALUES = {
            'I': 1,
            'V': 5,
            'X': 10,
            'L': 50,
            'C': 100,
            'D': 500,
            'M': 1000,
            }
        
        def romanToInt(self, s: str) -> int:
            res = 0
            n = len(s)
            for i, ch in enumerate(s):
                value = Solution.SYMBOL_VALUES[ch]
                if i < n - 1 and value < Solution.SYMBOL_VALUES[s[i + 1]]:
                    res -= value
                else:
                    res += value
            return res
    ```

    1. :white_check_mark: 2025/04/03

### 14. Longest Common Prefix

=== "Python: 纵向扫描"

    ```py
    class Solution: # (1) 
        def longestCommonPrefix(self, strs: list[str]) -> str:
            if not strs:
                return ""
            
            length, count = len(strs[0]), len(strs)
            for i in range(length):
                ch = strs[0][i]
                for j in range(1, count):
                    if i == len(strs[j]) or strs[j][i] != ch:
                        return strs[0][:i]
            return strs[0]
    ```

    1. :white_check_mark: 2025/04/04

=== "Python: 横向扫描"

    ```py
    class Solution:
        def longestCommonPrefix(self, strs: list[str]) -> str:
            if not strs:
                return ""
        
            prefix, count = strs[0], len(strs)
            for i in range(1, count):
                prefix = self.lcp(prefix, strs[i])
                if not prefix:
                    return ""
            return prefix

        def lcp(self, str1: str, str2: str) -> str:
            minlen, index = min(len(str1), len(str2)), 0
            while index < minlen and str1[index] == str2[index]:
                index += 1
            return str1[:index]
    ```

### 15. Three Sum 

=== "Python: dict-hashtable"

    ```py
    class Solution: # (1)
        def threeSum(self, nums: list[int]) -> list[list[int]]:
            # 将数字统计到字典中(hashtable)
            data = dict()
            for n in nums:
                if n in data:
                    data[n] += 1
                else:
                    data[n] = 1
            # 由小到大排序，且数字不同，以及得到0的位置
            keys = sorted(data.keys())
            N = len(keys)
            zeroAt = 0
            while zeroAt < N and keys[zeroAt] < 0:
                zeroAt += 1
            
            # 单独讨论3个0的情况
            res = []
            if 0 in data and data[0] > 2:
                res.append([0, 0, 0])
            
            # 各取一个负数a和一个正数b
            for i in range(zeroAt):
                for j in range(zeroAt + (0 in data), N):
                    a = keys[i]
                    b = keys[j]
                    rest = 0 - a - b # 虽然由a < 0 < b可以得到-b < rest < -a，但是为了避免重复，这里强制rest在a和b之间，保证输出的三元组一定是不重复的升序排列。
                    if rest == a and data[a] > 1:
                        res.append([a, a, b])
                    elif a < rest < b and rest in data:
                        res.append([a, rest, b])
                    elif rest == b and data[b] > 1:
                        res.append([a, b, b])
            return res
    ```

    1. :white_check_mark: 2025/04/04

=== "Python: 排序+双指针"

    ```py
    class Solution:
        def threeSum(self, nums: list[int]) -> list[list[int]]:
            nums.sort()
            n = len(nums)
            res = list()
            for i in range(n):
                if i > 0 and nums[i] == nums[i - 1]: # 跳过重复
                    continue
                l, r = i + 1, n - 1
                while l < r:
                    s = nums[i] + nums[l] + nums[r]
                    if s == 0:
                        res.append([nums[i], nums[l], nums[r]])
                        l += 1
                        r -= 1
                        while l < r and nums[l] == nums[l - 1]: # 跳过重复
                            l += 1
                        while l < r and nums[r] == nums[r + 1]: # 跳过重复
                            r -= 1
                    elif s < 0:
                        l += 1
                    else:
                        r -= 1
            return res
    ```


### 16. Three Sum Closest

=== "Python: 排序+双指针"

    ```py
    class Solution: # (1) 经典算法，多想多练把
        def threeSumClosest(self, nums: list[int], target: int) -> int:
            nums.sort()
            n = len(nums)
            best = 10 ** 5

            def update(cur):
                nonlocal best
                if abs(cur - target) < abs(best - target):
                    best = cur
            
            for i in range(n):
                if i > 0 and nums[i] == nums[i - 1]: # 跳过重复
                    continue
                l, r = i + 1, n - 1
                while l < r:
                    s = nums[i] + nums[l] + nums[r]
                    if s == target:
                        return target
                    update(s)
                    if s > target:
                        r0 = r - 1
                        while l < r0 and nums[r0] == nums[r]: # 跳过重复
                            r0 -= 1
                        r = r0
                    else:
                        l0 = l + 1
                        while l0 < r and nums[l0] == nums[l]: # 跳过重复
                            l0 += 1
                        l = l0
            return best
    ```

    1. :white_check_mark: 2025/04/07


### 17. letter combination of a phone number

=== "Python: 迭代方法"

    ```py
    class Solution: # (1) 迭代(循环)方法
    def letterCombinations(self, digits: str) -> list[str]:
        ascii_code = 97
        map = dict()
        for i in range(8):
            ls = list()
            for _ in range(3):
                ls.append(chr(ascii_code))
                ascii_code += 1
            if i + 2 == 7:
                ls.append('s')
                ascii_code += 1
            if i + 2 == 9:
                ls.append('z')
                ascii_code += 1
            map[i + 2] = ls
        
        if digits == '':
            return []
        if len(digits) == 1:
            return map[int(digits)]
        
        res = self.comb(map[int(digits[0])], map[int(digits[1])])
        digits = digits[2:]
        while digits:
            res = self.comb(res, map[int(digits[0])])
            digits = digits[1:]
        
        return res

    def comb(self, ls1: list, ls2: list) -> list[str]:
        combination = list()
        for i in ls1:
            for j in ls2:
                combination.append(i + j)
        return combination
    ```

    1. :white_check_mark: 2025/04/08

=== "Recursion"

    ```py
    class Solution:
        def letterCombinations(self, digits: str) -> list[str]:
            # mapping硬编码
            phoneMap = {
                "2": "abc",
                "3": "def",
                "4": "ghi",
                "5": "jkl",
                "6": "mno",
                "7": "pqrs",
                "8": "tuv",
                "9": "wxyz",
            }

            if not digits:
                return []

            # 递归辅助函数
            def helper(index: int) -> list[str]:
                # base case
                if index == len(digits):
                    return [""]
                # 获取子问题的结果，后续所有数字的组合
                sub_result = helper(index + 1)

                # 取出当前数字对应的字母
                current_letter = phoneMap[digits[index]]
                
                # 递归调用
                result = []
                for letter in current_letter:
                    for sub_str in sub_result:
                        result.append(letter + sub_str)
                return result
            
            return helper(0)
    ```

### 18. Four Sum

=== "Python: 排序+双指针"

    ```py
    class Solution: # (1) 和three sum一样，这里就是多了层for循环，然后记得跳过重复的数字。😑
        def fourSum(self, nums: list[int], target: int) -> list[list[int]]:
            nums.sort()
            n = len(nums)
            res = list()
            
            for i in range(n):
                if i > 0 and nums[i] == nums[i-1]: # skip duplicates
                    continue
                for j in range(i+1, n):
                    if j > i+1 and nums[j] == nums[j-1]: # skip duplicates
                        continue
                    l = j + 1
                    r = n - 1
                    while l < r:
                        s = nums[i] + nums[j] + nums[l] + nums[r]
                        if s == target:
                            res.append([nums[i], nums[j], nums[l], nums[r]])
                            l += 1
                            r -= 1
                            while l < r and nums[l] == nums[l-1]: # skip duplicates
                                l += 1
                            while l < r and nums[r] == nums[r+1]: # skip duplicates
                                r -= 1
                        elif s < target:
                            l += 1
                        else:
                            r -= 1

            return res
    ```

    1. :white_check_mark: 2025/04/08


### 19. Remove Nth Node From End of List