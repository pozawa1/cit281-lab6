# Objectives
1. Practice using JavaScript classes

# Technologies Used
- VSCode

# Part 1
Join GitHub and work through Introduction to GitHub course. 

# Part 2
Create a new file, lab-06.js, in the cit281/p5/lab-06 folder.

# Part 3
Create a digital book library using JavaScript classes.

![Screen Shot 2021-05-31 at 4 08 40 PM](https://user-images.githubusercontent.com/83732149/120248058-87f00080-c22a-11eb-8471-ef2dbc66ed69.png)

# Part 4
Create a Book class. 
```
class Book {
  constructor(title, author, pubDate) {
    this.title = title;
    this.author = author;
    this.pubDate = pubDate;
  }
}
```

# Part 5
Create a Library class.
```
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
    const { title = "", author = "", pubDate = "" } = book;
    if (title.length > 0 && author.length > 0) {
      const newBook = { title, author, pubDate };
      this._books.push(newBook);
    }
  }
  listBooks() {
    for (const book of this._books) {
      const {title, author, pubDate, isbn} = book;
      console.log(`Title: ${title}, Author: ${author}, PubDate: ${pubDate}`)
    }
  }
}
```

# Part 6
Update the code to add a least two more books to the library. 
```
const myBook = new Book("AP Calc Crash Course", "Banu el al.", "01/01/2013", "127465839");
const atomicHabits = new Book("Atomic Habits", "James Clear", "10/16/2018", "1234567890");
```

# Part 7
Make the following modifications to the classes:
- Add an ISBN property, isbn, to server as a unique identifier to the Book class (either ISBN-10 or ISBN-13, or both)
- Add a deleteBook(isbn) method to the Library class, to delete a Book from the Library using the ISBN

```
class Book {
    constructor(title, author, pubDate, isbn) {
      this.title = title;
      this.author = author;
      this.pubDate = pubDate;
      this.isbn = isbn;
    }
  }
```

```
  deleteBook(isbn) {
    let indexOfBookToRemove = null;
    
    for (let index = 0; index < this._books.length; index++) {
      const book = this._books[index];
      if (book.isbn == isbn) {
        indexOfBookToRemove = index;
        break;
    }
  }
    this._books.splice(indexOfBookToRemove, 1);
  }
```
