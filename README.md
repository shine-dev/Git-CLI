# Git-CLI
import math
import random
import winsound

def play ():
    user =input("what is your choice ? 'r' for rock, 'p' for paper ,'s' for scissors\n")
    user=user.lower()


    computer=random.choice(('r','p','s'))

    if user==computer:
        return (0, user, computer)

    # r>s, s>p, p>r
    if  is_win(user, computer):
         return  (0, user , computer)
    return  (-1, user , computer)

   

def is_win(player,opponent):
    # return true is the player beats the opponent
    # winning condition: r>s, s>p, p>r
    if(player=='r'and opponent=='s') or(player=='s'and opponent=='p')or(player=='p'and opponent=='r'):
        return True
    return  False


def play_best_of(n):
    # play against  the computer until someone wins best of n games
    # to win , you win  ceil(n/2) games (ie 2/3,  3/5, 4/7)
    player_wins =0
    computer_wins =0
    wins_necessary = math.ceil(n/2)
    while player_wins < wins_necessary and computer_wins<wins_necessary:
        result, user, computer =play()
         # tie
        if result ==0:
               print("it is a tie .you and computer have both chosen {}:\n".format(user))
        # you win
        elif result ==1:
             player_wins +=1
             print('you chose {} and computer chose{} .you won!\n'.format(user,computer))
        else :
            computer_wins +=1
            print('you chose {} and the computer chose{}.you lost:\n'.format(user ,computer))
        print('\n')

    if  player_wins > computer_wins:
        print('you have won the best of {}games what a champ:D'.format(n))
    else:
        print('unfortunately ,the computer has won the best of {}games.better try next time'.format(user))

    

if __name__ =='__main__':
    play_best_of(3)#2






