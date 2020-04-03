# Hangman Initial Project

# collects word from the user and start game screen
worda = input("Enter The Guess Word: ")
x = len(worda)
w = 3
screen = ["_", ] * x
life = "0" * w
print(screen)
print("Lives: " + life)

# turns string input into list
z = 0
wordb = []

while z < x:
    wordb.insert(z, worda[z])
    z += 1

# collect a letter from user compare and replace
while screen != wordb and w != 0:
    letter = input("Guess a  letter: ")
    try:
        y = worda.index(letter)
        b = worda.count(letter)
        d = 0
# resolves case if there are multiple of a letter
        if b > 1:
            while d < b:
                c = [i for i, x in enumerate(worda) if x == letter]
                screen[c[d]] = letter
                d += 1
            print(screen)
            print("Lives: " + life)

 # resolves case of single letter
        else:
            y = worda.index(letter)
            screen[y] = letter
            print(screen)
            print("Lives: " + life)
# deducts life for wrong input
    except ValueError:
        w = w - 1
        life = "0" * w
        print(screen)
        print("Lives: " + life)
# print end game screen
if w == 0:
    print("You Lose!")
else:
    print("You Won Congratulations!!! ")
