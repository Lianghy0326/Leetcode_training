# Date
## Question name and ID
### C++
``` c++
class Solution {
public:
    vector<int> maxSumOfThreeSubarrays(vector<int>& nums, int k) {
        int n;
        n = nums.size();

        vector<int> left(n,0);
        vector<int> right(n,0);

        // prefix[i] : sum {0 , i-1}
        // sum[i->i+k] = prefix[i+k+1] - prefix[i]
        vector<int> prefix(n+1,0);
        for (int i=1; i<n+1; i++){
            prefix[i] = prefix[i-1] + nums[i-1];
        }

        // find max sum of left array (OPT sum before i-index)
        // best left index must be the "start index of the array."
        int best_left = 0;
        int tmp;
        for (int i=k-1; i<n; ++i){
            tmp = prefix[i+1] - prefix[i-k+1];
            if (tmp > prefix[best_left+k]-prefix[best_left]) // 一樣會學最左邊的
                best_left = i-k+1;
            left[i] = best_left;
        }

        // find opt sub-array sum from right->left before index-i
        int best_right = n-k;
        for (int i=n-k; i>-1; i--){
            tmp = prefix[i+k] - prefix[i];
            if (tmp >= prefix[best_right+k]-prefix[best_right]) // >= means 一樣但是index較小會更新
                best_right = i;
            right[i] = best_right;
        }

        // find the middle best sub-arr-sum with limited range of index
        int best_sum = -1;
        vector<int> best_id(3);
        int l,r;
        for (int i=k; i<=n-k*2; i++){
            l = left[i-1];
            r = right[i+k];
            tmp = (prefix[l+k]-prefix[l])+(prefix[r+k]-prefix[r])+(prefix[i+k]-prefix[i]);
            if (tmp > best_sum){
                best_sum = tmp;
                best_id[0] = l;
                best_id[1] = i;
                best_id[2] = r;
            }
                
        }

        return best_id;
    }
};
```

### Python
```python

```