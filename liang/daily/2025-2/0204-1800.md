# 2/4
## 1800 - Maximum ascending sub-array
### C++
``` c++
class Solution {
public:
    int maxAscendingSum(vector<int>& nums) {
        
        int sum_tmp=nums[0];
        int sum_max=sum_tmp;

        for (int i=1;i<nums.size();++i){
            
            if (nums[i]>nums[i-1])
                sum_tmp += nums[i];
            else
                sum_tmp = nums[i];

            if (sum_max < sum_tmp)
                sum_max = sum_tmp;

        }

        return sum_max;
    }
};
```

### Python
```python

```