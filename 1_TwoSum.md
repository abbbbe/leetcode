# \#1 Two Sum

**TAGS** Algorithms Array Easy

## My Submit

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> res;

        vector<int> sortedNums(nums);
        sort(sortedNums.begin(), sortedNums.end());
        
        auto iter_low = sortedNums.begin();
        auto iter_high = sortedNums.end() - 1;
        while (iter_low < iter_high) {
            while (*iter_low + *iter_high > target) {
                iter_high--;
            }

            if (*iter_low + *iter_high == target) {
                int i = 0;
                for (; i < nums.size(); i++) {
                    if (nums[i] == *iter_low) {
                        res.push_back(i);
                    }
                }
                for (i = 0; i < nums.size(); i++) {
                    if (nums[i] == *iter_high && i != res[0]) {
                        res.push_back(i);
                    }
                }

                return res;
            } 
            
            while (*iter_low + *iter_high < target) {
                iter_low++;
            }
        }
        
        return res;
    }
};
```