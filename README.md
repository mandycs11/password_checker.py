import re

def password_strength_checker(password):
  """
  Assesses the strength of a password based on various criteria.

  Args:
    password: The password string to be evaluated.

  Returns:
    A string indicating the password strength:
      - "Very Weak"
      - "Weak"
      - "Medium"
      - "Strong"
      - "Very Strong"
  """

  length = len(password)
  has_upper = re.search(r'[A-Z]', password) is not None
  has_lower = re.search(r'[a-z]', password) is not None
  has_digit = re.search(r'\d', password) is not None
  has_special = re.search(r'[!@#$%^&*()_+{}\[\]:;<>,.?~-]', password) is not None

  strength = 0

  if length >= 8:
    strength += 1
  if length >= 12:
    strength += 1

  if has_upper:
    strength += 1
  if has_lower:
    strength += 1
  if has_digit:
    strength += 1
  if has_special:
    strength += 1

  if strength <= 1:
    return "Very Weak"
  elif strength <= 2:
    return "Weak"
  elif strength <= 3:
    return "Medium"
  elif strength <= 4:
    return "Strong"
  else:
    return "Very Strong"

# Get user input
password = input("Enter the password: ")

# Check password strength
strength = password_strength_checker(password)

# Provide feedback to the user
print(f"Password Strength: {strength}")
