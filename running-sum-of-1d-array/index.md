# Leetcode - Running sum of 1D array


<!--more-->

# Running sum of 1D array
`Python ` `leetcode` `data structure` `algorithems`

---

> Developer : __Divyansh Patel__

## Question

QUESTION
Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]).

## Solution
### Method 1
Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]).
``` python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        final_list = []
        running_sum = 0
        for i in nums:
            if len(final_list)==0 :
                final_list.append(i)
                running_sum=i
            else:
                running_sum+=i
                final_list.append(running_sum)
        return final_list
```


