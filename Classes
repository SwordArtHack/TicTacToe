from random import choice
from itertools import permutations

class Cell:
    def __init__(self):
        self.value = 0 # 0 - клетка свободна; 1 - стоит крестик; 2 - стоит нолик.
    
    def __bool__(self):
        return self.value == 0


class TicTacToe:
    FREE_CELL = 0      # свободная клетка
    HUMAN_X = 1        # крестик (игрок - человек)
    COMPUTER_O = 2     # нолик (игрок - компьютер)

    is_human_win = None
    is_computer_win = None
    is_draw = None

    free_coords = [
    (0, 0), (0, 1), (0, 2),
    (1, 0), (1, 1), (1, 2),
    (2, 0), (2, 1), (2, 2),
    ]



    def __init__(self):
        self.init()
    
    def __chekc_index(self, indx):
        if indx[0] < 0 or indx[0] >= 3 or indx[1] < 0 or indx[1] >= 3:
            raise IndexError('некорректно указанные индексы')
    
    def __check_value(self, value):
        if not type(value) == int:
            raise TypeError('значения матрицы должны быть числами')
    
    def __getitem__(self, item):
        self.__chekc_index(item)
        return self.pole[item[0]][item[1]]
    
    def __setitem__(self, item, value):
        self.__chekc_index(item)
        self.__check_value(value)

        self.pole[item[0]][item[1]] = value
    
    def init(self):
        self.free_coords = TicTacToe.free_coords
        self.pole = tuple(tuple(Cell() for _ in range(3)) for _ in range(3))
        self.human_coords, self.computer_coords = [], []

    def show(self):
        print()
        for row in self.pole:
            for i in row:
                print(i, end=' ')
            print()
    
    def __check_who_win(self):
        human_comb = []
        for i in permutations(coord_human, 3): # Комбинации ходов человека
            if sorted(list(i)) not in human_comb:
                human_comb.append(list(i))  #no_sort = 60    sort = 10

            if list(i) in win_combinations:
                print('Winner Human', list(i))
        del human_comb
        
        computer_comb = []
        for i in permutations(computer_coords, 3): # Комбинации ходов человека
            if sorted(list(i)) not in computer_comb:
                computer_comb.append(list(i))  #no_sort = 60    sort = 10

            if list(i) in win_combinations:
                print('Winner Computer', list(i))
        del computer_comb

        return 


    def human_go(self): # запрашивает координаты и ставит туда крестик
        coords = input('Введите координаты хода: ')

        while all(i.isdigit() for i in coords.split()):
        
            print('Ошибка координат, повторите попытку')
            coords = input('Введите координаты хода: ')

        x, y = map(int, coords.split())
        self.pole[x][y] = self.HUMAN_X
        del self.free_coords[x][y]
    
    def computer_go(self): # ставит случайным образом нолик
        x, y = choice(self.free_coords)
        self.pole[x][y] = self.COMPUTER_O
        del self.free_coords[x][y]
    
    
        


# is_human_win - возвращает True, если победил человек, иначе - False;
# is_computer_win - возвращает True, если победил компьютер, иначе - False;
# is_draw - возвращает True, если ничья, иначе - False.


# bool(game) - возвращает True, если игра не окончена (никто не победил и есть свободные клетки) и False - в противном случае.


game = TicTacToe()
game.init()
step_game = 0
while game:
    game.show()

    if step_game % 2 == 0:
        game.human_go()
    else:
        game.computer_go()

    step_game += 1


game.show()

if game.is_human_win:
    print("Поздравляем! Вы победили!")
elif game.is_computer_win:
    print("Все получится, со временем")
else:
    print("Ничья.")
Вам в программе необходимо объявить только два класса: TicTacToe и Cell так,
чтобы с их помощью можно было бы сыграть в "Крестики-нолики" между человеком и компьютером.
