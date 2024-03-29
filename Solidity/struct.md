---
layout: home
title: Struct
parent: Solidity
---

## Struct

Struct types are used to represent a record. Suppose you want to keep track of your books in a library, you might want to track the following attributes about each book

    Title
    Author
    Subject
    Book ID

### Defining a Struct
* To define a Struct, you must use the struct keyword. <br>
* The struct keyword defines a new data type, with more than one member. <br>

The format of the struct statement is as follows
```c++
struct struct_name { 
   type1 type_name_1;
   type2 type_name_2;
   type3 type_name_3;
}
```
Example:
```c++
struct Book { 
   string title;
   string author;
   uint book_id;
}
```

### Accessing a Struct and its variable

* We use the member access operator (.)
* The member access operator is coded as a period between the structure variable name and the structure member that we wish to access. 
* You would use the struct to define variables of structure type. 

The following example shows how to use a structure in a program.

Example:-1
```c++
pragma solidity ^0.5.0;

contract test {
   struct Book { 
      string title;
      string author;
      uint book_id;
   }
   Book book;

   function setBook() public {
      book = Book('Learn Java', 'TP', 1);
   }
   function getBookId() public view returns (uint) {
      return book.book_id;
   }
}
```

Example:-2
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract LearnStruct {
    struct Movie {
        string director;
        string title;
        uint256 movie_id;
    }
    // struct acts as a new datatype  and we can assign it to variables like so
    Movie movie;
 
    function setMovie() public {
        // assignment is done like so
        movie = Movie("Blade runner", "Ridley scott", 1);
    }
 
    function getMovie() public view returns (Movie memory) {
        return movie;
    }
 
    function getMovieId() public view returns (uint256) {
        return movie.movie_id;
    }
}
```