# guessingGame
import random

def computerGuess(lowval,highval,randnum,count=0):
    if highval>=lowval:
        guess=lowval+(highval-lowval)//2
        #If the guess is the middle, it is found!
        if guess==randnum:
            return count

            
        # If "guess" s greater than the number'
        # it must be in lower half set of numbers
        # between lower value and the guess.
        elif guess>randnum:
            count=count+1
            return computerGuess(lowval,guess-1,randnum,count)
    else:
        #Number not found
        return -1
#end of function

#Generate random number
randnum=random.randint(1,101)

count=0
guess=-99
while(guess!=randnum):
    #Get the user's input
    guess= int(input("Enter your guess between 1 and 100:"))

    if guess<randnum:
        print("Higher")

    elif guess>randnum:
        print("Lower")

    else:
        print("You guessed it right!")
        break
    count=count+1
#end of while loop

print("You took "+ str(count) + " steps to guess the number!")
print("Computer took "+ str(computerGuess(0,100,randnum)) + " steps!")
