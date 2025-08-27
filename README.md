# Problem-Longest-Palindromic-Substring
Problem : Longest Palindromic Substring You are given a string s. Your task is to find and return the longest palindromic substring within the given string. A palindrome is a string that reads the same forwards and backwards.  Input : A string s of length n. The length of the string satisfies 1≤n≤1000. Input: "babad"
def longestPalindrome(s: str) -> str:
    if len(s) == 0:
        return ""
    start, end = 0, 0  
    def expandAroundCenter(left: int, right: int) -> int:
        while left >= 0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
        return right - left - 1 
    for i in range(len(s)):
        len1 = expandAroundCenter(i, i)
        len2 = expandAroundCenter(i, i + 1)
        max_len = max(len1, len2)
        if max_len > (end - start):
            start = i - (max_len - 1) // 2
            end = i + max_len // 2
    return s[start:end+1]
print(longestPalindrome("babad")) 
