# Basic-Password-Analyzer
# Basic Password Analyzer written in python code

import string

password = input("Enter the password: ")

upper_case = any([1 if c in string.ascii_uppercase else 0 for c in password])
lower_case = any([1 if c in string.ascii_lowercase else 0 for c in password])
special = any([1 if c in string.punctuation else 0 for c in password])
digits = any([1 if c in string.digits else 0 for c in password])

characters = [upper_case, lower_case, special, digits]

length = len(password)

score = 0

with open('common.txt', 'r') as f:
    common = f.read().splitlines()

# You can find a password list in the format of a .txt file from google. In this case I named that filed common

if password in common:
        print("This password is common, please use another. Score: 0 / 7")
        exit()

if length > 8:
    score += 1
if length > 12:
    score += 1
if length > 18:
    score +=1
if length > 22:
    score +=1

print(f"Password length is {str(length)}, adding {str(score)} points!")

if sum(characters) > 1:
    score += 1
    
if sum(characters) > 2:
    score += 1
    
if sum(characters) > 3:
    score += 1

print(f"Password has {str(sum(characters))} different character types, adding {str(sum(characters) - 1)} points!")



if score < 4:
    print(f"This Password is weak! Score: {str(score)} / 7")
    
elif score == 4:
    print(f"This password is ok! Score: {str(score)} / 7")
    
elif score > 4 and score < 6:
    print(f"This password is pretty good! Score: {str(score)} / 7")
    
elif score >= 6:
    print(f"This password is strong! Score: {str(score)} / 7")
