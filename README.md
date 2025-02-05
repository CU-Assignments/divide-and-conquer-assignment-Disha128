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


