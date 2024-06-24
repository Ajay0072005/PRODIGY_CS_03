# PRODIGY_CS_03
A tool that assesses the strength of a password

    import re
   def check_password_strength(password):
# Initialize strength criteria
      length_criteria = len(password) >= 8
      lowercase_criteria = re.search(r"[a-z]", password) is not None
      uppercase_criteria = re.search(r"[A-Z]", password) is not None
      number_criteria = re.search(r"\d", password) is not None
      special_char_criteria = re.search(r"[!@#$%^&*(),.?\":{}|<>]", password) is not None
# Calculate strength score
      strength_score = sum([length_criteria, lowercase_criteria, uppercase_criteria, number_criteria, special_char_criteria])
# Provide feedback based on strength score
      feedback = []
      if not length_criteria:
          feedback.append("Password should be at least 8 characters long.")
      if not lowercase_criteria:
        feedback.append("Password should include at least one lowercase letter.")
      if not uppercase_criteria:
          feedback.append("Password should include at least one uppercase letter.")
      if not number_criteria:
          feedback.append("Password should include at least one number.")
      if not special_char_criteria:
          feedback.append("Password should include at least one special character.")
 # Determine strength level
      if strength_score == 5:
          strength_level = "Very Strong (Thala for a reason)"
      elif strength_score == 4:
          strength_level = "Strong"
      elif strength_score == 3:
          strength_level = "Moderate"
      else:
          strength_level = "Weak"
    
      return strength_level, feedback

    def main():
      password = input("Enter your password to check its strength: ")
      strength_level, feedback = check_password_strength(password)
      print(f"Password Strength: {strength_level}")
      if feedback:
          print("Feedback:")
            for f in feedback:
              print(f" - {f}")

    if __name__ == "__main__":
      main()
