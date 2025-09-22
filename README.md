# Number-guessing-game


import random
import time


is_running = True



difficulties = [
    "Easy", "Medium", "Hard"
]




def show_difficulty(num):
    print(f"Great! You have selected the {difficulties[int(num) - 1]} difficulty level.")


def play_game():
    attempts = 0
    print("1. Easy (10 chances)\n\
        2. Medium (5 chances)\n" \
        "3. Hard (3 chances)")
    
    choice = input("Please select the difficulty level: ")
    if choice == "1":
       chances = 10
    elif choice == "2":
        chances = 5
    elif choice == "3":
        chances = 3
    else:
        print("Invalid, try again.")
        choice = 0
        play_game()
        return
    show_difficulty(choice)
    print("Lets start the game!")
    time.sleep(1.5)

    def guessing(chances, attempts):
        global is_running
        guess = input("Enter your choice: ")

        if not guess.isdigit():
            print("Invalid. Try again")
            guessing(chances, attempts)
        guess = int(guess)

        if chances == 0:
            print("You ran out of chances. Game over.")
            is_running = False
            return
        elif guess < random_num:
            print(f"Incorrect! The number is greater than {guess}")

            chances -= 1
            attempts += 1
            print(chances)
            guessing(chances, attempts)
        elif guess > random_num:
            print(f"Incorrect! The number is less than {guess}")

            chances -= 1
            attempts += 1
            print(f"Chances remaining: {chances}")
            guessing(chances, attempts)
        
        else:
            print(f"Congratulations! You guessed the correct number in {attempts} attempts.")
            is_running = False
            return
            

        
    guessing(chances, attempts)
   

while is_running:
    random_num = random.randint(1, 100)
    

    print("Welcome to the Number Guessing Game!")
    time.sleep(2)
    print("I'm thinking of a number between 1 and 100.")
    time.sleep(2)
    print("You have 5 chances to guess the correct number.")
    print(random_num)
    play_game()

print("Thank you for playing.")
