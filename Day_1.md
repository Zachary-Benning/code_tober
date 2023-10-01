## Day 1 ##
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
