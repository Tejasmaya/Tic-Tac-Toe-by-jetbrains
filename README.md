```
# Tic-Tac-Toe by jetbrains
 a simple python game project

# write your code here
def result(cells):
    win_x = ['X', 'X', 'X']
    win_o = ['O', 'O', 'O']

    hor = [[cells[1][1], cells[1][2], cells[1][3]],
           [cells[2][1], cells[2][2], cells[2][3]],
           [cells[3][1], cells[3][2], cells[3][3]]]

    ver = [[cells[1][1], cells[2][1], cells[3][1]],
           [cells[1][2], cells[2][2], cells[3][2]],
           [cells[1][3], cells[2][3], cells[3][3]]]

    dia = [[cells[1][1], cells[2][2], cells[3][3]], [cells[3][1], cells[2][2], cells[1][3]]]

    if ('_' in hor[1] or '_' in hor[2] or '_' in hor[0]) \
            or (win_x in hor or win_x in ver or win_x in dia) \
            or (win_o in hor or win_o in ver or win_o in dia):
        if win_x in hor or win_x in ver or win_x in dia:
            return 'X wins'
        elif win_o in hor or win_o in ver or win_o in dia:
            return 'O wins'
        else:
            return ""
    else:
        return 'Draw'


def print_map(x):
    print(f"""
{x[0][0] * 9}
{x[1][0]}{x[1][1]} {x[1][2]} {x[1][3]}{x[1][4]}
{x[2][0]}{x[2][1]} {x[2][2]} {x[2][3]}{x[2][4]}
{x[3][0]}{x[3][1]} {x[3][2]} {x[3][3]}{x[3][4]}
{x[0][0] * 9}
""")


cells_2d = ['-', ['| ', '_', '_', '_', ' |'], ['| ', '_', '_', '_', ' |'], ['| ', '_', '_', '_', ' |'], '-']
z = 0

print_map(cells_2d)
win_or_draw = False
count_move = 1

while not win_or_draw:
    user_input = input().replace(" ", "")
    is_numeric_input = user_input.isnumeric()
    user_input = list(user_input)
    if not is_numeric_input:
        print('You should enter numbers!')
        count_move -= 1
    elif int(user_input[0]) < 0 or int(user_input[0]) > 3 or int(user_input[1]) < 0 or int(user_input[1]) > 3:
        print('Coordinates should be from 1 to 3!')
        count_move -= 1
    elif cells_2d[int(user_input[0])][int(user_input[1])] != '_':
        print('This cell is occupied! Choose another one!')
        count_move -= 1
    else:
        x = int(user_input[0])
        y = int(user_input[1])
        if count_move % 2 == 1:
            cells_2d[x][y] = 'X'
        else:
            cells_2d[x][y] = 'O'
        print_map(cells_2d)
        res = result(cells_2d)

        if any(res):
            win_or_draw = True
            print(res)
    count_move += 1
```
