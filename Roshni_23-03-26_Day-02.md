# Day 2 - ACM POTD

## Problem
Find two indices such that their values add up to the target.

## Approach
I used a hash map to store elements and their indices. For each element, I checked if the complement (target - current element) already exists in the map. If yes, I returned the indices.


```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> mp;

        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];

            if (mp.find(complement) != mp.end()) {
                return {mp[complement], i};
            }

            mp[nums[i]] = i;
        }

        return {};
    }
};