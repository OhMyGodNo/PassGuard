# PassGuard

import re

def assess_password_strength(password):
    # Criteria for password strength
    length_criteria = 8
    complexity_criteria = re.compile(r'^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[a-zA-Z\d]+$')

    # Assess length
    length_ok = len(password) >= length_criteria
    # Assess complexity
    complexity_ok = bool(complexity_criteria.match(password))

    return length_ok and complexity_ok

def password_strength_checker(password):
    strength = assess_password_strength(password)

    # Display results without colorization
    print(f"Password: {password}")
    print("Strength:", "Strong" if strength else "Weak")

    if not strength:
        print("Recommendations:")
        print("- Aim for at least 8 characters.")
        print("- Include a mix of uppercase, lowercase, and numbers.")
        print("- Avoid common words and patterns.")

if __name__ == "__main__":
    # Example usage
    user_password = input("Enter your password: ")
    password_strength_checker(user_password)
