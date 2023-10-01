## Day 1 ##
LeetCode
Integer to Roman : 1st submission Successful: Runtime 45ms Beats 87.48%: Memory 16.30mb Beats 73.99%

Roman numerals are represented by seven different symbols: I = 1, V = 5, X = 10, L = 50, C = 100, D = 500 and M = 1000.
Six instances this rule breaks.
  IV = 4, IX = 9, XL = 40, XC = 90, CD = 400, CM = 900 

INPUT: Integer
OUTPUT: Roman Numera Representation: String

EXAMPLES:
f(3) = "III"
f(58) = "LVIII"
f(1994) = "MCMXCIV"

MY SOLUTION
Time complexity O(1)
'''
class Solution:
    def intToRoman(self, nums: int) -> str:
        
        key = [(1000, 'M'), (900, 'CM'), (500, 'D'), (400, 'CD'), 
                (100, 'C'), (90, 'XC'), (50, 'L'),  (40, 'XL'), 
                (10, 'X'), (9, 'IX'), (5, 'V'), (4, 'IV'), (1, 'I')]
        
        current_total = nums
        solution = []

        for key_pairs in key:
            value  = key_pairs[0]
            string = key_pairs[1]

            if current_total >= value:
                while current_total >= value:
                    solution.append(string)
                    current_total -= value
            if current_total == 0:
                return ''.join(solution)
            elif current_total < 0:
                print('ERROR < 0')
                return 0
'''
LeetCode
Find the Index of the first occurrence in a String: 3rd submission Successful and optimized : Runtime 29ms Beats 96.14% : Memory 16.18 MB Beats 84.45%

Given two strings -needle- and -haystack-, return the first occurrence of needle in haystack.

INPUT: haystack: str, needle: str
Output: index: int  NOTE: -1 if no occurrence.

Constraints 1 <= haystack.length, needle.length <= 10^4
haystack and needle consist of only lowercase English characters

Examples:
INPUT: haystack = "sadbutsad", needle = "sad"
OUTPUT: 0

INPUT: haystack = "leetcode", needle = "leeto"
output = -1

My Solution
Time Complexity O(n) where n is length of haystack

'''
class Solution:
    
    def strStr(self, haystack: str, needle: str) -> int:
        #  Case: Where strs are same length
        if len(haystack) == len(needle) and haystack == needle:
            return 0
        
        #  Case: Where needle is single char
        if len(needle) == 1:
            for idx in range(len(haystack)):
                if haystack[idx] == needle:
                    return idx    

        #  General Case
        for idx in range(len(haystack) - len(needle) + 1):
            if haystack[idx] == needle[0] and haystack[idx + len(needle) - 1] == needle[-1]:
                if haystack[idx:idx + len(needle)] == needle:
                    return idx
        return -1


'''
