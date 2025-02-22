# math-quizz
import random

listquestion = []
listcorrect = []
lista = []
listb = []
listc = []
listd = []

f = open('questions.txt', 'r')
for line in f:
    l = line.replace('\n', ' ')
    w = line.strip().split(';')
    # print(w)
    listquestion.append(w[0])
    lista.append(w[1])
    listb.append(w[2])
    listc.append(w[3])
    listd.append(w[4])
    listcorrect.append(w[5])
allcount = 0
countcorrect = 0
print('       Math Quiz         ')
name = input('your name - ')
count = int(input('number of questions - '))

for i in range(count):
    random_index = random.randint(0, len(listquestion) - 1)
    q = listquestion[random_index]
    a = lista[random_index]
    b = listb[random_index]
    c = listc[random_index]
    d = listd[random_index]
    correct = listcorrect[random_index]
    variants = {
        "a": a,
        "b": b,
        "c": c,
        "d": d
    }
    r = input(f'{q} a) {variants["a"]} b) {variants["b"]} c) {variants["c"]} d) {variants["d"]} ').strip().lower()
    if r in variants and variants[r] == correct:
        print(' Correct!')
        countcorrect +=1
    else:
        print(f' Wrong! Correct answer: {correct}')
    allcount+=1
result = f'{countcorrect}/{allcount}'
f1 = open('data.txt','a')
f1.write(f'{name},{result}\n')
