#  Two Sum

def twoSum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        diff = target - num
        if diff in seen:
            return [seen[diff], i]
        seen[num] = i

#  Longest Substring Without Repeating Characters

def lengthOfLongestSubstring(s):
    seen = {}
    left = max_len = 0
    for right, char in enumerate(s):
        if char in seen and seen[char] >= left:
            left = seen[char] + 1
        seen[char] = right
        max_len = max(max_len, right - left + 1)
    return max_len

#  Remove N-th Node From End of List 

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

   def removeNthFromEnd(head, n):
      temp = ListNode(0, head)
      slow = fast = temp
  
      for _ in range(n):
          fast = fast.next
  
      while fast.next:
          slow = slow.next
          fast = fast.next
  
      slow.next = slow.next.next
      return temp.next

#  Subsets

def subsets(nums):
    result = []
    def backtrack(start, path):
        result.append(path[:])
        for i in range(start, len(nums)):
            path.append(nums[i])
            backtrack(i + 1, path)
            path.pop()
    backtrack(0, [])
    return result

#  House Robber

def rob(nums):
    if not nums: return 0
    if len(nums) <= 2: return max(nums)
    dp = [0] * len(nums)
    dp[0], dp[1] = nums[0], max(nums[0], nums[1])
    for i in range(2, len(nums)):
        dp[i] = max(dp[i-1], dp[i-2] + nums[i])
    return dp[-1]

