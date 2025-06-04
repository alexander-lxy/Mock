###[3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)
Given a string s, find the length of the longest substring without duplicate characters.

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.


Constraints:

0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces


```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int ans = 0;
        int[] hash = new int[128];
        int l = 0;
        int r = 0;
        while (r < s.length()) { // must be not r++
            char c = s.charAt(r);
            hash[c]++;
            while(hash[c] > 1) {
                hash[s.charAt(l)]--;
                l++;
            }
            ans = Math.max(ans, r - l + 1);
            r++;
        }
        return ans;
    }
}


class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        ans = 0
        map = defaultdict(int) // a regular dictionary and it provides a default value for non-existent key
        l = 0
        for r, c in enumerate(s): // you can get the index position and character at the same time
            map[c] += 1 
            while map[c] > 1:
                map[s[l]] -= 1
                l += 1
            ans = max(ans, r - l + 1)
        return ans


class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int ans = 0;
        // std::vector<int> map(128, 0);
        std::unordered_map<char, int> map;
        int l = 0;
        int r = 0;
        int n = s.size();
        while (r < n) {
            map[s[r]]++;
            while (map[s[r]] > 1) {
                map[s[l++]]--;
            }
            ans = max(ans, r - l + 1);
            r++;
        }
        return ans;
    }
};
```


