# Lab 6

## Objectives
1. Practice using JavaScript classes

## Technologies Used
- VSCode

## Source Code
```
class Book {
    constructor(title, author, pubDate, isbn) {
      this.title = title;
      this.author = author;
      this.pubDate = pubDate;
      this.isbn = isbn;
    }
  }

class Library {
  constructor(name) {
    this._name = name;
    this._books = [];
  }
  get books() {
    // Return copy of books
    return JSON.parse(JSON.stringify(this._books));
  }
  get count() {
    return this._books.length;
  }
  addBook(book = {}) {
    const { title = "", author = "", pubDate = "", isbn = "" } = book;
    if (title.length > 0 && author.length > 0) {
      const newBook = { title, author, pubDate, isbn };
      this._books.push(newBook);
    }
  }
  deleteBook(isbn) {
    // (1) Find the index of the book with the given isbn within the "_books" array
    let indexOfBookToRemove = null;
    
    for (let index = 0; index < this._books.length; index++) {
      const book = this._books[index];
      if (book.isbn == isbn) {
        indexOfBookToRemove = index;
        break;
    }
  }

    // (2) Once the index has been found, remove the entry from "_books"
    this._books.splice(indexOfBookToRemove, 1);
  }
  listBooks() {
    for (const book of this._books) {
      const {title, author, pubDate, isbn} = book;
      console.log(`Title: ${title}, Author: ${author}, PubDate: ${pubDate}, ISBN: ${isbn}`)
    }
  }
}

const myBook = new Book("AP Calc Crash Course", "Banu el al.", "01/01/2013", "127465839");
const atomicHabits = new Book("Atomic Habits", "James Clear", "10/16/2018", "1234567890");

let uoLibrary = new Library("Knight Library");
console.log("ADDING BOOKS");
uoLibrary.addBook(myBook);
uoLibrary.addBook(atomicHabits);
uoLibrary.listBooks();
console.log("DELETING BOOKS");
uoLibrary.deleteBook("1234567890");
uoLibrary.listBooks();
