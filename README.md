import re

def assess_password_strength(password):
    # Criteria
    length_criteria = len(password) >= 8
    uppercase_criteria = bool(re.search(r'[A-Z]', password))
    lowercase_criteria = bool(re.search(r'[a-z]', password))
    digit_criteria = bool(re.search(r'[0-9]', password))
    special_char_criteria = bool(re.search(r'[!@#$%^&*(),.?":{}|<>]', password))
    
    # Strength levels
    strength = 0
    if length_criteria: strength += 1
    if uppercase_criteria: strength += 1
    if lowercase_criteria: strength += 1
    if digit_criteria: strength += 1
    if special_char_criteria: strength += 1
    
    # Feedback
    feedback = "Password strength: "
    if strength == 5:
        feedback += "Very Strong"
    elif strength == 4:
        feedback += "Strong"
    elif strength == 3:
        feedback += "Moderate"
    elif strength == 2:
        feedback += "Weak"
    else:
        feedback += "Very Weak"
    
    # Additional suggestions
    suggestions = []
    if not length_criteria:
        suggestions.append("Make your password at least 8 characters long.")
    if not uppercase_criteria:
        suggestions.append("Add at least one uppercase letter.")
    if not lowercase_criteria:
        suggestions.append("Add at least one lowercase letter.")
    if not digit_criteria:
        suggestions.append("Include at least one digit.")
    if not special_char_criteria:
        suggestions.append("Add at least one special character (e.g., !@#$%^&*).")
    
    # Output feedback and suggestions
    print(feedback)
    if suggestions:
        print("Suggestions to improve your password strength:")
        for suggestion in suggestions:
            print("-", suggestion)

# Main function to run the password strength tool
if __name__ == "__main__":
    password = input("Enter your password: ")
    assess_password_strength(password)