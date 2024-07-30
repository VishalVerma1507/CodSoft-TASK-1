// Task-1 
// Tic-Tac-Toe Game


#include<iostream>
#include<string>

using namespace std;

char Board[3][3] = { {'1','2','3'},{'4','5','6'},{'7','8','9'} };
int row, col;
bool draw = false;                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
char token = 'x';

string p1 = "";
string p2 = "";

void fun1()
{
    cout << "      |       |      " << endl;
    cout << "  " << Board[0][0] << "   |   " << Board[0][1] << "   |   " << Board[0][2] << "   " << endl;
    cout << "      |       |      " << endl;
    cout << "---------------------" << endl;
    cout << "      |       |      " << endl;
    cout << "  " << Board[1][0] << "   |   " << Board[1][1] << "   |   " << Board[1][2] << "   " << endl;
    cout << "      |       |      " << endl;
    cout << "---------------------" << endl;
    cout << "      |       |      " << endl;
    cout << "  " << Board[2][0] << "   |   " << Board[2][1] << "   |   " << Board[2][2] << "   " << endl;
    cout << "      |       |      " << endl;
}

void fun2()
{
    int digit;
    cout << (token == 'x' ? p1 : p2) << ", enter your choice: ";
    cin >> digit;

    if (digit == 1)
    { 
        row = 0; 
        col = 0; 
    }
    else if (digit == 2)
     { 
        row = 0; 
        col = 1; 
    }
    else if (digit == 3)
     { 
        row = 0; 
        col = 2;
     }
    else if (digit == 4)
    { 
        row = 1;
        col = 0; 
    }
    else if (digit == 5)
     {
         row = 1; 
         col = 1; 
    }
    else if (digit == 6)
     {
         row = 1; 
         col = 2; 
     }
    else if (digit == 7) 
    { 
        row = 2; 
        col = 0; 
    }
    else if (digit == 8)
     { 
        row = 2; 
        col = 1; 
     }
    else if (digit == 9) 
    { 
        row = 2; 
        col = 2; 
    }
    else {
        cout << "Invalid input!" << endl;
        fun2();
        return;
    }

    if (Board[row][col] != 'x' && Board[row][col] != '0') {
        Board[row][col] = token;
        token = (token == 'x') ? '0' : 'x';
    } else {
        cout << "No empty space left for this move!" << endl;
        fun2();
    }
}

bool fun3()
{
    for (int i = 0; i < 3; i++) {
        if ((Board[i][0] == Board[i][1] && Board[i][0] == Board[i][2]) || 
            (Board[0][i] == Board[1][i] && Board[0][i] == Board[2][i]))
            return true;
    }

    if ((Board[0][0] == Board[1][1] && Board[1][1] == Board[2][2]) || 
        (Board[0][2] == Board[1][1] && Board[1][1] == Board[2][0]))
        return true;

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (Board[i][j] != 'x' && Board[i][j] != '0')
                return false;
        }
    }
    draw = true;
    return true;
}

int main()
{
    cout << "Enter the name of the first player: ";
    getline(cin, p1);
    cout << "Enter the name of the second player: ";
    getline(cin, p2);
    cout << endl;
    cout << p1 << " is the first player, so will play first." << endl;
    cout << p2 << " is the second player, so will play second.\n\n" << endl;

    while (!fun3()) {
        fun1();
        fun2();
    }

    fun1();

    if (draw) {
        cout << "Game is DRAW!" << endl;
    } else {
        if (token == 'x') {
            cout << p2 << " is the Winner!!" << endl;
        } else {
            cout << p1 << " is the Winner!!" << endl;
        }
    }

    return 0;
}
