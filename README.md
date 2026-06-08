# -Secure-Password-Generator-and-Strength-Analyzer-Using-Python-
This code generates no of random passwords of user choice of password length entered by the user
#Sample code
import random
import string

n = int(input("Enter no of passwords: "))
k = int(input("Enter length of each password: "))

if k < 4:
    print("Password length must be at least 4")
else:
    file = open("passwords.txt", "w")

    for i in range(n):
        password = [
            random.choice(string.ascii_uppercase),
            random.choice(string.ascii_lowercase),
            random.choice(string.digits),
            random.choice('@#_-£&')
        ]

        chars = string.ascii_letters + string.digits + '@#_-£&'

        for j in range(k - 4):
            password.append(random.choice(chars))

        random.shuffle(password)
        password = ''.join(password)

        if k >= 12:
            strength = "Strong"
        elif k >= 8:
            strength = "Medium"
        else:
            strength = "Weak"

        print(f"Password {i+1}: {password} ({strength})")
        file.write(f"Password {i+1}: {password} ({strength})\n")

    file.close()
    print("\nPasswords saved to passwords.txt")


