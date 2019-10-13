#include <iostream>
#include <cstdlib>
#include <ctime>
#include <cmath>
using namespace std;

int main() {
	srand(time(0));
	cout << "Welcome to Beat That++!" << endl;
	int bet = 10, compDice3, dice3, dice4, compbet = 10, money;
	double differ;
	string nextdice, cont;
	while(bet > 0 && compbet > 0){
		int compDice1 = rand() % 6 + 1, compDice2 = rand() % 6 + 1;
		if(compDice1 > compDice2){
			compDice3 = compDice1 * 10 + compDice2;
			cout << "The Computer rolled " << compDice1 << " and " << compDice2 <<", so the score is " << compDice3 << "..." << endl;
		}
		if(compDice2 > compDice1){
			compDice3 = compDice2 * 10 + compDice1;
			cout << "The Computer rolled " << compDice1 << " and " << compDice2 <<", so the score is " << compDice3 << "..." << endl;
		}
		int dice1 = rand() % 6 + 1, dice2 = rand() % 6 + 1;
		cout << "You rolled " << dice1 << ", roll again? ";
		cin >> nextdice;
		if(nextdice == "y" || nextdice == "Y"){
				if(dice1 > dice2){
				dice3 = dice1 * 10 + dice2;
				cout << "You rolled " << dice1 << " and " << dice2 <<", so the score is " << dice3 << "... ";
		}
				if(dice2 > dice1){
				dice3 = dice2 * 10 + dice1;
				cout << "You rolled " << dice1 << " and " << dice2 <<", so the score is " << dice3 << "... ";
		}
		}
		if(nextdice == "n" || nextdice == "N"){
				dice4 = dice1 * 10 + dice1;
				cout << "You rolled " << dice1 << " and " << dice1 << ", so the score is " << dice4 << "... ";
		}
		else {
				cout << "** Oops type 'y/Y' or 'n/N'";
				cin >> nextdice; // fix
		}
		if(compDice3 == dice3 || compDice3 == dice4) {
			cout << "tied..." << endl;
			cout << "You have $" << bet << ", computer has $" << compbet << endl;
		}
		if(compDice3 > dice3 || compDice3 > dice4){
			if(dice3 > 1) {
			differ = (compDice3 - dice3) / 10;
			money = nearbyint(differ);
		}
			if(dice4 > 1){
			differ = (compDice3 - dice4) / 10;
			money = nearbyint(differ);
		}
		cout << "You lost $" << money << "..." << endl;
		compbet = compbet + money; bet = bet - money;
		cout << "You have $" << bet << ", computer has $" << compbet << endl;
		}
		if(compDice3 < dice3 || compDice3 < dice4){
			if(dice3 > 1) {
		    differ = (dice3 - compDice3) / 10;
		    money = nearbyint(differ);
		}
			if(dice4 > 1){
		    differ = (dice4 - compDice3) / 10;
				money = nearbyint(differ);
		}  
			cout << "You won $" << money << "..." << endl;
			compbet = compbet - money; bet = bet + money;
			cout << "You have $" << bet << ", computer has $" << compbet << endl;
		}
		cout << "Continue? ";
		cin >> cont;
		if(cont == "n" || cont == "N") break;
		}
	cout << "Final: you have $" << bet << ", computer has $" << compbet << ", thanks for gaming with me" << endl;
	return 0;
}
