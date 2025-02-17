[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/6wGdpkN5)
# Longest Nice Substring

class Solution {
public:
    string longestNiceSubstring(string s) {
        if (s.size() < 2) return "";

        unordered_set<char> charSet(s.begin(), s.end());

        for (int i = 0; i < s.size(); i++) {
            if (charSet.count(tolower(s[i])) && charSet.count(toupper(s[i]))) continue;
            
            // Recursively check left and right substrings
            string left = longestNiceSubstring(s.substr(0, i));
            string right = longestNiceSubstring(s.substr(i + 1));

            return left.size() >= right.size() ? left : right;
        }
        
        return s; 
    }
};

# Output
![image](https://github.com/user-attachments/assets/c72389ab-3bd5-4289-9710-359c1e55c6ad)


# Reverse Bits

class Solution {
public:
    uint32_t reverseBits(uint32_t n) {
        uint32_t res = 0;
        
        for (int i = 0; i < 32; i++) {
            res = (res << 1) | (n & 1); 
            n >>= 1; 
        }
        
        return res;
    }
};


# Output
![image](https://github.com/user-attachments/assets/011cea06-ba9c-4890-b377-8f88ae2c5f19)

# Number of 1 Bits

class Solution {
public:
    int hammingWeight(int n) {
        int count = 0;
        while (n) {
            n &= (n - 1); 
            count++;
        }
        return count;
    }
};


# Output
![image](https://github.com/user-attachments/assets/0d162c1d-2450-4593-91e2-8c837888735e)


# Max SubArray
class Solution {
public:
    int maxSubArray(std::vector<int>& nums) {
        int maxSum = nums[0];
        int currentSum = nums[0];

        for (size_t i = 1; i < nums.size(); i++) {
            currentSum = std::max(nums[i], currentSum + nums[i]);
            maxSum = std::max(maxSum, currentSum);
        }

        return maxSum;
    }
};

# Output
![image](https://github.com/user-attachments/assets/558a74c2-152d-42a7-99fe-df441b630b0d)


# Search 2d Matrix 2
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
     int m = matrix.size(), n = matrix[0].size(), row = 0, col = n - 1;
        while (row < m && col >= 0) {
            if (matrix[row][col] == target) return true;
            matrix[row][col] > target ? col-- : row++;
        }
        return false;   
    }
};

# Output
![image](https://github.com/user-attachments/assets/9bad5a42-20c0-4f96-a2e7-3e19186f60e6)

# Sub Pow
class Solution {
public:
const int MOD = 1337;
    
    int modPow(int x, int n) {
        int res = 1;
        x %= MOD;
        while (n > 0) {
            if (n % 2) res = (res * x) % MOD;
            x = (x * x) % MOD;
            n /= 2;
        }
        return res;
    }
    int superPow(int a, vector<int>& b) {
     int res = 1;
        for (int digit : b)
            res = (modPow(res, 10) * modPow(a, digit)) % MOD;
        return res;   
    }
};

# Output
![image](https://github.com/user-attachments/assets/ad767547-75d4-43f2-8f4f-9d3881671d4e)

# Beautiful Array
class Solution {
public:
    vector<int> beautifulArray(int n) {
     vector<int> res = {1};
        while (res.size() < n) {
            vector<int> temp;
            for (int num : res) if (num * 2 - 1 <= n) temp.push_back(num * 2 - 1);
            for (int num : res) if (num * 2 <= n) temp.push_back(num * 2);
            res = temp;
        }
        return res;   
    }
};

# Output
![image](https://github.com/user-attachments/assets/fbe7e7f1-bd15-4f90-b7fe-af7d7a5051b4)

# The Skyline Problem
class Solution {

public:

    vector<vector<int>> getSkyline(vector<vector<int>>& buildings) {

        vector<pair<int, int>> events;

        for (auto& b : buildings) {

            events.emplace_back(b[0], -b[2]);

            events.emplace_back(b[1], b[2]);

        }

        sort(events.begin(), events.end());

        

        multiset<int> heights = {0};

        vector<vector<int>> skyline;

        int prevHeight = 0;

        

        for (auto& [x, h] : events) {

            if (h < 0) heights.insert(-h);

            else heights.erase(heights.find(h));

            int currHeight = *heights.rbegin();

            if (currHeight != prevHeight) {

                skyline.push_back({x, currHeight});

                prevHeight = currHeight;

            }

        }

        return skyline;

    }

};
# Output
![image](https://github.com/user-attachments/assets/d4500d9a-5182-4f85-8bbf-5b90c9c0f35e)

# Reverse Pairs
class Solution {

public:

    int reversePairs(vector<int>& nums) {

        return mergeSort(nums, 0, nums.size() - 1);

    }



    int mergeSort(vector<int>& nums, int l, int r) {

        if (l >= r) return 0;

        int mid = (l + r) / 2, count = mergeSort(nums, l, mid) + mergeSort(nums, mid + 1, r);

        int j = mid + 1;

        

        for (int I = l; I <= mid; I++) {

            while (j <= r && nums[I] > 2LL * nums[j]) j++;

            count += (j - (mid + 1));

        }



        inplace_merge(nums.begin() + l, nums.begin() + mid + 1, nums.begin() + r + 1);

        return count;

    }

};
# Output
![image](https://github.com/user-attachments/assets/f048c55c-36c6-4571-9361-355e359fb941)

# Longest Increasing Subsequence II
#include <vector>

#include <map>

using namespace std;



class Solution {

public:

    int lengthOfLIS(vector<int>& nums, int k) {

        map<int, int> dp;

        int maxLen = 1;

        

        for (int num : nums) {

            int best = 0;

            for (auto it = dp.lower_bound(num - k); it != dp.upper_bound(num - 1); ++it)

                best = max(best, it->second);

            

            dp[num] = best + 1;

            maxLen = max(maxLen, dp[num]);

        }

        

        return maxLen;

    }

};
# Output
![image](https://github.com/user-attachments/assets/085fa602-513d-4095-9330-483dcef8653f)
