# Read-File

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

string  s;

int patronss = 0;
int grandPatrons = 0;

while(inFile.good())
{
 inFile>>s;
 break;
} 
int Max =stoi(s) ; /*Enter name of data file: Donate.txt
terminating with uncaught exception of type std::invalid_argument: stoi: no conversion
/buildbot/src/android/ndk-release-r22/toolchain/llvm-project/libcxx/../../../toolchain/llvm-project/libcxxabi/src/abort_message.cpp:72: abort_message: assertion "terminating with uncaught exception of type std::invalid_argument: stoi: no conversion" failed
Aborted*/

patrons * Society = new patrons[Max];

for (int i = 0; i < Max; i++)
{
getline(inFile, Society[i].name); // getline to grab name
cout << Society[i].name;
(inFile >> Society[i].money).get();
/*inFile >> society[i].money;*/
cout << Society[i].money;
}
cout << "Grand Patrons: \n";
for(int x = 0; x < Max; x++)
{
if(Society[x].money >= 10000)
{
cout << Society[x].name << " Donated: "
<< "$ " << Society[x].money << "\n";
grandPatrons = 1;
}
}
if(grandPatrons == 0)
cout << "none\n";

 
cout << "Patrons list: \n";
for(int y = 0; y < Max; y++)
{
if(Society[y].money < 10000)
{
cout << Society[y].name << " Donated: "
<< "$ " << Society[y].money << "\n";
patronss = 1;
}
}
if(patronss == 0)
cout << "none\n";

delete [] Society;

if (inFile.eof())
cout << "End of file reached.\n";
else if (inFile.fail())
cout << "Input terminated by data mismatch.\n";
else
cout << "Input terminated for unknown reason.\n";
inFile.close(); // finished with the file
return 0;
}
