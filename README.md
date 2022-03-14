# 100-Game-
Two players start from 0 and alternatively add a number from 1 to 10 to the sum. The player who reaches 100 wins.




#function to make sure the user inputs right integer input
def get_int(prompt):
    while True:
        try:
            value = int (input(prompt))
        except ValueError:
            print('Invalid input. Please try again.')
            continue
        if 0 < value < 10:
            break
        else:
            print('Invalid input. Please try again.')
            continue
    return value

#function to make sure the user inputs right string input
def get_str(prompt):
    while True:
        try:
            value = str (input(prompt))
        except ValueError:
            print('Invalid input. Please try again.')
            continue
        else:
            break
    return value

#function to add numbers
def addnum(start,num):
    total = start + num
    return total

#main game
play = True
while play:
    print('Welcome to 100 Game!')
    start = 0
    print('Total = ',start)
    
    player=1
    win=0
    while True:
        print ('Player',player, end='\n')
        num = get_int('Please enter number: ')

        start = addnum(start,num)
        
        while True:
            if start == 100:
                win = 1
                break
            elif start < 100:
                print('Total = ',start)
                break
            elif start > 100:
                print('Overflow error. Total should reach 100.')
                start = start - num 
                print('Total = ',start)
                break
           
        #check winner
        if win==1:
            print('Total = ',start)
            print('Player',player,' wins!')
            break

        #each player takes a turn
        if player==1:
            player = 2
        else:
            player = 1

    #play again?
    print('Play again? Yes or No?')
    again = get_str('Answer: ')
    if again.lower()=='no':
        play = False
        print('Thank you for playing!')
