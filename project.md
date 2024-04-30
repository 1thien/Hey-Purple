import speech_recognition as speechr
import pyttsx3
import datetime
import random
import pywhatkit



listener = speechr.Recognizer()  #Uses speech recognition and applies it to 'listener'
TTS = pyttsx3.init() #Applys the text to speech
TTS.say("I am listening, speak up")
TTS.runAndWait()

def my_order():
    try:
        with speechr.Microphone() as audio:
            print('Listening...')
            voice = listener.listen(audio) #The microphone will gather the audio in which it will convert the audio to the variable 'voice'
            command = listener.recognize_google(voice)  # Using the google's API it will now take my voice and make it a command/order
            print("Okay gotchu", command)
    except:
        pass
    return command


order = my_order()

#TIME AND DATE -----------------------------------------------------------------------------------------
def run_purple():

    if 'time' in order:
        print("24-Hour-Clock")
        time = datetime.datetime.now()
        print(time)


#ROCK PAPER GAME -----------------------------------------------------------------------------------------

    if 'rock' in order:

        from random import randrange

        choices = ["Rock", "Paper", "Scissors"]

        def playGame(playerChoice, computerChoice):
            if computerChoice == playerChoice:
                return "It's a tie!"
            elif computerChoice == "Rock":
                if playerChoice == "Paper":
                    return "You win!"
                else:
                    return "You Lose!"
            elif computerChoice == "Paper":
                if playerChoice == "Rock":
                    return "You Lose!"
                else:
                    return "You win!"
            elif computerChoice == "Scissors":
                if playerChoice == "Rock":
                    return "You win!"
                else:
                    return "You Lose!"

        def main():
            playAgain = "yes"
            while playAgain == "yes":
                playerChoice = input("Choose: Rock, Paper, or Scissors: ").capitalize()
                computerChoice = choices[randrange(3)]
                print("The computer chose: " + computerChoice)
                print("You chose: " + playerChoice)
                # print(playGame(playerChoice, computerChoice))
                session = playGame(playerChoice, computerChoice)
                print(session)
                print("\n\n---------------------------\n")
                playAgain = input("Do you want to play again?: ").lower()

            print("Thank you for Playing!")

        main()


#CALCULATOR -----------------------------------------------------------------------------------------
    if 'calculator' in order:

        print('''                   

                            WELCOME TO UCALC
                            CHOOSE AN OPTION FROM 1 TO 6

                            1. ADDITION
                            2. SUBTRACTION
                            3. MULTIPLICATION
                            4. DIVISION
                            5. EXPONENT
                            6. EXIT


        -------------------------------------------------------------''')

        def add():
            try:
                num1 = float(input('enter a number: '))
                num2 = float(input('enter another number: '))
                result = (num1 + num2)
                print(result)
            except ValueError:
                print('Please use numbers only!')

        def subtract():
            try:
                num1 = float(input('enter a number: '))
                num2 = float(input('enter another number: '))
                result = (num1 - num2)
                print(result)
            except ValueError:
                print('Please use numbers only!')

        def multiply():
            try:
                num1 = float(input('enter a number: '))
                num2 = float(input('enter another number: '))
                result = (num1 * num2)
                print(result)
            except ValueError:
                print('Please use numbers only!')

        def division():
            try:
                num1 = input('enter a number: ')
                num2 = input('enter another number: ')
                result = float(num1) / float(num2)
                print(result)
            except ValueError:
                print('Please use numbers only!')

        def exponent():
            try:
                num1 = input('enter a number: ')
                num2 = input('what would you like that number to be powered by?: ')
                result = float(num1) ** float(num2)
                print(result)
            except ValueError:
                print('Please use numbers only!')

        while True:
            try:
                inp = int(input('OPTION: '))
                if inp == 1:
                    add()
                elif inp == 2:
                    subtract()
                elif inp == 3:
                    multiply()
                elif inp == 4:
                    division()
                elif inp == 5:
                    exponent()
                elif inp == 6:
                    break
                else:
                    print('PLEASE INPUT ANY OF THE OPTION FROM 1-6')
            except ValueError:
                print('PLEASE INPUT ANY OF THE OPTION FROM 1-6')

#MUSIC---------------------------------------------------------

    if 'listen' in order:
        song = order
        pywhatkit.playonyt(song)

#COINGAME------------------------------------------------------
    if 'heads' in order:

        def coin_flip_guessing_game():
            print("Welcome to the Coin Flip Guessing Game!")
            play_again = True

            while play_again:
                print("I will flip a coin. Guess if it will land on 'heads' or 'tails'.")

                user_guess = input("Enter your guess (heads/tails): ").lower()

                coin_result = random.choice(['heads', 'tails'])

                if user_guess == coin_result:
                    print(f"The coin landed on {coin_result}. Congratulations, you guessed correctly!")
                else:
                    print(f"The coin landed on {coin_result}. Sorry, you guessed incorrectly.")

                play_again_input = input("Do you want to play again? (yes/no): ").lower()
                play_again = play_again_input == 'yes'

        if __name__ == "__main__":
            coin_flip_guessing_game()
            


run_purple()
