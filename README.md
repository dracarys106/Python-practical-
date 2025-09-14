# Python-practical-
Code for the given practical questions
Questions:
1.Write a program to find the roots of a quadratic equation
ans-import cmath

# Quadratic equation: ax^2 + bx + c = 0
a = float(input("Enter coefficient a: "))
b = float(input("Enter coefficient b: "))
c = float(input("Enter coefficient c: "))

# Calculate discriminant
d = (b**2) - (4*a*c)

# Calculate roots
root1 = (-b + cmath.sqrt(d)) / (2 * a)
root2 = (-b - cmath.sqrt(d)) / (2 * a)

print(f"The roots of the quadratic equation are: {root1} and {root2}")
________________________
2.Write a program to accept a number ‘n’ and a. Check if ’n’ is prime b. Generate all prime 
numbers till ‘n’ c. Generate first ‘n’ prime numbers This program may be done using functions
ans-# Function to check if a number is prime
def is_prime(num):
    if num <= 1:
        return False
    for i in range(2, int(num**0.5) + 1):
        if num % i == 0:
            return False
    return True


# Function to generate all prime numbers up to n
def primes_till_n(n):
    primes = []
    for i in range(2, n + 1):
        if is_prime(i):
            primes.append(i)
    return primes


# Function to generate first n prime numbers
def first_n_primes(n):
    primes = []
    num = 2
    while len(primes) < n:
        if is_prime(num):
            primes.append(num)
        num += 1
    return primes 
_________________________
3.Write a program to create a pyramid of the character ‘*’ and a reverse pyramid
ans-# Function to print pyramid
def pyramid(n):
    for i in range(1, n + 1):
        print(" " * (n - i) + "*" * (2 * i - 1))


# Function to print reverse pyramid
def reverse_pyramid(n):
    for i in range(n, 0, -1):
        print(" " * (n - i) + "*" * (2 * i - 1))
______________________
4.Write a program that accepts a character and performs the following:
a. print whether the character is a letter or numeric digit or a special character. 
b. if the character is a letter, print whether the letter is uppercase or lowercase
c. if the character is a numeric digit, prints its name in text (e.g., if input is 9, output is NINE)
ans-def char_type(ch):
    # a. Check type of character
    if ch.isalpha():  # Letter
        print(f"'{ch}' is a letter.")
        # b. Check case
        if ch.isupper():
            print("It is an uppercase letter.")
        else:
            print("It is a lowercase letter.")

    elif ch.isdigit():  # Digit
        print(f"'{ch}' is a numeric digit.")
        # c. Print digit name
        digit_names = {
            "0": "ZERO", "1": "ONE", "2": "TWO", "3": "THREE",
            "4": "FOUR", "5": "FIVE", "6": "SIX",
            "7": "SEVEN", "8": "EIGHT", "9": "NINE"
        }
        print(f"Its name is {digit_names[ch]}.")

    else:  # Special character
        print(f"'{ch}' is a special character.")
_______________________
5.Write a program to perform the following operations on a string 
a. Find the frequency of a character in a string. 
b. Replace a character by another character in a string. 
c. Remove the first occurrence of a character from a string. 
d. Remove all occurrences of a character from a string
ans-# Function to find frequency of a character
def char_frequency(s, ch):
    return s.count(ch)


# Function to replace a character by another
def replace_char(s, old, new):
    return s.replace(old, new)


# Function to remove first occurrence of a character
def remove_first_occurrence(s, ch):
    return s.replace(ch, "", 1)


# Function to remove all occurrences of a character
def remove_all_occurrences(s, ch):
    return s.replace(ch, "")


# -------- Main Program --------
string = input("Enter a string: ")

# a. Find frequency
ch = input("Enter character to find frequency: ")
print(f"Frequency of '{ch}' = {char_frequency(string, ch)}")

# b. Replace character
old = input("Enter character to replace: ")
new = input("Enter new character: ")
print("After replacement:", replace_char(string, old, new))

# c. Remove first occurrence
ch = input("Enter character to remove first occurrence: ")
print("After removing first occurrence:", remove_first_occurrence(string, ch))

# d. Remove all occurrences
ch = input("Enter character to remove all occurrences: ")
print("After removing all occurrences:", remove_all_occurrences(string, ch))
_______________________
6.Write a program to swap the first n characters of two strings.
ans-# Function to swap first n characters of two strings
def swap_first_n(s1, s2, n):
    # Ensure n is not larger than either string
    if n > len(s1) or n > len(s2):
        print("Error: n is larger than the length of one of the strings.")
        return s1, s2
    
    # Swap first n characters
    new_s1 = s2[:n] + s1[n:]
    new_s2 = s1[:n] + s2[n:]
    
    return new_s1, new_s2


# -------- Main Program --------
s1 = input("Enter first string: ")
s2 = input("Enter second string: ")
n = int(input("Enter value of n: "))

new_s1, new_s2 = swap_first_n(s1, s2, n)

print("\nAfter swapping first", n, "characters:")
print("String 1:", new_s1)
print("String 2:", new_s2)
_____________________
7.Write a function that accepts two strings and returns the indices of all the occurrences of the 
second string in the first string as a list. If the second string is not present in the first string then 
it should return -1
ans-def find_substring_indices(text, pattern):
    indices = []
    start = 0
    
    while True:
        # find substring starting from 'start'
        idx = text.find(pattern, start)
        if idx == -1:
            break
        indices.append(idx)
        start = idx + 1  # move one step ahead for next search
    
    if indices:
        return indices
    else:
        return -1


# -------- Main Program --------
s1 = input("Enter the main string: ")
s2 = input("Enter the substring to search: ")

result = find_substring_indices(s1, s2)
print("Result:", result)
_______________________
8.Write a program to create a list of the cubes of only the even integers appearing in the input 
list (may have elements of other types also) using the following:
a. 'for' loop 
b. list comprehension
ans-# -------- Main Program --------

# Sample input list (can contain integers, strings, floats, etc.)
input_list = [1, 2, "hello", 3.5, 4, 5, 6, "abc", 8]

# a. Using 'for' loop
cubes_for = []
for item in input_list:
    if isinstance(item, int) and item % 2 == 0:  # check integer & even
        cubes_for.append(item ** 3)

print("Cubes using for loop:", cubes_for)

# b. Using list comprehension
cubes_list_comp = [item ** 3 for item in input_list if isinstance(item, int) and item % 2 == 0]

print("Cubes using list comprehension:", cubes_list_comp)
_____________________
9.Write a program to read a file and 
a. Print the total number of characters, words and lines in the file. 
b. Calculate the frequency of each character in the file. Use a variable of dictionary type 
to maintain the count. 
c. Print the words in reverse order. 
d. Copy even lines of the file to a file named ‘File1’ and odd lines to another file named ‘File2’.
ans-def file_operations(filename):
    # Open file for reading
    with open(filename, "r") as f:
        lines = f.readlines()

    # a. Count characters, words, lines
    total_chars = sum(len(line) for line in lines)
    total_words = sum(len(line.split()) for line in lines)
    total_lines = len(lines)

    print("Total Characters:", total_chars)
    print("Total Words:", total_words)
    print("Total Lines:", total_lines)

    # b. Frequency of each character
    freq = {}
    for line in lines:
        for ch in line:
            freq[ch] = freq.get(ch, 0) + 1
    print("\nCharacter Frequency:")
    for k, v in freq.items():
        print(repr(k), ":", v)

    # c. Words in reverse order
    all_words = []
    for line in lines:
        all_words.extend(line.split())
    print("\nWords in reverse order:")
    print(" ".join(all_words[::-1]))

    # d. Copy even lines to File1, odd lines to File2
    with open("File1.txt", "w") as f1, open("File2.txt", "w") as f2:
        for i, line in enumerate(lines, start=1):
            if i % 2 == 0:
                f1.write(line)
            else:
                f2.write(line)
    print("\nLines have been copied: Even → File1.txt, Odd → File2.txt")


# -------- Main Program --------
filename = input("Enter the filename to process: ")
file_operations(filename)
_____________________
10.Write a program to define a class Point with coordinates x and y as attributes. Create 
relevant methods and print the objects. Also define a method distance to calculate the distance 
between any two point objects.
ans-import math

class Point:
    # Constructor
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    # Method to display point nicely
    def __str__(self):
        return f"({self.x}, {self.y})"

    # Method to calculate distance between two Point objects
    def distance(self, other):
        return math.sqrt((self.x - other.x) ** 2 + (self.y - other.y) ** 2)


# -------- Main Program --------
# Create point objects
p1 = Point(3, 4)
p2 = Point(7, 1)
p3 = Point()  # default point at (0,0)

# Print points
print("Point 1:", p1)
print("Point 2:", p2)
print("Point 3 (default):", p3)

# Calculate distance
print("Distance between Point1 and Point2:", p1.distance(p2))
print("Distance between Point1 and Point3:", p1.distance(p3))
_________________________
11.. Write a function that prints a dictionary where the keys are numbers between 1 and 5 and 
the values are cubes of the keys.
ans-def print_cubes_dict():
    cubes = {x: x**3 for x in range(1, 6)}
    print("Dictionary of cubes (1 to 5):")
    print(cubes)


# -------- Main Program --------
print_cubes_dict()
________________________
12.Consider a tuple t1=(1, 2, 5, 7, 9, 2, 4, 6, 8, 10). Write a program to perform following

operations:

a. Print half the values of the tuple in one line and the other half in the next line.

b. Print another tuple whose values are even numbers in the given tuple.

c. Concatenate a tuple t2=(11,13,15) with t1.

d. Return maximum and minimum value from this tuple
ans-# Given tuple
t1 = (1, 2, 5, 7, 9, 2, 4, 6, 8, 10)

# a. Print half values in one line and other half in next line
half = len(t1) // 2
print("First half:", t1[:half])
print("Second half:", t1[half:])

# b. Tuple of even numbers
even_tuple = tuple(x for x in t1 if x % 2 == 0)
print("Tuple of even numbers:", even_tuple)

# c. Concatenate with another tuple
t2 = (11, 13, 15)
t3 = t1 + t2
print("Concatenated tuple:", t3)

# d. Maximum and minimum value
print("Maximum value:", max(t3))
print("Minimum value:", min(t3))
________________________
13.Write a program to accept a name from a user. Raise and handle appropriate exception(s) if 
the text entered by the user contains digits and/or special characters.
ans-class InvalidNameError(Exception):
    """Custom exception for invalid names"""
    pass

def validate_name(name):
    if not name.isalpha():   # checks if all characters are letters
        raise InvalidNameError("Name should contain only alphabets (no digits or special characters).")
    return True

# -------- Main Program --------
try:
    name = input("Enter your name: ")
    validate_name(name)
    print("Valid Name:", name)

except InvalidNameError as e:
    print("Error:", e)
