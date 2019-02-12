# practice_assignment
!curl https://raw.githubusercontent.com/MicrosoftLearning/intropython/master/elements1_20.txt -o elements.txt

elem_txt = open('elements.txt', 'r')
elem_list = elem_txt.readlines()
elem_txt.seek(0)

elem_str = []

first_counter = 0
while first_counter < 20:
    elem_str += elem_txt.readline().lower().strip().split(',')
    first_counter += 1
    if first_counter >= 20:
        break

print("List any 5 of the first 20 elements in the Periodic table\n")
elem_guess = []

# function to collect input of 5 element names - no args - list elem_guess - no empty - 5 unique inputs, then return the list
def get_names():
    counter = 0
    while counter < 5:
        guess = input("Enter the name of an element: ")
        if guess in elem_guess:
            print(guess, "was already entered\t <--no duplicated allowed")
            pass
        elif guess == "":
            print("Nothing was entered! Try again!")
            pass
        else:
            elem_guess.append(guess)
            counter += 1
    return elem_guess

get_names()

#variables for next section
correct_guess = []
incorrect_guess = []
correct = 0
incorrect = 0
guess_counter = 0

while guess_counter < 5:
    for guess in elem_guess:
       
        if guess in elem_str:
            correct_guess.append(guess)
            guess_counter += 1
            correct += 1
        else:
            incorrect_guess.append(guess)
            guess_counter += 1
            incorrect += 1

pct_correct = correct * 20

# print output
print(pct_correct, "% correct!")
print("Found: ", correct_guess)
print("Not Found: ", incorrect_guess)
