Assume you oversee a small library and would like to develop a program that looks up books using their ISBNs. A list of books with their corresponding ISBN digits is in front of you. After the librarian inputs an ISBN, your software will look through the list to locate the relevant book.  The book's title and other details will be shown if the book is located. A notice stating that the book is not available in the library will appear if it cannot be located.
#include <iostream>
using namespace std;
struct Book {
    string title;
    string author;
    int year;
    string genre;
};
void searchBook(const map<string, Book>& library, const string& isbn) {
    auto it = library.find(isbn);
    if (it != library.end()) {
        cout << "Book Found!" << endl;
        cout << "Title: " << it->second.title << endl;
        cout << "Author: " << it->second.author << endl;
        cout << "Year: " << it->second.year << endl;
        cout << "Genre: " << it->second.genre << endl;
    } else {
        cout << "Book with ISBN " << isbn << " not found in the library." << endl;
    }
}

int main() {
       map<string, Book> library = {
        {"9780132350884", {"The C++ Programming Language", "Bjarne Stroustrup", 2008, "Programming"}},
        {"9780321714114", {"Effective Modern C++", "Scott Meyers", 2014, "Programming"}},
        {"9780596008673", {"C++ Primer", "Stanley B. Lippman", 2012, "Programming"}},
           };

    // Prompt the librarian to input an ISBN
    cout << "Enter the ISBN of the book you're looking for: ";
    string isbn;
    cin >> isbn;
        searchBook(library, isbn);

    return 0;
}

