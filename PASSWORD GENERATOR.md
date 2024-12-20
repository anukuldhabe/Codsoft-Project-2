# Codsoft-Project-2
import random
import string

def generate_password(length):
    if length < 4:
        print("Password length must be at least 4 characters for better security.")
        return None

    # Combine letters, digits, and special characters for complexity
    characters = string.ascii_letters + string.digits + string.punctuation
    
    # Ensure the password has at least one letter, one digit, and one special character
    password = [
        random.choice(string.ascii_letters),
        random.choice(string.digits),
        random.choice(string.punctuation)
    ]
    
    # Fill the rest of the password length with random choices
    password += random.choices(characters, k=length - 3)
    
    # Shuffle to ensure randomness
    random.shuffle(password)
    
    return ''.join(password)

# Prompt the user for password length
try:
    length = int(input("Enter the desired password length: "))
    password = generate_password(length)
    if password:
        print("Generated Password:", password)
except ValueError:
    print("Invalid input. Please enter a number.")
