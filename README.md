# Read-File
Still in trouble

#include <iostream>
#include <fstream> // file I/O support
#include <cstdlib> // support for exit()
#include <string>

struct patrons
{
	std::string name;
	double money;
};

int main()
{
using namespace std;
string filename;
ifstream inFile; // object for: handling file input

cout << "Enter name of data file: ";
getline(cin,filename);
inFile.open(filename); // associate inFile with a file
if (!inFile.is_open()) // failed to open file
{
cout << "Could not open the file " << filename << endl;
cout << "Program terminating.\n";
exit(EXIT_FAILURE);
}

int Max = 0;

while (inFile.good()) // if input good and not at EOF
{	
	  inFile >> ch; // get next char 
	  if (isdigit(ch))
	  {
	    Max = atoi(&ch);
	    break;
	  }
}
cout << Max;

if (inFile.eof())
cout << "End of file reached.\n";
else if (inFile.fail())
cout << "Input terminated by data mismatch.\n";
else
cout << "Input terminated for unknown reason.\n";
inFile.close(); // finished with the file
return 0;
}
