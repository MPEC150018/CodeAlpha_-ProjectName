import random

# List of predefined words
words = ["python", "computer", "programming", "developer", "hangman"]

# Select a random word
word = random.choice(words)

guessed_letters = []
incorrect_guesses = 0
max_incorrect_guesses = 6

print("🎮 Welcome to Hangman Game!")
print("Guess the word one letter at a time.")

while incorrect_guesses < max_incorrect_guesses:
    # Display current progress
    display_word = ""
    for letter in word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word)
    print(f"Incorrect guesses left: {max_incorrect_guesses - incorrect_guesses}")

    # Check if word is completely guessed
    if "_" not in display_word:
        print("\n🎉 Congratulations! You guessed the word:", word)
        break

    guess = input("Enter a letter: ").lower()

    # Validation
    if len(guess) != 1 or not guess.isalpha():
        print("⚠ Please enter a single alphabet letter.")
        continue

    if guess in guessed_letters:
        print("⚠ You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess in word:
        print("✅ Correct guess!")
    else:
        incorrect_guesses += 1
        print("❌ Wrong guess!")

# Game Over
if incorrect_guesses == max_incorrect_guesses:
    print("\n💀 Game Over!")
    print("The correct word was:", word)
