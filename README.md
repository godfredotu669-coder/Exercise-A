# Exercise-A
Number guessing game
import random

def number_guessing_game():
    """
    A number guessing game where the computer picks a secret number
    and the player tries to guess it with hints.
    """
    # Game setup
    secret_number = random.randint(1, 100)
    attempts = 0
    max_attempts = 10
    
    print("=" * 50)
    print("Welcome to the Number Guessing Game!")
    print("=" * 50)
    print(f"I'm thinking of a number between 1 and 100.")
    print(f"You have {max_attempts} attempts to guess it.")
    print("Let's begin!\n")
    
    # Main game loop
    while attempts < max_attempts:
        try:
            # Get player input
            guess = int(input(f"Attempt {attempts + 1}/{max_attempts} - Enter your guess: "))
            attempts += 1
            
            # Check the guess
            if guess < 1 or guess > 100:
                print("Please guess a number between 1 and 100!\n")
                attempts -= 1  # Don't count invalid guesses
                continue
            
            if guess < secret_number:
                print("Too Low! Try a higher number.\n")
            elif guess > secret_number:
                print("Too High! Try a lower number.\n")
            else:
                print("=" * 50)
                print(f"🎉 Congratulations! You guessed it in {attempts} attempts!")
                print(f"The secret number was {secret_number}!")
                print("=" * 50)
                break
        
        except ValueError:
            print("Invalid input! Please enter a number.\n")
            attempts -= 1  # Don't count invalid inputs
    
    else:
        # This runs if the loop completes without breaking (player ran out of attempts)
        print("=" * 50)
        print(f"Game Over! You've used all {max_attempts} attempts.")
        print(f"The secret number was {secret_number}.")
        print("Better luck next time!")
        print("=" * 50)
    
    # Ask if they want to play again
    play_again = input("\nWould you like to play again? (yes/no): ").lower()
    if play_again in ['yes', 'y']:
        print("\n")
        number_guessing_game()
    else:
        print("Thanks for playing! Goodbye!")

# Start the game
if __name__ == "__main__":
    number_guessing_game()
