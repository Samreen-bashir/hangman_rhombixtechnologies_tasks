# hangman_rhombixtechnologies_tasks
import random
def hangman():
    # Predefined list of words
    words = ['python', 'javascript', 'hangman', 'programming', 'developer', 'algorithm']
    
    # Randomly choose a word from the list
    word = random.choice(words)
    
    # Initialize the game variables
    guessed_letters = []
    attempts_left = 6  # Number of attempts before the game is over
    word_display = ['_'] * len(word)  # Word to display to the user
    
    # Function to display the current state of the word
    def display_word():
        return ' '.join(word_display)
    
    print("Welcome to Hangman!")
    print(f"The word has {len(word)} letters.")
    
    # Main game loop
    while attempts_left > 0:
        print(f"\nWord: {display_word()}")
        print(f"Guessed letters: {', '.join(guessed_letters)}")
        print(f"Attempts left: {attempts_left}")
        
        # Get user input (a letter)
        guess = input("Guess a letter: ").lower()
        
        # Check if the input is valid
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a valid letter.")
            continue
        
        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue
        
        # Add the guess to the list of guessed letters
        guessed_letters.append(guess)
        
        # Check if the letter is in the word
        if guess in word:
            print(f"Good guess! The letter '{guess}' is in the word.")
            # Update the word display with the correctly guessed letter
            for i in range(len(word)):
                if word[i] == guess:
                    word_display[i] = guess
        else:
            print(f"Sorry, the letter '{guess}' is not in the word.")
            attempts_left -= 1
        
        # Check if the player has won
        if ''.join(word_display) == word:
            print(f"\nCongratulations! You've guessed the word '{word}' correctly.")
            break
    else:
        print(f"\nGame Over! The word was '{word}'. Better luck next time!")

# Run the game
if __name__ == "__main__":
    hangman()
