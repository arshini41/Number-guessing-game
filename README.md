# Number-guessing-game
https://roadmap.sh/projects/number-guessing-game
...
# Number Guessing Game - CLI Version

import random

# Generate random number
secret_number = random.randint(1, 100)

# Welcome Message
print("Welcome to the Number Guessing Game!")
print("I'm thinking of a number between 1 and 100.")

# Difficulty Selection
print("\nPlease select the difficulty level:")
print("1. Easy (10 chances)")
print("2. Medium (5 chances)")
print("3. Hard (3 chances)")

choice = input("\nEnter your choice: ")

# Set chances based on difficulty
if choice == "1":
    chances = 10
    level = "Easy"

elif choice == "2":
    chances = 5
    level = "Medium"

elif choice == "3":
    chances = 3
    level = "Hard"

else:
    print("Invalid choice! Defaulting to Medium difficulty.")
    chances = 5
    level = "Medium"

print(f"\nGreat! You have selected the {level} difficulty level.")
print("Let's start the game!")

attempts = 0

# Game Loop
while chances > 0:

    try:
        guess = int(input("\nEnter your guess: "))
        attempts += 1
        chances -= 1

        # Correct Guess
        if guess == secret_number:
            print(f"\nCongratulations! You guessed the correct number in {attempts} attempts.")
            break

        # Hint Messages
        elif guess > secret_number:
            print(f"Incorrect! The number is less than {guess}.")

        else:
            print(f"Incorrect! The number is greater than {guess}.")

        # Chances Left
        if chances > 0:
            print(f"You have {chances} chances left.")

    except ValueError:
        print("Please enter a valid number!")

# Game Over
if chances == 0 and guess != secret_number:
    print("\nGame Over!")
    print(f"The correct number was {secret_number}.")
