# Tic-Tac-Toe
#include <iostream>
#include<string>
using namespace std;
char matrix[3][3] = { '1','2', '3', '4', '5', '6', '7','8','9' };
char player = 'X';
bool check = false;
bool flag;
void draw() {
	system("cls");
	cout << "Tic Tac Toe v1.0" << endl;
	for (int i = 0; i<3; i++) {
		for (int j = 0; j<3; j++) {
			cout << matrix[i][j] << " ";
		}
		cout << endl;
	}
}
void input() {
	int a;
	cout << "Press the number of the fields";
	cin >> a;
	a--;
	if (matrix[a / 3][a % 3] == 'X' || matrix[a / 3][a % 3] == 'O') {
		cout << "The space is already occupied please enter another number ";
		cin >> a;
		a--;
		if (matrix[a / 3][a % 3] != 'X' && matrix[a / 3][a % 3] != 'O') {
			matrix[a / 3][a % 3] = player;
		}
	}
	else {
		matrix[a / 3][a % 3] = player;
	}
}
void Toggleplayer() {
	if (player == 'X')
		player = 'O';
	else
		player = 'X';
}
void win(char m[3][3]) {
int i = 0;
if (matrix[i][i] == matrix[i][i + 1] && matrix[i][i] == matrix[i][i + 2] || matrix[i + 1][i] == matrix[i + 1][i + 1] && matrix[i + 1][i] == matrix[i + 1][i + 2] || matrix[i + 2][i] == matrix[i + 2][i + 1] && matrix[i + 2][i] == matrix[i + 2][i + 2])
		check = true;
if (matrix[i][i] == matrix[i + 1][i] && matrix[i][i] == matrix[i + 2][i] || matrix[i][i + 1] == matrix[i + 1][i + 1] && matrix[i][i + 1] == matrix[i + 2][i + 1] || matrix[i][i + 2] == matrix[i + 1][i + 2] && matrix[i][i + 2] == matrix[i + 2][i + 2])
		check = true;
if (matrix[i][i] == matrix[i + 1][i + 1] && matrix[i][i] == matrix[i + 2][i + 2])
		check = true;
if (matrix[i][i + 2] == matrix[i + 1][i + 1] && matrix[i][i+ 2] == matrix[i + 2][i])
		check = true;
/*for (int i = 0; i<1; i++) {
		flag = false;
		for (int j = 0; j<3; j++) {
			if (matrix[i][j] == matrix[i][j + 1] && matrix[i][j] == matrix[i][j + 2]) {
				check = true;                                                                                                                    //00 01 02
				break;                                                                                                                          //10 11 12
			}                                                                                                                                  //20 21 22
			if (matrix[i][j] == matrix[i + 1][j] && matrix[i][j] == matrix[i + 2][j]) {
				check = true;
				break;
			}
			if (!flag) {
				flag = true;
				if (matrix[i][j] == matrix[i + 1][j + 1] && matrix[i][j] == matrix[i + 2][j + 2]) {
					check = true;
					break;
				}
				if (matrix[i][j + 2] == matrix[i + 1][j + 1] && matrix[i][j + 2] == matrix[i + 2][j]) {
					check = true;
					break;
				}
			}
			cout << "";
		}                      //matrix[2][0]==matrix[1][1] && matrix[1][1]=matrix[2][2] && matrix[2][0]==matrix[2][2]
	}*/
	
}
int main() {
	draw();
	while (1) {
		input();
		draw();
		win(matrix);
		if (check == true) {
			cout << '[' << player << ']' << " YOU WON!" << endl;
			break;
		}
		Toggleplayer();
	}
	system("pause");
}
