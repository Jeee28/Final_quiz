#include <iostream>
#include <string>
#include <iomanip>
#include <stdio.h>
#include <conio.h>
#include <windows.h>
#include <fstream>
#include <string>
using namespace std;
void loadingBar();
void registration();
void quiz();
void chamm();
void viewRecord();
void exit();
void remove();
const int MAXSIZE = 100;
const int ARRAY_SIZE = 100;
HANDLE h = GetStdHandle(STD_OUTPUT_HANDLE);
char fname[15], lname[15], username[15];
string firstname[MAXSIZE] = {};
string lastname[MAXSIZE] = {};
string user[MAXSIZE] = {};

int examCorrect[MAXSIZE] = {};
int examWrong[MAXSIZE] = {};
fstream cham;

void chamm(){
	cham:
	int enter;
	system("cls");
    loadingBar();                 
    SetConsoleTextAttribute(h, 7); 
    system("cls");
    SetConsoleTextAttribute(h, 2);
	cout << "" << setw(50) << "\e[0m\3  QUIJEE  \3 \n";
	cout<<"============================================================================\n";
	SetConsoleTextAttribute(h, 7); 
	cout<<"[1] Register. \n[2] Quiz. \n[3] View Record. \n[4] Delete. \n[5] Exit. \n\n";
	cout<<"============================================================================\n";
	cout<<"Pili na bagal [1-4]: ";
	cin >>enter;
	switch(enter){
		case 1: 
		system("CLS");
		registration();
		break;
		case 2:
			system("CLS");
			quiz();
			break;
		case 3:
			system("CLS");
			viewRecord();
			break;
			case 4:
				system("CLS");
				remove();
				break;
			case 5:
				
				exit();
				break;
        default:
            cout << "INVALID CHOICE INPUT\n\nPLEASE ENTER ANY KEY TO CONTINUE...";
            _getch();
            cin.clear();           // clear the previous input
            cin.ignore(12345, '\n'); // discard the previous input
            
            break;
        }
        
    } 

int main (){

	chamm();
} 
void registration(){
	bool reg=false;
	system("CLS");

	cham.open("jcham.txt", ios::out | ios::app);
	if(cham.is_open()){
    cout << "" << setw(50) << "REGISTRATION FORM\n";
    cout << "=================================================================================\n";
    cout << "Enter Firstname: ";
    cin>> fname;
    cham <<fname << endl;
    
    cout << "Enter Lastname: ";
    cin>> lname;
    cham <<lname << endl;
    
    cout << "Enter Username: ";
    cin>> username;
    cham <<username << endl;
    
    cout<<endl;
    
   for (int i = 0; i < MAXSIZE; i++)
    {
        if (firstname[i] == "\0")
        {
            firstname[i] = fname;
            lastname[i] = lname;
            user[i] = username;
            SetConsoleTextAttribute(h, 2);
            cout << "\n"
                 << setw(60) << "ACCOUNT SUCCESSFULLY REGISTERED\n";
            SetConsoleTextAttribute(h, 7);
            cout << "=================================================================================\n";
            cout << "\nPLEASE ENTER ANY KEY TO CONTINUE...";
            chamm();
            break; // to register one accout at a time
        }
    }
}
}
void quiz(){
	
    cin.ignore();
    cham.open("jcham.txt", ios::out | ios::app);
	if(cham.is_open()){
    int counter = 0;
    char fname[15], lname[15];
    char _choice;
    cout << "" << setw(45) << "LOGIN FORM\n";
    cout << "=================================================================================\n";
    cout << "Enter Firstname: ";
    cin.getline(fname, 15);
    cout << "Enter Lastname: ";
    cin.getline(lname, 15);
    for (int i = 0; i < MAXSIZE; i++)
    {
        if (firstname[i] == fname && lastname[i] == lname)
        {
            counter++;
            SetConsoleTextAttribute(h, 2);
            cout << "\n"
                 << setw(65) << "ACCESS GRANTED REDIRECTING TO QUIZ EXAMINATION\n";
            SetConsoleTextAttribute(h, 7);
            cout << "=================================================================================\n";

            cout << "\nPLEASE ENTER ANY KEY TO CONTINUE...";
            _getch();
            system("CLS");
            int score = 0;
            cout << "USERNAME: " << user[i]<< "\n\n";

            cout << "[1] What is the most popular programming langguage?\n\n";
            cout << "[A] PYTHON\n";
            cout << "[B] JAVASCRIPT\n";
            cout << "[C] JAVA\n";
            cout << "[D] C++\n\n";

            cout << "ENTER CHOICE: ";
            cin >> _choice;
            cham<< _choice;
            if (_choice == 'a' || _choice == 'A')
            {
                score++;
                examCorrect[i] = score;
            }
            else if (_choice == 'b' || _choice == 'B')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'c' || _choice == 'C')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'd' || _choice == 'D')
            {
                examWrong[i] = 0;
            }
            cout << "\n[2] C++ was developed by ___?\n\n";
            cout << "[A] Thomas Kushz\n";
            cout << "[B] John Kemney\n";
            cout << "[C] Bjarne Stroutstrup\n";
            cout << "[D] James Goling\n\n";

            cout << "ENTER CHOICE: ";
            cin >> _choice;
            cham<< _choice;
            if (_choice == 'a' || _choice == 'A')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'b' || _choice == 'B')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'c' || _choice == 'C')
            {
                score++;
                examCorrect[i] = score;
            }
            else if (_choice == 'd' || _choice == 'D')
            {
                examWrong[i] = 0;
            }
            cout << "\n[3] The modulus operator uses ___ character.?\n\n";
            cout << "[A] +\n";
            cout << "[B] *\n";
            cout << "[C] /\n";
            cout << "[D] %\n\n";

            cout << "ENTER CHOICE: ";
            cin >> _choice;
           cham<< _choice;
            if (_choice == 'a' || _choice == 'A')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'b' || _choice == 'B')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'c' || _choice == 'C')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'd' || _choice == 'D')
            {
                score++;
                examCorrect[i] = score;
            }
            cout << "\n[4] Every variable should be separated by ___ separator.?\n\n";
            cout << "[A] Dot\n";
            cout << "[B] Colon\n";
            cout << "[C] Comma\n";
            cout << "[D] Semicolon\n\n";

            cout << "ENTER CHOICE: ";
            cin >> _choice;
          cham<< _choice;
            if (_choice == 'a' || _choice == 'A')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'b' || _choice == 'B')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'c' || _choice == 'C')
            {
                score++;
                examCorrect[i] = score;
            }
            else if (_choice == 'd' || _choice == 'D')
            {
                examWrong[i] = 0;
            }
            cout << "\n[5] Variable names must begin with ___?\n\n";
            cout << "[A] #\n";
            cout << "[B] $\n";
            cout << "[C] Numbe\n";
            cout << "[D] Letter\n\n";

            cout << "ENTER CHOICE: ";
            cin >> _choice;
           cham<< _choice;
            if (_choice == 'a' || _choice == 'A')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'b' || _choice == 'B')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'c' || _choice == 'C')
            {
                examWrong[i] = 0;
            }
            else if (_choice == 'd' || _choice == 'D')
            {
                score++;
                examCorrect[i] = score;
            }
            SetConsoleTextAttribute(h, 6);
            cout << "\n"
                 << setw(60) << "ACCOUNT WILL AUTOMATICALLY LOG-OUT\n";
            SetConsoleTextAttribute(h, 7);
            cout << "=================================================================================\n";
            cout << "\nPLEASE ENTER ANY KEY TO CONTINUE...";
            _getch();
            chamm();
        }
    }

    // if no regiter account
    if (counter == 0)
    {
        SetConsoleTextAttribute(h, 4);
        cout << "\n"
             << setw(60) << "NO RECORD FIRSTNAME OR LASTNAME WAS FOUND\n";
        SetConsoleTextAttribute(h, 7);
        cout << "=================================================================================\n";
        cout << "\nPLEASE ENTER ANY KEY TO CONTINUE...";
        _getch();
        chamm();
        system("CLS");
    }
}
}
void viewRecord()
{
    int counter = 0;
    cout << "" << setw(45) << "VIEW RECORD\n";
    cout << "=================================================================================\n";
    cout << "NO." << setw(15) << "FIRStNAME" << setw(15) << "LASTNAME" << setw(15) << "USERNAME" << setw(15) << "SCORE" << setw(15) << "\n";
    for (int i = 0; i < MAXSIZE; i++)
    {
        if (firstname[i] != "\0")
        {
            counter++;
            cout << counter << setw(15) << firstname[i] << setw(15) << lastname[i] << setw(15) << user[i] << setw(15) << examCorrect[i] << setw(15);
            cout << "\n=================================================================================\n";
        }
    }

    if (counter == 0)
    {
        SetConsoleTextAttribute(h, 4);
        cout << "\n"
             << setw(45) << "NO RECORD FOUND";
        SetConsoleTextAttribute(h, 7);
        cout << "\n=================================================================================\n";
    }
    cout << "\nPLEASE ENTER ANY KEY TO BACK...";
    _getch();
    chamm();
}

void remove()
{
	
	cham.open(fname,ios::out | ios::trunc);
	cham.open(lname,ios::out | ios::trunc);
	cham.open(username,ios::out | ios::trunc);
	cham.close();
	 
}
void exit()
{   
   system("CLS");
    cout << "\n=================================================================================\n";
    cout << "|"
         << setw(80) << "|";
    cout << "\n|" << setw(52) << "THANK FOR USING THE APP ";
    SetConsoleTextAttribute(h, 4);
    cout << "\3" << setw(28) << "|\n";
    SetConsoleTextAttribute(h, 7);
    cout << "|"
         << setw(80) << "|";
    cout << "\n=================================================================================\n";
    _getch();
    exit(0);
}

void loadingBar()
{
  
    SetConsoleTextAttribute(h, 2);

    char a = 177,
         b = 219;

    cout << "\n\n\n\n";
    cout << "\n\n\n\n\t\t\t\tLoading...\n\n";
    cout << "\t\t\t\t";

    // Print initial loading bar
    for (int i = 0; i < 26; i++)
    {
        cout << a;
    }

    // Set the cursor again starting
    // point of loading bar
    cout << "\r";
    cout << "\t\t\t\t";

    // Print loading bar progress
    for (int i = 0; i < 26; i++)
    {
        cout << b;
        // Sleep for 1 second
        Sleep(30);
    }
}

