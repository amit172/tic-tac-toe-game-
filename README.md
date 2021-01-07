# We will make the board using dictionary in which keys will be the location(i.e : top-left,mid-right,etc.)and initialliy it's values will be empty space and then after every move we will change the value according to player's choice of move. 

theBoard = {'7': ' ' , '8': ' ' , '9': ' ' , '4': ' ' , '5': ' ' , '6': ' ' , '1': ' ' , '2': ' ' , '3': ' ' }
def printBoard(board):
    print(board['7'] + ' | ' + board['8'] + ' | ' + board['9'])
    print('--+---+--')
    print(board['4'] + ' | ' + board['5'] + ' | ' + board['6'])
    print('--+---+--')
    print(board['1'] + ' | ' + board['2'] + ' | ' + board['3'])


    
# Now we'll write the main function which has all the gameplay functionality


def game():
    turn = 'X'
    count = 0

    for i in range(10):
        printBoard(theBoard)
        print( "It's your turn," + turn + ".Move to which place?")

        move = input()

        if theBoard[move] == ' ':
            theBoard[move] = turn
            count += 1

            
# Now we will check if player X or O has won,for every move after 5 moves.
            
            if count>=5 and count<9:
                if theBoard['7'] == theBoard['8'] == theBoard['9'] != ' ': 
                    print(" \n$$$$$$ " +turn + " WON $$$$$$\n")
                    printBoard(theBoard)
                    play_again()
                    break
                elif theBoard['4'] == theBoard['5'] == theBoard['6'] != ' ': 
                    print("\n $$$$$$ " +turn + " WON $$$$$$\n")
                    printBoard(theBoard)
                    play_again()
                    break
                elif theBoard['1'] == theBoard['4'] == theBoard['7'] != ' ':
                    print(" \n$$$$$$ " +turn + " WON $$$$$$\n")
                    printBoard(theBoard)
                    play_again()
                    break
         
                elif theBoard['2'] == theBoard['5'] == theBoard['8'] != ' ': 
                    print(" \n$$$$$$ " +turn + " WON $$$$$$\n")
                    printBoard(theBoard)
                    play_again()
                    break
         
                elif theBoard['3'] == theBoard['6'] == theBoard['9'] != ' ':
                    print("\n$$$$$$ " +turn + " WON $$$$$$\n")
                    printBoard(theBoard)
                    play_again()
                    break
         
                elif theBoard['7'] == theBoard['5'] == theBoard['3'] != ' ': 
                    print("\n $$$$$$ " +turn + " WON $$$$$$\n")
                    printBoard(theBoard)
                    play_again()
                    break
         
                elif theBoard['1'] == theBoard['5'] == theBoard['9'] != ' ':
                    print(" \n$$$$$$ " +turn + " WON $$$$$$\n")
                    printBoard(theBoard)
                    play_again()
                    break
                
                else:
                    if turn =='X':
                        turn= 'O' 
                    else:
                        turn= 'X'
                    
        
# If neither X nor O wins and the board is full, we'll declare the result as 'tie'.   
            
            elif count == 9:
                print("\nGAME OVER.\n")
                print("It's a Tie!!")
                play_again()
                break
# Now we have to change the player after every move.
            
            else:
                if turn =='X':
                    turn= 'O' 
                else:
                    turn= 'X'
            
        else:
            print("That place is already filled.\nMove to which place?")
            continue

# Now we will ask if player wants to restart the game or not.

def play_again():
    board=[]
    for key in theBoard:
        board.append(key)
    
    print("DO YOU WANT TO PLAY AGAIN TYPE [Y/N]")
    a=input()
    if a.upper()=="Y":
        for i in board:
            theBoard[i]=' '
        game()
    else:
        print("THANKS TO PLAY")
    
game()
