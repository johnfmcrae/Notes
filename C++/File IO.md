# File Input and Output

File I/O in C++ is dealt with using stream classes. For example, the classic `cin` and `cout` classes are of type `istream` and `ostream` respectively. For files, we need to `#include <fstream>` so that we can access **file streams**.

Always remember to `close()` your files to avoid data corruption and other nasty things.

File streams must always be passed by reference into functions since the function will be modifying the file by looking into it or writing to it.

## File Output

To send output to a file we can make use of an `ofstream`, for example,

```cpp
#include <iostream>
#include <fstream>
int main () {
    std::ofstream outFile; // can also init as outFile("output.txt");
    outFile.open("output.txt");
    outFile << "Hello World!\n";
    outFile.close();
}
```

## File Input

Similar to output, we can get input data using `ifstream`. It is important to check that the file opened correctly in the code as well.

```cpp
#include <iostream>
#include <fstream>
#include <string>

// this is a very useful function
void openInputFile(ifstream &inFile) {
    string filename;
    std::cout << "Enter filename: ";
    std::cin >> filename;
    inFile.open(filename);
    while (!inFile) {
        std::cout << "Failed to open\n";
        std::cout << "Enter filename: ";
        std::cin >> filename;
        inFile.clear();
        inFile.open(filename);
    }
}

int main () {
    std::ifstream inFile;
    openInputFile(inFile);
}
```

The `.clear()` function in our while loop is important to clear the flag in the input file stream which indicates whether or not the file exists.

To **append** to a file, you need to add an append open mode input parameter to the `open` function, for example,

```cpp
inFile.open(filename, std::ios::app);
```

## Reading Data

A common way to check the end of a file is to use the **end of file** (EOF) function to test if we are at the end of the file. Beware, however, that this function can be dangerous to use since it can't check if the file itself is behaving properly or if it actually exists. Better to check with the boolean returned by the file, as shown in the above example for file input.

A good way to read data is with the input operator, `>>`. The input operator will skip over whitespace and stop when it hits trailing whitespace or an invalid character. So, for example to read a file containing a list of integers and making use of our above `openInputFile` function, we could do the following,

```cpp
#include <iostream>
#include <fstream>
#include <string>
#include <vector>

void openInputFile(ifstream &inFile) {...} // see above

int main () {
    std::ifstream inFile;
    openInputFile(inFile);
    vector<int> v;
    int input;
    while (inFile >> input)
        v.push_back(input);
}
```

Another handy function is the `std::getline(input, str, delim)`, which will return one line at a time into the input string `str`. The delimiter `delim` is optional and by default is the new line character.

[Contents](_main_cpp_notes.md)
