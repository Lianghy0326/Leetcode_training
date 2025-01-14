# 1/14
## 2657. Find the Prefix Common Array of Two Arrays
### C++
``` c++
class Solution {
public:
    vector<int> findThePrefixCommonArray(vector<int>& A, vector<int>& B) {
        vector<int> C(A.size(),0);

        // map
        unordered_map<int,int> map;

        // iter
        for (int i=0;i<A.size();++i){
            // check A[i] and B[i] ,check if == 2
            map[A[i]]++;
            map[B[i]]++;
            if (i>0)
                C[i] = C[i-1];

            if (map[A[i]]==2)
            {
                map[A[i]]=0;
                C[i]++;
            }
            if (map[B[i]]==2)
            {
                map[B[i]]=0;
                C[i]++;
            }

            
        }

        return C;
    }

};
```

### Python
```python

```