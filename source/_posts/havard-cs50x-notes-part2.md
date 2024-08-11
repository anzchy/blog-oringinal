---
title: 哈佛 CS50x notes Lecture 6-10
date: 2024-08-10 09:31:32
categories:
- 编程
- 自学
tags:
- computer science
---



# Harvard CS50x Course Notes Lecture 6-10




# Lecture 6-Python



+   [Welcome!](#welcome)
+   [Python](#python)
+   [Hello](#hello)
+   [Speller](#speller)
+   [Filter](#filter)
+   [CS50 Library](#cs50-library)
+   [Strings](#strings)
+   [Variables](#variables)
+   [Types](#types)
+   [Calculator](#calculator)
+   [Conditionals](#conditionals)
+   [Object-Oriented Programming](#object-oriented-programming)
+   [Loops](#loops)
+   [Abstraction](#abstraction)
+   [Truncation and Floating Point Imprecision](#truncation-and-floating-point-imprecision)
+   [Exceptions](#exceptions)
+   [Mario](#mario)
+   [Lists](#lists)
+   [Searching and Dictionaries](#searching-and-dictionaries)
+   [Command-Line Arguments](#command-line-arguments)
+   [Exit Status](#exit-status)
+   [Third-Party Libraries](#third-party-libraries)
+   [Summing Up](#summing-up)

## Welcome!

+   In previous weeks, you were introduced to the fundamental building blocks of programming.
+   You learned about programming in a lower-level programming language called C.
+   Today, we are going to work with a higher-level programming language called *Python*.
+   As you learn this new language, you’re going to find that you are going to be more able to teach yourself new programming languages.

## Python

+   Humans, over the decades, have seen how previous design decisions could be improved upon.
+   Python is a programming language that builds upon what you have already learned in C.
+   Unlike in C, Python is an interpreted language, where you need not separately compile your program. Instead, you run your program in the *Python Interpreter*.

## Hello

+ Up until this point, the code has looked like this:

  ```auto
  // A program that says hello to the world
  
  #include <stdio.h>
  
  int main(void)
  {
      printf("hello, world\n");
  }
  ```

+ Today, you’ll find that the process of writing and compiling code has been simplified.

+ For example, the above code will be rendered in Python as:

  ```auto
  # A program that says hello to the world
  
  print("hello, world")
  ```

  Notice that the semicolon is gone and that no library is needed.

+ Python notably can implement what was quite complicated in C with relative simplicity.

## Speller

+ To illustrate this simplicity, let’s type ‘code dictionary.py’ in the terminal window and write code as follows:

  ```auto
  # Words in dictionary
  words = set()
  
  
  def check(word):
      """Return true if word is in dictionary else false"""
      return word.lower() in words
  
  
  def load(dictionary):
      """Load dictionary into memory, returning true if successful else false"""
      with open(dictionary) as file:
          words.update(file.read().splitlines())
      return True
  
  
  def size():
      """Returns number of words in dictionary if loaded else 0 if not yet loaded"""
      return len(words)
  
  
  def unload():
      """Unloads dictionary from memory, returning true if successful else false"""
      return True
  ```

  Notice that there are four functions above. In the `check` function, if a `word` is in `words`, it returns `True`. So much easier than an implementation in C! Similarly, in the `load` function the dictionary file is opened. For each line in that file, we add that line to `words`. Using `rstrip`, the trailing new line is removed from the added word. `size` simply returns the `len` or length of `words`. `unload` only needs to return `True` because Python handles memory management on its own.

+ The above code illustrates why higher-level languages exist: To simplify and allow you to write code more easily.

+ However, speed is a tradeoff. Because C allows you, the programmer, to make decisions about memory management, it may run faster than Python – depending on your code. While C only runs your lines of code, Python runs all the code that comes under the hood with it when you call Python’s built-in functions.

+ You can learn more about functions in the [Python documentation](https://docs.python.org/3/library/functions.html)

## Filter

+ To further illustrate this simplicity, create a new file by typing `code blur.py` in your terminal window and write code as follows:

  ```auto
  # Blurs an image
  
  from PIL import Image, ImageFilter
  
  # Blur image
  before = Image.open("bridge.bmp")
  after = before.filter(ImageFilter.BoxBlur(1))
  after.save("out.bmp")
  ```

  Notice that this program imports modules `Image` and `ImageFilter` from a library called `PIL`. This takes an input file and creates and output file.

+ Further, you can create a new file called `edges.py` as follows:

  ```auto
  # Finds edges in an image
  
  from PIL import Image, ImageFilter
  
  # Find edges
  before = Image.open("bridge.bmp")
  after = before.filter(ImageFilter.FIND_EDGES)
  after.save("out.bmp")
  ```

  Notice that this code is a small adjustment to your `blur` code, but produces a dramatically different result.

+ Finally, you can even do face detection as follows:

  ```auto
  # Find faces in picture
  # https://github.com/ageitgey/face_recognition/blob/master/examples/find_faces_in_picture.py
  
  from PIL import Image
  import face_recognition
  
  # Load the jpg file into a numpy array
  image = face_recognition.load_image_file("office.jpg")
  
  # Find all the faces in the image using the default HOG-based model.
  # This method is fairly accurate, but not as accurate as the CNN model and not GPU accelerated.
  # See also: find_faces_in_picture_cnn.py
  face_locations = face_recognition.face_locations(image)
  
  for face_location in face_locations:
  
      # Print the location of each face in this image
      top, right, bottom, left = face_location
  
      # You can access the actual face itself like this:
      face_image = image[top:bottom, left:right]
      pil_image = Image.fromarray(face_image)
      pil_image.show()
  ```

  Notice how this file uses a third-party library called face\_recognition. This is enabled by running `pip install face_recognition` in one’s terminal window.

+ Python allows you to abstract away programming that would be much more complicated within C and other *lower-level* programming languages.

## CS50 Library

+ As with C, the CS50 library can be utilized within Python.

+ The following functions will be of particular use:

  ```auto
    get_float
    get_int
    get_string
  ```

+ You also have the option of importing only specific functions from the CS50 library as follows:

  ```auto
  from CS50 import get_float, get_int, get_string
  ```

## Strings

+ In C, you might remember this code:

  ```auto
  // get_string and printf with %s
  
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string answer = get_string("What's your name? ");
      printf("hello, %s\n", answer);
  }
  ```

+ This code is transformed in Python to:

  ```auto
  # get_string and print, with concatenation
  
  from cs50 import get_string
  
  answer = get_string("What's your name? ")
  print("hello, " + answer)
  ```

  You can write this code by executing `code hello.py` in the terminal window. Then, you can execute this code by running `python hello.py`. Notice how the `+` sign concatenates `"hello, "` and `answer`.

+ Similarly, you could implement the above code as:

  ```auto
  # get_string and print, with format strings
  
  from cs50 import get_string
  
  answer = get_string("What's your name? ")
  print(f"hello, {answer}")
  ```

  Notice how the curly braces allow for the `print` function to interpolate the `answer` such that `answer` appears within. The `f` is required to include the `answer` properly formatting.

## Variables

+   Variable declaration is simplified too. In C, you might have `int counter = 0;`. In Python, this same line would read `counter = 0`. You need not declare the type of the variable.
+   Python favors `counter += 1` to increment by one, losing the ability found in C to type `counter++`.

## Types

+ Data types in Python do not need to be explicitly declared. For example, you saw how `answer` above is a string, but we did not have to tell the interpreter this was the case: It knew on its own.

+ In Python, commonly used types include:

  Notice that `long` and `double` are missing. Python will handle what data type should be used for larger and smaller numbers.

+ Some other data types in Python include:

  ```auto
    range
    list
    tuple
    dict
    set
  ```

+ Each of these data types can be implemented in C, but in Python they can be implemented more simply.

## Calculator

+ You might recall `calculator.c` from earlier in the course:

  ```auto
  // Addition with int
  
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Prompt user for x
      int x = get_int("x: ");
  
      // Prompt user for y
      int y = get_int("y: ");
  
      // Perform addition
      printf("%i\n", x + y);
  }
  ```

+ We can implement a simple calculator just as we did within C. Type `code calculator.py` into the terminal window and write code as follows:

  ```auto
  # Addition with int [using get_int]
  
  from cs50 import get_int
  
  # Prompt user for x
  x = get_int("x: ")
  
  # Prompt user for y
  y = get_int("y: ")
  
  # Perform addition
  print(x + y)
  ```

  Notice how the CS50 library is imported. Then, `x` and `y` are gathered from the user. Finally, the result is printed. Notice that the `main` function that would have been seen in a C program is gone entirely! While one could utilize a `main` function, it is not required.

+ It’s possible for one to remove the training wheels of the CS50 library. Modify your code as follows:

  ```auto
  # Addition with int [using input]
  
  # Prompt user for x
  x = input("x: ")
  
  # Prompt user for y
  y = input("y: ")
  
  # Perform addition
  print(x + y)
  ```

  Notice how executing the above code results in strange program behavior. Why might this be so?

+ You may have guessed that the interpreter understood `x` and `y` to be strings. You can fix your code by employing the `int` function as follows:

  ```auto
  # Addition with int [using input]
  
  # Prompt user for x
  x = int(input("x: "))
  
  # Prompt user for y
  y = int(input("y: "))
  
  # Perform addition
  print(x + y)
  ```

  Notice how the input for `x` and `y` is passed to the `int` function which converts it to an integer. Without converting `x` and `y` to be integers, the characters will concatenate.

## Conditionals

+ In C, you might remember a program like this:

  ```auto
  // Conditionals, Boolean expressions, relational operators
  
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Prompt user for integers
      int x = get_int("What's x? ");
      int y = get_int("What's y? ");
  
      // Compare integers
      if (x < y)
      {
          printf("x is less than y\n");
      }
      else if (x > y)
      {
          printf("x is greater than y\n");
      }
      else
      {
          printf("x is equal to y\n");
      }
  }
  ```

+ In Python, it would appear as follows:

  ```auto
  # Conditionals, Boolean expressions, relational operators
  
  from cs50 import get_int
  
  # Prompt user for integers
  x = get_int("What's x? ")
  y = get_int("What's y? ")
  
  # Compare integers
  if x < y:
      print("x is less than y")
  elif x > y:
      print("x is greater than y")
  else:
      print("x is equal to y")
  ```

  Notice that there are no more curly braces. Instead, indentations are utilized. Second, a colon is utilized in the `if` statement. Further, `elif` replaces `else if`. Parentheses are also no longer required in the `if` and `elif` statements.

+ In C, we faced challenges when we wanted to compare two values. Consider the following code:

  ```auto
  // Conditionals, Boolean expressions, relational operators
  
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Prompt user for integers
      int x = get_int("What's x? ");
      int y = get_int("What's y? ");
  
      // Compare integers
      if (x < y)
      {
          printf("x is less than y\n");
      }
      else if (x > y)
      {
          printf("x is greater than y\n");
      }
      else
      {
          printf("x is equal to y\n");
      }
  }
  ```

+ In Python, we can execute the above as follows:

  ```auto
  # Conditionals, Boolean expressions, relational operators
  
  from cs50 import get_int
  
  # Prompt user for integers
  x = get_int("What's x? ")
  y = get_int("What's y? ")
  
  # Compare integers
  if x < y:
      print("x is less than y")
  elif x > y:
      print("x is greater than y")
  else:
      print("x is equal to y")
  ```

  Notice that the CS50 library is imported. Further, minor changes exist in the `if` statement.

+ Further looking at comparisons, consider the following code in C:

  ```auto
  // Logical operators
  
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Prompt user to agree
      char c = get_char("Do you agree? ");
  
      // Check whether agreed
      if (c == 'Y' || c == 'y')
      {
          printf("Agreed.\n");
      }
      else if (c == 'N' || c == 'n')
      {
          printf("Not agreed.\n");
      }
  }
  ```

+ The above can be implemented as follows:

  ```auto
  # Logical operators
  
  from cs50 import get_string
  
  # Prompt user to agree
  s = get_string("Do you agree? ")
  
  # Check whether agreed
  if s == "Y" or s == "y":
      print("Agreed.")
  elif s == "N" or s == "n":
      print("Not agreed.")
  ```

  Notice that the two vertical bars utilized in C is replaced with `or`. Indeed, people often enjoy Python because it is more readable by humans. Also, notice that `char` does not exist in Python. Instead, `str`s are utilized.

+ Another approach to this same code could be as follows using *lists*:

  ```auto
  # Logical operators, using lists
  
  from cs50 import get_string
  
  # Prompt user to agree
  s = get_string("Do you agree? ")
  
  # Check whether agreed
  if s in ["y", "yes"]:
      print("Agreed.")
  elif s in ["n", "no"]:
      print("Not agreed.")
  ```

  Notice how we are able to express multiple keywords like `y` and `yes` in a `list`.

## Object-Oriented Programming

+ Up until this point, our programs in this course have been linear: sequential.

+ It’s possible to have certain types of values not only have properties or attributes inside of them but have functions as well. In Python, these values are known as *objects*

+ In C, we could create a `struct` where you could associate multiple variables inside a single self-created data type. In Python, we can do this and also include functions in a self-created data type. When a function belongs to a specific *object*, it is known as a *method*.

+ For example, `strs` in Python have a built-in *methods*. Therefore, you could modify your code as follows:

  ```auto
  # Logical operators, using lists
  
  from cs50 import get_string
  
  # Prompt user to agree
  s = get_string("Do you agree? ").lower()
  
  # Check whether agreed
  if s.lower() in ["y", "yes"]:
      print("Agreed.")
  elif s.lower() in ["n", "no"]:
      print("Not agreed.")
  ```

  Notice how the old value of `s` is overwritten with the result of `s.lower()`, a built-in method of `strs`.

+ In this class, we will only scratch the surface of Python. Therefore, the [Python documentation](https://docs.python.org/) will be of particular importance as you continue.

+ You can learn more about string methods in the [Python documentation](https://docs.python.org/3/library/stdtypes.html#string-methods)

## Loops

+ Loops in Python are very similar to C. You may recall the following code in C:

  ```auto
  // Demonstrates while loop
  
  #include <stdio.h>
  
  int main(void)
  {
      int i = 0;
      while (i < 3)
      {
          printf("meow\n");
          i++;
      }
  }
  ```

+ In Python, this code appears as:

  ```auto
  # Demonstrates while loop
  
  i = 0
  while i < 3:
      print("meow")
      i += 1
  ```

+ `for` loops can be implemented in Python as follows:

  ```auto
  # Better design
  
  for i in range(3):
      print("meow")
  ```

  Notice that `i` is never explicitly used. However, Python will increment the value of `i`.

+ Similarly, one could express the above code as:

  ```auto
  # Abstraction with parameterization
  
  def main():
      meow(3)
  
  
  # Meow some number of times
  def meow(n):
      for i in range(n):
          print("meow")
  
  
  main()
  ```

  Notice that a function is utilized to abstract away the meowing.

+ Finally, a `while` loop could be implemented as follows:

  ```auto
  # Demonstrates while loop
  
  i = 0
  while i < 3:
      print("meow")
      i += 1
  ```

+ To further our understanding of loops and iteration in Python, let’s create a new file called `uppercase.py` as follows:

  ```auto
  # Uppercases string one character at a time
  
  before = input("Before: ")
  print("After:  ", end="")
  for c in before:
      print(c.upper(), end="")
  print()
  ```

  Notice how `end=` is used to pass a parameter to the `print` function that continues the line without a line ending. This code passes one string at a time.

+ Reading the documentation, we discover that Python has methods that can be implemented upon the entire string as follows:

  ```auto
  # Uppercases string all at once
  
  before = input("Before: ")
  after = before.upper()
  print(f"After:  {after}")
  ```

  Notice how `.upper` is applied to the entire string.

## Abstraction

+ As we hinted at earlier today, you can further improve upon our code using functions and abstracting away various code into functions. Modify your earlier-created `meow.py` code as follows:

  ```auto
  # Abstraction
  
  def main():
      for i in range(3):
          meow()
  
  # Meow once
  def meow():
      print("meow")
  
  
  main()
  ```

  Notice that the `meow` function abstracts away the `print` statement. Further, notice that the `main` function appears at the top of the file. At the bottom of the file, the `main` function is called. By convention, it’s expected that you create a `main` function in Python.

+ Indeed, we can pass variables between our functions as follows:

  ```auto
  # Abstraction with parameterization
  
  def main():
      meow(3)
  
  
  # Meow some number of times
  def meow(n):
      for i in range(n):
          print("meow")
  
  
  main()
  ```

  Notice how `meow` now takes a variable `n`. In the `main` function, you can call `meow` and pass a value like `3` to it. Then, `meow` utilizes the value of `n` in the `for` loop.

+ Reading the above code, notice how you, as a C programmer, are able to quite easily make sense of the above code. While some conventions are different, the building blocks you previously learned are very apparent in this new programming language.

## Truncation and Floating Point Imprecision

+ Recall that in C, we experienced truncation where one integer being divided by another could result in an inprecise result.

+ You can see how Python handles such division as follows by modifying your code for `calculator.py`:

  ```auto
  # Division with integers, demonstration lack of truncation
  
  # Prompt user for x
  x = int(input("x: "))
  
  # Prompt user for y
  y = int(input("y: "))
  
  # Divide x by y
  z = x / y
  print(z)
  ```

  Notice that executing this code results in a value, but that if you were to see more digits after `.333333` you’d see that we are faced with *floating-point imprecision*. Truncation does not occur.

+ We can reveal this imprecision by modifying our codes slightly:

  ```auto
  # Floating-point imprecision
  
  # Prompt user for x
  x = int(input("x: "))
  
  # Prompt user for y
  y = int(input("y: "))
  
  # Divide x by y
  z = x / y
  print(f"{z:.50f}")
  ```

  Notice that this code reveals the imprecision. Python still faces this issue, just as C does.

## Exceptions

+ Let’s explore more about exceptions that can occur when we run Python code.

+ Modify `calculator.py` as follows:

  ```auto
  # Implements get_int
  
  def get_int(prompt):
      return int(input(prompt))
  
  
  def main():
  
      # Prompt user for x
      x = get_int("x: ")
  
      # Prompt user for y
      y = get_int("y: ")
  
      # Perform addition
      print(x + y)
  
  
  main()
  ```

  Notice that inputting the wrong data could result in an error.

+ We can `try` to handle and *catch* potential exceptions by modifying our code as follows:

  ```auto
  # Implements get_int with a loop
  
  def get_int(prompt):
      while True:
          try:
              return int(input(prompt))
          except ValueError:
              print("Not an integer")
  
  
  def main():
  
      # Prompt user for x
      x = get_int("x: ")
  
      # Prompt user for y
      y = get_int("y: ")
  
      # Perform addition
      print(x + y)
  
  
  main()
  ```

  Notice that the above code repeatedly tries to get the correct type of data, providing additional prompts when needed.

## Mario

+ Recall a few weeks ago our challenge of building three blocks on top of one another, like in Mario.

  ![three vertical blocks](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week6Slide073.png "mario blocks")

+ In Python, we can implement something akin to this as follows:

  ```auto
  # Prints a column of 3 bricks with a loop
  
  for i in range(3):
      print("#")
  ```

+ In C, we had the advantage of a `do-while` loop. However, in Python it is convention to utilize a `while` loop, as Python does not have a `do while` loop. You can write code as follows in a file called `mario.py`:

  ```auto
  # Prints a column of n bricks with a loop
  
  from cs50 import get_int
  
  while True:
      n = get_int("Height: ")
      if n > 0:
          break
  
  for i in range(n):
      print("#")
  ```

  Notice how the while loop is used to obtain the height. Once a height greater than zero is inputted, the loop breaks.

+ Consider the following image:

  ![four horizontal question blocks](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week6Slide075.png "mario blocks")

+ In Python, we could implement by modifying your code as follows:

  ```auto
  # Prints a row of 4 question marks with a loop
  
  for i in range(4):
      print("?", end="")
  print()
  ```

  Notice that you can override the behavior of the `print` function to stay on the same line as the previous print.

+ Similar in spirit to previous iterations, we can further simplify this program:

  ```auto
  # Prints a row of 4 question marks without a loop
  
  print("?" * 4)
  ```

  Notice that we can utilize `*` to multiply the print statement to repeat `4` times.

+ What about a large block of bricks?

  ![three by three block of mario blocks](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week6Slide078.png "mario blocks")

+ To implement the above, you can modify your code as follows:

  ```auto
  # Prints a 3-by-3 grid of bricks with loops
  
  for i in range(3):
      for j in range(3):
          print("#", end="")
      print()
  ```

  Notice how one `for` loop exists inside another. The `print` statement adds a new line at the end of each row of bricks.

+ You can learn more about the `print` function in the [Python documentation](https://docs.python.org/3/library/functions.html#print)

## Lists

+ `list`s are a data structure within Python.

+ `list`s have built in methods or functions within them.

+ For example, consider the following code:

  ```auto
  # Averages three numbers using a list
  
  # Scores
  scores = [72, 73, 33]
  
  # Print average
  average = sum(scores) / len(scores)
  print(f"Average: {average}")
  ```

  Notice that you can use the built-in `sum` method to calculate the average.

+ You can even utilize the following syntax to get values from the user:

  ```auto
  # Averages three numbers using a list and a loop
  
  from cs50 import get_int
  
  # Get scores
  scores = []
  for i in range(3):
      score = get_int("Score: ")
      scores.append(score)
  
  # Print average
  average = sum(scores) / len(scores)
  print(f"Average: {average}")
  ```

  Notice that this code utilizes the built-in `append` method for lists.

+ You can learn more about lists in the [Python documentation](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)

+ You can also learn more about `len` in the [Python documentation](https://docs.python.org/3/library/functions.html#len)

## Searching and Dictionaries

+ We can also search within a data structure.

+ Consider a program called `phonebook.py` as follows:

  ```auto
  # Implements linear search for names using loop
  
  # A list of names
  names = ["Carter", "David", "John"]
  
  # Ask for name
  name = input("Name: ")
  
  # Search for name
  for n in names:
      if name == n:
          print("Found")
          break
  else:
      print("Not found")
  ```

  Notice how this implements linear search for each name.

+ However, we don’t need to iterate through a list. In Python, we can execute linear search as follows:

  ```auto
  # Implements linear search for names using `in`
  
  # A list of names
  names = ["Carter", "David", "John"]
  
  # Ask for name
  name = input("Name: ")
  
  # Search for name
  if name in names:
      print("Found")
  else:
      print("Not found")
  ```

  Notice how `in` is used to implement linear search.

+ Still, this code could be improved.

+ Recall that a *dictionary* or `dict` is a collection of *key* and *value* pairs.

+ You can implement a dictionary in Python as follows:

  ```auto
  # Implements a phone book as a list of dictionaries, without a variable
  
  from cs50 import get_string
  
  people = [
      {"name": "Carter", "number": "+1-617-495-1000"},
      {"name": "David", "number": "+1-617-495-1000"},
      {"name": "John", "number": "+1-949-468-2750"},
  ]
  
  # Search for name
  name = get_string("Name: ")
  for person in people:
      if person["name"] == name:
          print(f"Found {person['number']}")
          break
  else:
      print("Not found")
  ```

  Notice that the dictionary is implemented having both `name` and `number` for each entry.

+ Even better, strictly speaking, we don’t need both a `name` and a `number`. We can simplify this code as follows:

  ```auto
  # Implements a phone book using a dictionary
  
  from cs50 import get_string
  
  people = {
      "Carter": "+1-617-495-1000",
      "David": "+1-617-495-1000",
      "John": "+1-949-468-2750",
  }
  
  # Search for name
  name = get_string("Name: ")
  if name in people:
      print(f"Number: {people[name]}")
  else:
      print("Not found")
  ```

  Notice that the dictionary is implemented using curly braces. Then, the statement `if name in people` searches to see if the `name` is in the `people` dictionary. Further, notice how, in the `print` statement, we can index into the people dictionary using the value of `name`. Very useful!

+ Python has done their best to get to *constant time* using their built-in searches.

+ You can learn more about dictionaries in the [Python documentation](https://docs.python.org/3/library/stdtypes.html#dict)

## Command-Line Arguments

+ As with C, you can also utilize command-line arguments. Consider the following code:

  ```auto
  # Prints a command-line argument
  
  from sys import argv
  
  if len(argv) == 2:
      print(f"hello, {argv[1]}")
  else:
      print("hello, world")
  ```

  Notice that `argv[1]` is printed using a *formatted string*, noted by the `f` present in the `print` statement.

+ You can print all the arguments in `argv` as follows:

  ```auto
  # Printing command-line arguments, indexing into argv
  
  from sys import argv
  
  for i in range(len(argv)):
      print(argv[i])
  ```

  Notice that the above will not present the word `python` if executed, and the first argument will be the name of the file you are running. You can think of the word `python` as being analogous to `./` when we were running programs in C.

+ You can slice pieces of lists away. Consider the following code:

  ```auto
  # Printing command-line arguments
  
  from sys import argv
  
  for arg in argv:
      print(arg)
  ```

  Notice that executing this code will result in the name of the file you are running being sliced away.

+ You can learn more about the `sys` library in the [Python documentation](https://docs.python.org/3/library/sys.html)

## Exit Status

+ The `sys` library also has built-in methods. We can use `sys.exit(i)` to exit the program with a specific exit code:

  ```auto
  # Exits with explicit value, importing sys
  
  import sys
  
  if len(sys.argv) != 2:
      print("Missing command-line argument")
      sys.exit(1)
  
  print(f"hello, {sys.argv[1]}")
  sys.exit(0)
  ```

  Notice that dot-notation is used to utilize the built-in functions of `sys`.

## Third-Party Libraries

+   One of the advantages of Python is its massive user-base and similarly large number of third-party libraries.
+   For example, David demoed the use of `cowsay` and `qrcode` libraries.

## Summing Up

In this lesson, you learned how the building blocks of programming from prior lessons can be implemented within Python. Further, you learned about how Python allowed for more simplified code. Also, you learned how to utilize various Python libraries. In the end, you learned that your skills as a programmer are not limited to a single programming language. Already, you are seeing how you are discovering a new way of learning through this course that could serve you in any programming language – and, perhaps, in nearly any avenue of learning! Specifically, we discussed…

+   Python
+   Variables
+   Conditionals
+   Loops
+   Types
+   Object-Oriented programming
+   Truncation and floating point imprecision
+   Exceptions
+   Dictionaries
+   Command-line arguments
+   Third-Party libraries

See you next time!



# lecture 6.5-Artificial Intelligence

## Artificial Intelligence

+   [Welcome!](#welcome)
+   [Image Generation](#image-generation)
+   [ChatGPT](#chatgpt)
+   [Prompt Generation](#prompt-generation)
+   [CS50.ai](#cs50ai)
+   [Generative AI](#generative-ai)
+   [Decision Trees](#decision-trees)
+   [Minimax](#minimax)
+   [Machine Learning](#machine-learning)
+   [Deep Learning](#deep-learning)
+   [Generative Artificial Intelligence](#generative-artificial-intelligence)
+   [Summing Up](#summing-up)

## Welcome!

+   In computer science and programming circles, *rubber ducking* or *rubber duck debugging* is the act of speaking to an inanimate object to be able to *talk through* a challenging problem.
+   Most recently, CS50 created our own rubber duck debugger at [cs50.ai](https://cs50.ai/), which uses artificial intelligence as a way by which to interact with students to help them with their own challenging problems.
+   Students engaging with this tool can begin understanding the potential of what AI can offer the world.

## Image Generation

+   Numerous AI tools have created the potential for artificially generated images to enter the world.
+   Up until recently, most of these tools had numerous tells that might indicate to an observer that an image is AI-generated.
+   However, tools are becoming exceedingly good at generating these images.
+   Indeed, as technology improves, it will soon be almost, if not entirely, impossible for such images to be detected with the naked eye.
+   Software has also gained the ability to mutate individual images within video.

## ChatGPT

+   A very well-known bleeding-edge tool is the text generation tool *chatGPT*.
+   In CS50, we do not allow the use of ChatGPT. However, we do allow the use of our own rubber duck debugger at [cs50.ai](https://cs50.ai/).
+   In CS50, we leverage the tools of Azure and OpenAI, along with our own vector database that holds very recent information from our most recent lectures and offerings, to provide our rubber duck debugger toll.

## Prompt Generation

+   *Prompt generation* is the way by which an individual can communicate with an AI platform.
+   We use a *system prompt* to teach the AI how to interact with users. We teach the AI how to work with students.
+   *User prompts* are those provided by users to interact with the AI. With these prompts, students interact with the AI.

## CS50.ai

+ Our [rubber duck debugger](https://cs50.ai/) can provide conceptual help with computer science concepts.

+ Further, the [rubber duck debugger](https://cs50.ai/) can help students write more efficient code.

+ Additionally, the [rubber duck debugger](https://cs50.ai/) can help when a student is stuck in one of their assignments. For example, students may encounter errors that prevent them from progressing in their assignments. When students hit a wall, they don’t have to wait for support staff to be available.

+ The [rubber duck debugger](https://cs50.ai/) does stipulate, however, that it is an AI and that it is experimental. Students should be conscious of the degree to which they blindly trust the AI. Consider the following image:

  ![rubber duck giving an answer with a disclaimer](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50AiLectureSlide060.png)

+ AI has an inhuman level of patience.

## Generative AI

+   AI has been with us for much time! Software has long adapted to users. Algorithms look for patterns in junk mail, images saved on your phone, and to play games.
+   In games, for example, step-by-step instructions may allow a computerized adversary play a game of Breakout.

## Decision Trees

+ *Decision trees* are used by an algorithm to decide what decision to make.

+ For example, in Breakout, an algorithm may consider what choice to make based on the instructions in the code:

  ```auto
  While game is ongoing:
  If ball is left of paddle:
    Move paddle left
  Else if ball is right of padding:
    Move paddle right
  Else:
    Don't move paddle
  ```

+ With most games, they attempt to minimize the number of calculations required to compete with the player.

## Minimax

+ You can imagine where an algorithm may score outcomes as positive, negative, and neutral.

+ In tic-tac-toe, the AI may consider a board where the computer wins as `1` and one where the computer loses as `-1`.

+ You can imagine how a computer may look at a decision tree of potential outcomes and assign scores to each potential move.

+ The computer will attempt to win by maximizing its own score.

+ In the context of tic-tac-toe, the algorithm may conceptualize this as follows:

  ```auto
  If player is X:
  For each possible move:
    Calculate score for board
  Choose move with highest score
  
  Else if player is O:
    For each possible move:
      Calculate score for board
    Choose move with lowest score
  ```

+ This could be pictured as follows:

  ![tictactoe with outcomes as 1 or -1 or 0](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50AiLectureSlide132.png)

+ Because computers are so powerful, they can crunch massive potential outcomes. However, the computers in our pockets or on our desks may not be able to calculate trillions of options. This is where machine learning can help.

## Machine Learning

+   Machine learning is a way by which a computer can learn through reinforcement.
+   A computer can learn how to flip a pancake.
+   A computer can learn how to play Mario.
+   A computer can learn how to play The Floor is Lava.
+   The computer repeats trial after trial after trial to discover what behaviors to repeat and those not to repeat.
+   Within much of AI-based algorithms, there are concepts of *explore vs. exploit*, where the AI may randomly try something that may not be considered optimal. Randomness can yield better outcomes.

## Deep Learning

+ *Deep learning* uses neural networks whereby problems and solutions are explored.

+ For example, deep learning may attempt to predict whether a blue or red dot will appear somewhere on a graph. Consider the following image:

  ![blue dots and red dots separated by a line](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50AiLectureSlide208.png)

+ Existing training data is used to predict an outcome. Further, more training data may be created by the AI to discover further patterns.

+ Deep learning creates nodes (pictured below), which associate inputs and outputs.

  ![Nodes connected to notes](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50AiLectureSlide210.png)

## Generative Artificial Intelligence

+   *Large language models* are massive models that make predictions based on huge amounts of training.
+   Just a few years ago, AI was not very good at completing and generating sentences.
+   The AI encodes words into *embeddings* to find relationships between words. Thus, through a huge amount of training, a massive neural network can predict the association between words - resulting in the ability for generative AI to generate content and even have conversations with users.
+   These technologies are what is behind our [rubber duck debugger](https://cs50.ai/).

## Summing Up

In this lesson, you learned about some of the technology behind our own [rubber duck debugger](https://cs50.ai/). Specifically, we discussed…

+   Image Generation
+   ChatGPT
+   Prompt Generation
+   CS50.ai
+   Generative AI
+   Decision Trees
+   Minimax
+   Machine Learning
+   Deep Learning
+   Generative Artificial Intelligence

This was CS50!




# Lecture 7-SQL

## 

+   [Welcome!](#welcome)
+   [Flat-File Database](#flat-file-database)
+   [Relational Databases](#relational-databases)
+   [Shows](#shows)
+   [`JOIN`s](#joins)
+   [Indexes](#indexes)
+   [Using SQL in Python](#using-sql-in-python)
+   [Race Conditions](#race-conditions)
+   [SQL Injection Attacks](#sql-injection-attacks)
+   [Summing Up](#summing-up)

## Welcome!

+   In previous weeks, we introduced you to Python, a high-level programming language that utilized the same building blocks we learned in C. However, we introduced this new language not for the purpose of learning “just another language.” Instead, we do so because some tools are better for some jobs and not so great for others!
+   This week, we will be continuing more syntax related to Python.
+   Further, we will be integrating this knowledge with data.
+   Finally, we will be discussing *SQL* or *Structured Query Language*.
+   Overall, one of the goals of this course is to learn to program generally – not simply how to program in the languages described in this course.

## Flat-File Database

+ As you have likely seen before, data can often be described in patterns of columns and rows.

+ Spreadsheets like those created in Microsoft Excel and Google Sheets can be outputted to a `csv` or *comma-separated values* file.

+ If you look at a `csv` file, you’ll notice that the file is flat in that all of our data is stored in a single table represented by a text file. We call this form of data a *flat-file database*.

+ Python comes with native support for `csv` files.

+ First, download [favorites.csv](https://cdn.cs50.net/2023/fall/lectures/7/src7/favorites/favorites.csv) and upload it to your file explorer inside [cs50.dev](https://cs50.dev/). Second, in your terminal window, type `code favorites.py` and write code as follows:

  ```auto
  # Prints all favorites in CSV using csv.reader
  
  import csv
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create reader
      reader = csv.reader(file)
  
      # Skip header row
      next(reader)
  
      # Iterate over CSV file, printing each favorite
      for row in reader:
          print(row[1])
  ```

  Notice that the `csv` library is imported. Further, we created a `reader` that will hold the result of `csv.reader(file)`. The `csv.reader` function reads each row from the file, and in our code we store the results in `reader`. `print(row[1])`, therefore, will print the language from the `favorites.csv` file.

+ You can improve your code as follows:

  ```auto
  # Stores favorite in a variable
  
  import csv
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create reader
      reader = csv.reader(file)
  
      # Skip header row
      next(reader)
  
      # Iterate over CSV file, printing each favorite
      for row in reader:
          favorite = row[1]
          print(favorite)
  ```

  Notice that `favorite` is stored and then printed. Also notice that we use the `next` function to skip to the next line of our reader.

+ One of the disadvantages of the above approach is that we are trusting that `row[1]` is always the favorite. However, what would happen if the columns have been moved around?

+ We can fix this potential issue. Python also allows you to index by the keys of a list. Modify your code as follows:

  ```auto
  # Prints all favorites in CSV using csv.DictReader
  
  import csv
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Iterate over CSV file, printing each favorite
      for row in reader:
          favorite = row["language"]
          print(favorite)
  ```

  Notice that this example directly utilizes the `language` key in the print statement.

+ This could be further simplified to:

  ```auto
  # Prints all favorites in CSV using csv.DictReader
  
  import csv
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Iterate over CSV file, printing each favorite
      for row in reader:
          print(row["language"])
  ```

+ To count the number of favorite languages expressed in the `csv` file, we can do the following:

  ```auto
  # Counts favorites using variables
  
  import csv
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Counts
      scratch, c, python = 0, 0, 0
  
      # Iterate over CSV file, counting favorites
      for row in reader:
          favorite = row["language"]
          if favorite == "Scratch":
              scratch += 1
          elif favorite == "C":
              c += 1
          elif favorite == "Python":
              python += 1
  
  # Print counts
  print(f"Scratch: {scratch}")
  print(f"C: {c}")
  print(f"Python: {python}")
  ```

  Notice that each language is counted using `if` statements. Further notice the double equal `==` signs in those `if` statements.

+ Python allows us to use a dictionary to count the `counts` of each language. Consider the following improvement upon our code:

  ```auto
  # Counts favorites using dictionary
  
  import csv
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Counts
      counts = {}
  
      # Iterate over CSV file, counting favorites
      for row in reader:
          favorite = row["language"]
          if favorite in counts:
              counts[favorite] += 1
          else:
              counts[favorite] = 1
  
  # Print counts
  for favorite in counts:
      print(f"{favorite}: {counts[favorite]}")
  ```

  Notice that the value in `counts` with the key `favorite` is incremented when it exists already. If it does not exist, we define `counts[favorite]` and set it to 1. Further, the formatted string has been improved to present the `counts[favorite]`.

+ Python also allows sorting `counts`. Improve your code as follows:

  ```auto
  # Sorts favorites by key
  
  import csv
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Counts
      counts = {}
  
      # Iterate over CSV file, counting favorites
      for row in reader:
          favorite = row["language"]
          if favorite in counts:
              counts[favorite] += 1
          else:
              counts[favorite] = 1
  
  # Print counts
  for favorite in sorted(counts):
      print(f"{favorite}: {counts[favorite]}")
  ```

  Notice the `sorted(counts)` at the bottom of the code.

+ If you look at the parameters for the `sorted` function in the Python documentation, you will find it has many built-in parameters. You can leverage some of these built-in parameters as follows:

  ```auto
  # Sorts favorites by value using .get
  
  import csv
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Counts
      counts = {}
  
      # Iterate over CSV file, counting favorites
      for row in reader:
          favorite = row["language"]
          if favorite in counts:
              counts[favorite] += 1
          else:
              counts[favorite] = 1
  
  # Print counts
  for favorite in sorted(counts, key=counts.get, reverse=True):
      print(f"{favorite}: {counts[favorite]}")
  ```

  Notice the arguments passed to `sorted`. The `key` argument allows you to tell Python the method you wish to use to sort items. In this case `counts.get` is used to sort by the values. `reverse=True` tells `sorted` to sort from largest to smallest.

+ Python has numerous libraries that we can utilize in our code. One of these libraries is `collections`, from which we can import `Counter`. `Counter` will allow you to access the counts of each language without the headaches of all the `if` statements seen in our previous code. You can implement as follows:

  ```auto
  # Sorts favorites by value using .get
  
  import csv
  
  from collections import Counter
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Counts
      counts = Counter()
  
      # Iterate over CSV file, counting favorites
      for row in reader:
          favorite = row["language"]
          counts[favorite] += 1
  
  # Print counts
  for favorite, count in counts.most_common():
      print(f"{favorite}: {count}")
  ```

  Notice how `counts = Counter()` enables the use of this imported `Counter` class from `collections`.

+ We can change the column we are examining, focusing on our favorite problem instead:

  ```auto
  # Favorite problem instead of favorite language
  
  import csv
  
  from collections import Counter
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Counts
      counts = Counter()
  
      # Iterate over CSV file, counting favorites
      for row in reader:
          favorite = row["problem"]
          counts[favorite] += 1
  
  # Print counts
  for favorite, count in counts.most_common():
      print(f"{favorite}: {count}")
  ```

  Notice that `problem` replaced `language`.

+ We can also get the count of the popularity of a specific problem in the course:

  ```auto
  # Gets a specific count
  
  import csv
  
  from collections import Counter
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Counts
      counts = Counter()
  
      # Iterate over CSV file, counting favorites
      for row in reader:
          favorite = row["problem"]
          counts[favorite] += 1
  
  # Print count
  favorite = input("Favorite: ")
  print(f"{favorite}: {counts[favorite]}")
  ```

  Notice how compact our code is compared to our experience in C.

## Relational Databases

+ Google, Twitter, and Meta all use relational databases to store their information at scale.

+ Relational databases store data in rows and columns in structures called *tables*.

+ SQL allows for four types of commands:

  ```auto
    Create
    Read
    Update
    Delete
  ```

+ These four operations are affectionately called *CRUD*.

+ We can create a SQL database at the terminal by typing `sqlite3 favorites.db`. Upon being prompted, we will agree that we want to create `favorites.db` by pressing `y`.

+ You will notice a different prompt as we are now inside a program called `sqlite3`.

+ We can put `sqlite3` into `csv` mode by typing `.mode csv`. Then, we can import our data from our `csv` file by typing `.import favorites.csv favorites`. It seems that nothing has happened!

+ We can type `.schema` to see the structure of the database.

+ You can read items from a table using the syntax `SELECT columns FROM table`.

+ For example, you can type `SELECT * FROM favorites;` which will iterate every row in `favorites`.

+ You can get a subset of the data using the command `SELECT language FROM favorites;`.

+ SQL supports many commands to access data, including:

  ```SQL
    AVG
    COUNT
    DISTINCT
    LOWER
    MAX
    MIN
    UPPER
  ```

+ For example, you can type `SELECT COUNT(language) FROM favorites;`. Further, you can type `SELECT DISTINCT(language) FROM favorites;` to get a list of the individual languages within the database. You could even type `SELECT COUNT(DISTINCT(language)) FROM favorites;` to get a count of those.

+ SQL offers additional commands we can utilize in our queries:

  ```auto
    WHERE       -- adding a Boolean expression to filter our data
    LIKE        -- filtering responses more loosely
    ORDER BY    -- ordering responses
    LIMIT       -- limiting the number of responses
    GROUP BY    -- grouping responses together
  ```

  Notice that we use `--` to write a comment in SQL.

+ For example, we can execute `SELECT COUNT(*) FROM favorites WHERE language = 'C';`. A count is presented.

+ Further, we could type `SELECT COUNT(*) FROM favorites WHERE language = 'C' AND problem = 'Hello, World;`. Notice how the `AND` is utilized to narrow our results.

+ Similarly, we could execute `SELECT language, COUNT(*) FROM favorites GROUP BY language;`. This would offer a temporary table that would show the language and count.

+ We could improve this by typing `SELECT language, COUNT(*) FROM favorites GROUP BY language ORDER BY COUNT(*);`. This will order the resulting table by the `count`.

+ We can also `INSERT` into a SQL database utilizing the form `INSERT INTO table (column...) VALUES(value, ...);`.

+ We can execute `INSERT INTO favorites (language, problem) VALUES ('SQL', 'Fiftyville');`.

+ `DELETE` allows you to delete parts of your data. For example, you could `DELETE FROM favorites WHERE Timestamp IS NULL;`.

+ We can also utilize the `UPDATE` command to update your data.

+ For example, you can execute `UPDATE favorites SET language = 'SQL', problem = 'Fiftyville';`. This will result in overwriting all previous statements where C was the favorite programming language.

+ Notice that these queries have immense power. Accordingly, in the real-world setting, you should consider who has permissions to execute certain commands.

## Shows

+ We can imagine a database that we might want to create to catalog various TV shows. We could create a spreadsheet with columns like `title`, `star`, `star`, `star`, `star`, and more stars. A problem with this approach is this approach has a lot of wasted space. Some shows may have one star. Others may have dozens.

+ We could separate our database into multiple sheets. We could have a `shows` sheet and a `people` sheet. On the `people` sheet, each person could have a unique `id`. On the `shows` sheet, each show could have a unique `id` too. On a third sheet called `stars` we could relate how each show has people for each show by having a `show_id` and `person_id`. While this is an improvement, this is not an ideal database.

+ IMDb offers a database of people, shows, writers, stars, genres, and ratings. Each of these tables is related to one another as follows:

  ![six boxes that represent various sql tables arrows are drawn to each showing their many relationships with one another](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week7Slide025.png "imdb relationships")

+ After downloading [`shows.db`](https://github.com/cs50/lectures/blob/2022/fall/7/src7/imdb/shows.db), you can execute `sqlite3 shows.db` in your terminal window.

+ Let’s zero in on the relationship between two tables within the database called `shows` and `ratings`. The relationship between these two tables can be illustrated as follows:

  ![two boxes one called shows and the other called ratings](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week7Slide032.png "imdb shows and ratings")

+ To illustrate the relationship between these tables, we could execute the following command: `SELECT * FROM ratings LIMIT 10;`. Examining the output, we could execute `SELECT * FROM shows LIMIT 10;`.

+ To understand the database, upon executing `.schema` you will find not only each of the tables but the individual fields inside each of these fields.

+ As you can see, `shows` has an `id` field. The `genres` table has a `show_id` field which has data that is common between it and the `shows` table.

+ Further, `show_id` exists in all of the tables. In the `shows` table, it is simply called `id`. This common field between all the fields is called a *key*. Primary keys are used to identify a unique record in a table. *Foreign keys* are used to build relationships between tables by pointing to the primary key in another table.

+ By storing data in a relational database, as above, data can be more efficiently stored.

+ In *sqlite*, we have five datatypes, including:

  ```auto
    BLOB       -- binary large objects that are groups of ones and zeros
    INTEGER    -- an integer
    NUMERIC    -- for numbers that are formatted specially like dates
    REAL       -- like a float
    TEXT       -- for strings and the like
  ```

+ Additionally, columns can be set to add special constraints:

+ We could execute `SELECT * FROM stars LIMIT 10;`. `show_id` is a foreign key in this final query because `show_id` corresponds to the unique `id` field in `shows`. `person_id` corresponds to the unique `id` field in the `people` column.

+ We can further play with this data to understand these relationships. Execute `SELECT * FROM ratings;`. There are a lot of ratings!

+ We can further limit this data down by executing `SELECT show_id FROM ratings WHERE rating >= 6.0 LIMIT 10;`. From this query, you can see that there are 10 shows presented. However, we don’t know what show each `show_id` represents.

+ You can discover what shows these are by executing `SELECT * FROM shows WHERE id = 626124;`

+ We can further our query to be more efficient by executing:

  ```auto
  SELECT title
  FROM shows
  WHERE id IN (
      SELECT show_id
      FROM ratings
      WHERE rating >= 6.0
      LIMIT 10
  )
  ```

  Notice that this query nests together two queries. An inner query is used by an outer query.

## `JOIN`s

+ We are pulling data from `shows` and `ratings`.

+ How could we combine tables temporarily? Tables could be joined together using the `JOIN` command.

+ Execute the following command:

  ```auto
  SELECT * FROM shows
    JOIN ratings on shows.id = ratings.show_id
    WHERE rating >= 6.0
    LIMIT 10;
  ```

  Notice this results in a wider table than we have previously seen.

+ Where the previous queries have illustrated the *one-to-one* relationship between these keys, let’s examine some *one-to-many* relationships. Focusing on the `genres` table, execute the following:

  ```auto
  SELECT * FROM genres
  LIMIT 10;
  ```

  Notice how this provides us a sense of the raw data. You might notice that one shows have three values. This is a one-to-many relationship.

+ We can learn more about the `genres` table by typing `.schema genres`.

+ Execute the following command to learn more about the various comedies in the database:

  ```auto
  SELECT title FROM shows
  WHERE id IN (
    SELECT show_id FROM genres
    WHERE genre = 'Comedy'
    LIMIT 10
  );
  ```

  Notice how this produces a list of comedies, including *Catweazle*.

+ To learn more about Catweazle, by joining various tables through a join:

  ```auto
  SELECT * FROM shows
  JOIN genres
  ON shows.id = genres.show_id
  WHERE id = 63881;
  ```

  Notice that this results in a temporary table. It is fine to have duplicate table.

+ A final relationship is a *many-to-many* relationship.

+ We can learn more about the show *The Office* by executing the following command:

  ```auto
  SELECT person_id FROM stars
  WHERE show_id = (
    SELECT id FROM shows
    WHERE title = 'The Office' AND year = 2005
  );
  ```

  Notice that this results in a table that includes the `person_id`s of various stars.

+ I could learn more about this group of actors by executing the following:

  ```auto
  SELECT name FROM people
  WHERE id IN (
      SELECT person_id FROM stars
      WHERE show_id = (
        SELECT id FROM shows
        WHERE title = 'The Office' AND year = 2005
      )
  );
  ```

  This results in a top-billed stars.

+ We can further understand this data by executing:

  ```auto
  SELECT title from shows
  WHERE id IN (
    SELECT show_id FROM stars
    WHERE person_id = (
      SELECT id FROM people
      WHERE name = 'Steve Carell'
    )
  );
  ```

  This results in a list of titles of shows wherein Steve Carell stared.

+ The wildcard `%` operator can be used to find all people whose names start with `Steve C` one could employ the syntax `SELECT * FROM people WHERE name LIKE 'Steve C%';`.

## Indexes

+ While relational databases have the ability to be more fast and more robust than utilizing a `CSV` file, data can be optimized within a table using *indexes*.

+ Indexes can be utilized to speed up our queries.

+ We can track the speed of our queries by executing `.timer on` in `sqlite3`.

+ To understand how indexes can speed up our queries, run the following: `SELECT * FROM shows WHERE title = 'The Office';` Notice the time that displays after the query executes.

+ Then, we can create an index with the syntax `CREATE INDEX title_index on shows (title);`. This tells `sqlite3` to create an index and perform some special under-the-hood optimization relating to this column `title`.

+ This will create a data structure called a *B Tree*, a data structure that looks similar to a binary tree. However, unlike a binary tree, there can be more than two child notes.

  ![one node at the top from which come four children and below that there are three children coming from one of the nodes and two from another two from another and three from another](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week7Slide039.png "b tree")

+ Running the query `SELECT * FROM shows WHERE title = 'The Office';`, you will notice that the query runs much more quickly!

+ Unfortunately, indexing all columns would result in utilizing more storage space. Therefore, there is a tradeoff for enhanced speed.

## Using SQL in Python

+ To assist in working with SQL in this course, the CS50 Library can be utilized as follows in your code:

+ Similar to previous uses of the CS50 Library, this library will assist with the complicated steps of utilizing SQL within your Python code.

+ You can read more about the CS50 Library’s SQL functionality in the [documentation](https://cs50.readthedocs.io/libraries/cs50/python/#cs50.SQL).

+ Recall where we last left off in `favorites.py`. Your code should appear as follows:

  ```auto
  # Gets a specific count
  
  import csv
  
  from collections import Counter
  
  # Open CSV file
  with open("favorites.csv", "r") as file:
  
      # Create DictReader
      reader = csv.DictReader(file)
  
      # Counts
      counts = Counter()
  
      # Iterate over CSV file, counting favorites
      for row in reader:
          favorite = row["problem"]
          counts[favorite] += 1
  
  # Print count
  favorite = input("Favorite: ")
  print(f"{favorite}: {counts[favorite]}")
  ```

  Notice how this code is exactly as we left it prior.

+ Modify your code as follows:

  ```auto
  # Searches database popularity of a problem
  
  import csv
  
  from cs50 import SQL
  
  # Open database
  db = SQL("sqlite:///favorites.db")
  
  # Prompt user for favorite
  favorite = input("Favorite: ")
  
  # Search for title
  rows = db.execute("SELECT COUNT(*) AS n FROM favorites WHERE problem LIKE ?", favorite)
  
  # Get first (and only) row
  row = rows[0]
  
  # Print popularity
  print(row["n"])
  ```

  Notice that `db = SQL("sqlite:///favorites.db")` provide Python the location of the database file. Then, the line that begins with `rows` executes SQL commands utilizing `db.execute`. Indeed, this command passes the syntax within the quotation marks to the `db.execute` function. We can issue any SQL command using this syntax. Further, notice that `rows` is returned as a list of dictionaries. In this case, there is only one result, one row, returned to the rows list as a dictionary.

## Race Conditions

+   Utilization of SQL can sometimes result in some problems.
+   You can imagine a case where multiple users could be accessing the same database and executing commands at the same time.
+   This could result in glitches where code is interrupted by other people’s actions. This could result in a loss of data.
+   Built-in SQL features such as `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK` help avoid some of these race condition problems.

## SQL Injection Attacks

+ Now, still considering the code above, you might be wondering what the `?` question marks do above. One of the problems that can arise in real-world applications of SQL is what is called an *injection attack*. An injection attack is where a malicious actor could input malicious SQL code.

+ For example, consider a login screen as follows:

  ![harvard key login screen with username and password fields](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week7Slide051-20240811153308167.png "harvard key login screen")

+ Without the proper protections in our own code, a bad actor could run malicious code. Consider the following:

  ```auto
  rows = db.execute("SELECT COUNT(*) FROM users WHERE username = ? AND password = ?", username, password)
  ```

  Notice that because the `?` is in place, validation can be run on `favorite` before it is blindly accepted by the query.

+ You never want to utilize formatted strings in queries as above or blindly trust the user’s input.

+ Utilizing the CS50 Library, the library will *sanitize* and remove any potentially malicious characters.

## Summing Up

In this lesson, you learned more syntax related to Python. Further, you learned how to integrate this knowledge with data in the form of flat-file and relational databases. Finally, you learned about *SQL*. Specifically, we discussed…

+   Flat-file databases
+   Relational databases
+   SQL
+   Primary and foreign keys
+   `JOIN`s
+   Indexes
+   Using SQL in Python
+   Race conditions
+   SQL injection attacks

See you next time!


# Lecture 8-Html&CSS

## 

+   [Welcome!](#welcome)
+   [Routers](#routers)
+   [DNS](#dns)
+   [HTTP](#http)
+   [HTML](#html)
+   [Regular Expressions](#regular-expressions)
+   [CSS](#css)
+   [Frameworks](#frameworks)
+   [JavaScript](#javascript)
+   [Summing Up](#summing-up)

## Welcome!

+   In previous weeks, we introduced you to Python, a high-level programming language that utilized the same building blocks we learned in C. Today, we will extend those building blocks further in HTML, CSS, and JavaScript.
+   The internet is a technology that we all use.
+   Using our skills from previous weeks, we can build our own web pages and applications.
+   The *ARPANET* connected the first points on the internet to one another.
+   Dots between two points could be considered *routers*.

## Routers

+ To route data from one place to another, we need to make *routing decisions*. That is, someone needs to program how data is transferred from point A to point B.

+ You can imagine how data could take multiple paths from point A and point B, such that when a router is congested, data can flow through another path. *Packets* of data are transferred from one router to another, from one computer to another.

+ *TCP/IP* are two protocols that allow computers to transfer data between them over the internet.

+ *IP* or *internet protocol* is a way by which computers can identify one another across the internet. Every computer has a unique address in the world. Addresses are in this form:

+ Numbers range from `0` to `255`. IP addresses are 32-bits, meaning that these addresses could accommodate over 4 billion addresses. Newer versions of IP addresse, implementing 128-bits, can accommodate far more computers!

+ In the real world, servers do a lot of work for us.

+ Packets are structured as follows:

  ![ascii art of a packet](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week8Slide014.png "packets")

+ Packets are standardized. The source and destination are held within each packet.

+ *TCP*, or transmission control protocol, is used to distinguish web services from one another. For example, `80` is used to denote HTTP and `443` is used to denote HTTPS. These numbers are *port numbers*.

+ When information is sent from one location to another, a source IP address, a destination IP address, and TCP port number are sent.

+ These protocols are also used to fragment large files into multiple parts or packets. For example, a large photo of a cat can be sent in multiple packets. When a packet is lost, TCP/IP can request missing packets again from the origin server.

+ TCP will acknowledge when all the data has been transmitted and received.

## DNS

+   It would be very tedious if you needed to remember an IP address to visit a website.
+   *DNS*, or *domain name systems*, is a collection of servers on the internet that are used to route website addresses like *harvard.edu* to a specific IP address.
+   DNS simply hold a table or database that links specific, fully qualified domain names to specific IP addresses.

## HTTP

+ *HTTP* or *hypertext transfer protocol* is an application-level protocol that developers use to build powerful and useful things through the transferring of data from one place to another.

+ When you see an address such as `https://www.example.com` you are actually implicitly visiting that address with a `/` at the end of it.

+ The *path* is what exists after that slash. For example, `https://www.example.com/folder/file.html` visits `example.com` and browses to the `folder` folder and then visits the file named `file.html`.

+ The `.com` is called a *top-level domain* that is used to denote the location or type of organization associated with this address.

+ `https` in this address is the protocol that is used to connect to that web address. By protocol, we mean that HTTP utilizes `GET` or `POST` *requests* to ask for information from a server. For example, you can launch Google Chrome, right-click, and click `inspect`. When you open the `developer tools` and visit `Network`, selecting `Preserve log`, you will see `Request Headers`. You’ll see mentions of `GET`. This is possible in other browsers as well, using slightly different methods.

+ For example, when issuing a GET request, your computer may send the following to a server:

  ```auto
    GET / HTTP/2
    Host: www.harvard.edu
  ```

  Notice that this requests via HTTP the content served on www.harvard.edu

+ Generally, after making a request a server, you will receive the following in `Response Headers`:

  ```auto
    HTTP/2 200
    Content-Type: text/html
  ```

+ This approach to inspecting these logs may be a bit more complicated than need be. You can analyze the work of HTTP protocols at [cs50.dev](https://cs50.dev/). For example, type the following in your terminal window:

  ```auto
    curl -I https://www.harvard.edu/
  ```

  Notice that the output of this command returns all the header values of the responses of the server.

+ Via developer tools in your web browser, you can see all the HTTP requests when browsing to the above website.

+ Further, execute the following command in your terminal window:

  ```auto
    curl -I https://harvard.edu
  ```

  Notice that you will see a `301` response, providing a hint to a browser of where it can find the correct website.

+ Similarly, execute the following in your terminal window:

  ```auto
    curl -I http://www.harvard.edu/
  ```

  Notice that the `s` in `https` has been removed. The server response will show that the response is `301`, meaning that the website has permanently moved.

+ Similar to `301`, a code of `404` means that a specified URL has not been found. There are numerous other response codes, such as:

  ```auto
    200 OK
    301 Moved Permanently
    302 Found
    304 Not Modified
    304 Temporary Redirect
    401 Unauthorized
    403 Forbidden
    404 Not Found
    418 I'm a Teapot
    500 Internal Server Error
    503 Service Unavailable
  ```

+ It’s worth mentioning that `500` errors are always your fault as the developer. This will be especially important for next week’s problem set, and potentially for your final project!

## HTML

+ *HTML* or *hypertext markup language* is made up of *tags*, each of which may have some *attributes* that describe it.

+ In your terminal, type `code hello.html` and write code as follows:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates HTML -->
  
  <html lang="en">
      <head>
          <title>hello, title</title>
      </head>
      <body>
          hello, body
      </body>
  </html>
  ```

  Notice that the `html` tag both opens and closes this file. Further, notice the `lang` attribute, which modifies the behavior of the `html` tag. Also, notice that there are both `head` tags and `body` tags. Indentation is not required but does suggest a hierarchy.

+ You can serve your code by typing `http-server`. This serve is now available on a very long URL. If you click it, you can visit the website with your own code.

+ When you visit this URL, notice that the file name `hello.html` appears at the end of this URL. Further, notice, based upon the URL, that the server is serving via port 8080.

+ The hierarchy of tags can be represented as follows:

  ![html code next to a hierarchy showing parent and child nodes](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week8Slide065.png "DOM")

+ Knowledge of this hierarchy will be useful later as we learn JavaScript.

+ The browser will read your HTML file top to bottom and left to right.

+ Because whitespace and indentation is effectively ignored in HTML, you will need to use `<p>` paragraph tags to open and close a paragraph. Consider the following:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates paragraphs -->
  
  <html lang="en">
      <head>
          <title>paragraphs</title>
      </head>
      <body>
          <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
          </p>
          <p>
              Mauris ut dui in eros semper hendrerit. Morbi vel elit mi. Sed sit amet ex non quam dignissim dignissim et vel arcu. Pellentesque eget elementum orci. Morbi ac cursus ex. Pellentesque quis turpis blandit orci dapibus semper sed non nunc. Nulla et dolor nec lacus finibus volutpat. Sed non lorem diam. Donec feugiat interdum interdum. Vivamus et justo in enim blandit fermentum vel at elit. Phasellus eu ante vitae ligula varius aliquet. Etiam id posuere nibh.
          </p>
          <p>
              Aenean venenatis convallis ante a rhoncus. Nullam in metus vel diam vehicula tincidunt. Donec lacinia metus sem, sit amet egestas elit blandit sit amet. Nunc egestas sem quis nisl mattis semper. Pellentesque ut magna congue lorem eleifend sodales. Donec tortor tortor, aliquam vitae mollis sed, interdum ut lectus. Mauris non purus quis ipsum lacinia tincidunt.
          </p>
          <p>
              Integer at justo lacinia libero blandit aliquam ut ut dui. Quisque tincidunt facilisis venenatis. Nullam dictum odio quis lorem luctus, vel malesuada dolor luctus. Aenean placerat faucibus enim a facilisis. Maecenas eleifend quis massa sed eleifend. Ut ultricies, dui ac vulputate hendrerit, ex metus iaculis diam, vitae fermentum libero dui et ante. Phasellus suscipit, arcu ut consequat sagittis, massa urna accumsan massa, eu aliquet nulla lorem vitae arcu. Pellentesque rutrum felis et metus porta semper. Nam ac consectetur mauris.
          </p>
          <p>
              Suspendisse rutrum vestibulum odio, sed venenatis purus condimentum sed. Morbi ornare tincidunt augue eu auctor. Vivamus sagittis ac lectus at aliquet. Nulla urna mauris, interdum non nibh in, vehicula porta enim. Donec et posuere sapien. Pellentesque ultrices scelerisque ipsum, vel fermentum nibh tincidunt et. Proin gravida porta ipsum nec scelerisque. Vestibulum fringilla erat at turpis laoreet, nec hendrerit nisi scelerisque.
          </p>
          <p>
              Sed quis malesuada mi. Nam id purus quis augue sagittis pharetra. Nulla facilisi. Maecenas vel fringilla ante. Cras tristique, arcu sit amet blandit auctor, urna elit ultricies lacus, a malesuada eros dui id massa. Aliquam sem odio, pretium vel cursus eget, scelerisque at urna. Vestibulum posuere a turpis consectetur consectetur. Cras consequat, risus quis tempor egestas, nulla ipsum ornare erat, nec accumsan nibh lorem nec risus. Integer at iaculis lacus. Integer congue nunc massa, quis molestie felis pellentesque vestibulum. Nulla odio tortor, aliquam nec quam in, ornare aliquet sapien.
          </p>
      </body>
  </html>
  ```

  Notice that paragraphs start with a `<p>` tag and end with a `</p>` tag.

+ HTML allows for the representation of headings:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates headings (for chapters, sections, subsections, etc.) -->
  
  <html lang="en">
  
      <head>
          <title>headings</title>
      </head>
  
      <body>
  
          <h1>One</h1>
          <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
          </p>
  
          <h2>Two</h2>
          <p>
              Mauris ut dui in eros semper hendrerit. Morbi vel elit mi. Sed sit amet ex non quam dignissim dignissim et vel arcu. Pellentesque eget elementum orci. Morbi ac cursus ex. Pellentesque quis turpis blandit orci dapibus semper sed non nunc. Nulla et dolor nec lacus finibus volutpat. Sed non lorem diam. Donec feugiat interdum interdum. Vivamus et justo in enim blandit fermentum vel at elit. Phasellus eu ante vitae ligula varius aliquet. Etiam id posuere nibh.
          </p>
  
          <h3>Three</h3>
          <p>
              Aenean venenatis convallis ante a rhoncus. Nullam in metus vel diam vehicula tincidunt. Donec lacinia metus sem, sit amet egestas elit blandit sit amet. Nunc egestas sem quis nisl mattis semper. Pellentesque ut magna congue lorem eleifend sodales. Donec tortor tortor, aliquam vitae mollis sed, interdum ut lectus. Mauris non purus quis ipsum lacinia tincidunt.
          </p>
  
          <h4>Four</h4>
          <p>
              Integer at justo lacinia libero blandit aliquam ut ut dui. Quisque tincidunt facilisis venenatis. Nullam dictum odio quis lorem luctus, vel malesuada dolor luctus. Aenean placerat faucibus enim a facilisis. Maecenas eleifend quis massa sed eleifend. Ut ultricies, dui ac vulputate hendrerit, ex metus iaculis diam, vitae fermentum libero dui et ante. Phasellus suscipit, arcu ut consequat sagittis, massa urna accumsan massa, eu aliquet nulla lorem vitae arcu. Pellentesque rutrum felis et metus porta semper. Nam ac consectetur mauris.
          </p>
  
          <h5>Five</h5>
          <p>
              Suspendisse rutrum vestibulum odio, sed venenatis purus condimentum sed. Morbi ornare tincidunt augue eu auctor. Vivamus sagittis ac lectus at aliquet. Nulla urna mauris, interdum non nibh in, vehicula porta enim. Donec et posuere sapien. Pellentesque ultrices scelerisque ipsum, vel fermentum nibh tincidunt et. Proin gravida porta ipsum nec scelerisque. Vestibulum fringilla erat at turpis laoreet, nec hendrerit nisi scelerisque.
          </p>
  
          <h6>Six</h6>
          <p>
              Sed quis malesuada mi. Nam id purus quis augue sagittis pharetra. Nulla facilisi. Maecenas vel fringilla ante. Cras tristique, arcu sit amet blandit auctor, urna elit ultricies lacus, a malesuada eros dui id massa. Aliquam sem odio, pretium vel cursus eget, scelerisque at urna. Vestibulum posuere a turpis consectetur consectetur. Cras consequat, risus quis tempor egestas, nulla ipsum ornare erat, nec accumsan nibh lorem nec risus. Integer at iaculis lacus. Integer congue nunc massa, quis molestie felis pellentesque vestibulum. Nulla odio tortor, aliquam nec quam in, ornare aliquet sapien.
          </p>
  
      </body>
  
  </html>
  ```

  Notice that `<h1>`, `<h2>`, and `<h3>` denote different levels of headings.

+ We can also create unordered lists within HTML:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates (ordered) lists -->
  
  <html lang="en">
      <head>
          <title>list</title>
      </head>
      <body>
          <ul>
              <li>foo</li>
              <li>bar</li>
              <li>baz</li>
          </ul>
      </body>
  </html>
  ```

  Notice that the `<ul>` tag creates an unordered list containing three items.

+ We can also create ordered lists within HTML:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates (ordered) lists -->
  
  <html lang="en">
      <head>
          <title>list</title>
      </head>
      <body>
          <ol>
              <li>foo</li>
              <li>bar</li>
              <li>baz</li>
          </ol>
      </body>
  </html>
  ```

  Notice that the `<ol>` tag creates an ordered list containing three items.

+ We can also create a table in HTML:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates table -->
  
  <html lang="en">
      <head>
          <title>table</title>
      </head>
      <body>
          <table>
              <tr>
                  <td>1</td>
                  <td>2</td>
                  <td>3</td>
              </tr>
              <tr>
                  <td>4</td>
                  <td>5</td>
                  <td>6</td>
              </tr>
              <tr>
                  <td>7</td>
                  <td>8</td>
                  <td>9</td>
              </tr>
              <tr>
                  <td>*</td>
                  <td>0</td>
                  <td>#</td>
              </tr>
          </table>
      </body>
  </html>
  ```

  Tables also have tags that open and close each element within. Also, notice the syntax for comments in HTML.

+ Images can also be utilized within HTML:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates image -->
  
  <html lang="en">
      <head>
          <title>image</title>
      </head>
      <body>
          <img alt="photo of bridge" src="bridge.png">
      </body>
  </html>
  ```

  Notice that `src="bridge.png"` indicates the path where the image file can be located.

+ Videos can also be included in HTML:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates video -->
  
  <html lang="en">
      <head>
          <title>video</title>
      </head>
      <body>
          <video controls muted>
              <source src="video.mp4" type="video/mp4">
          </video>
      </body>
  </html>
  ```

  Notice that the `type` attribute designates that this is a video of type `mp4`. Further, notice how `controls` and `muted` are passed to `video`.

+ You can also link between various web pages:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates link -->
  
  <html lang="en">
      <head>
          <title>link</title>
      </head>
      <body>
         Visit <a href="https://www.harvard.edu">Harvard</a>.
      </body>
  </html>
  ```

  Notice that the `<a>` or *anchor* tag is used to make `Harvard` a linkable text.

+ Meta tags are used to hold information about the data within the HTML file. Consider the following:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates responsive design -->
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>meta</title>
      </head>
      <body>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
      </body>
  </html>
  ```

  Notice this set of `meta` attributes makes this page mobile-friendly.

+ There are numerous `meta` key-value pairs that you can use:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates Open Graph tags -->
  
  <html lang="en">
      <head>
          <meta property="og:title" content="CS50">
          <meta property="og:description" content="Introduction to the intellectual enterprises of computer science and the art of programming.">
          <meta property="og:image" content="cat.jpg">
          <title>meta</title>
      </head>
      <body>
          ...
      </body>
  </html>
  ```

  Notice that these key value pairs relate to the `title` and `description` of the web page.

+ You can also create forms reminiscent of Google’s search:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates form -->
  
  <html lang="en">
      <head>
          <title>search</title>
      </head>
      <body>
          <form action="https://www.google.com/search" method="get">
              <input name="q" type="search">
              <input type="submit" value="Google Search">
          </form>
      </body>
  </html>
  ```

  Notice that a `form` tag opens and provides the attribute of what `action` it will take. The `input` field is included, passing the name `q` and the type as `search`.

+ We can make this search better as follows:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates additional form attributes -->
  
  <html lang="en">
      <head>
          <title>search</title>
      </head>
      <body>
          <form action="https://www.google.com/search" method="get">
              <input autocomplete="off" autofocus name="q" placeholder="Query" type="search">
              <button>Google Search</button>
          </form>
      </body>
  </html>
  ```

  Notice that `autocomplete` is turned `off`. `autofocus` is enabled.

+ We’ve seen just a few of many HTML elements you can add to your site. If you have an idea for something to add to your site that we haven’t seen yet (a button, an audio file, etc.) try Googling “X in HTML” to find the right syntax! Similarly, you can use [cs50.ai](https://cs50.ai/) to help you discover more HTML features!

## Regular Expressions

+ *Regular expressions* or *regexes* are a means by which to ensure that user-provided data fits a specific format.

+ We can impelement our own registration page that utilizes regexes as follows:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates type="email" -->
  
  <html lang="en">
      <head>
          <title>register</title>
      </head>
      <body>
          <form>
              <input autocomplete="off" autofocus name="email" placeholder="Email" type="email">
              <button>Register</button>
          </form>
      </body>
  </html>
  ```

  Notice that the `input` tag includes attributes that designate that this is of type `email`. The browser knows to double-check that input is an email address.

+ While the browser uses these built-in attributes to check for an email address, we can add a `pattern` attribute to ensure that only specific data ends up in the email address:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates pattern attribute -->
  
  <html lang="en">
      <head>
          <title>register</title>
      </head>
      <body>
          <form>
              <input autocomplete="off" autofocus name="email" pattern=".+@.+\.edu" placeholder="Email" type="email">
              <button>Register</button>
          </form>
      </body>
  </html>
  ```

  Notice that the `pattern` attribute is handed a regular expression to denote that the email address must include an `@` symbol and a `.edu`.

+ You can learn more about regular expressions from [Mozilla’s documentation](https://cs50.harvard.edu/x/2024/notes/8/developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions). Further, you can make inquiries to [cs50.ai](https://cs50.ai/) for hints.

## CSS

+ `CSS`, or *cascading style sheet*, is a markup language that allows you to fine-tune the aesthetics of your HTML files.

+ CSS is filled with *properties*, which include key-value pairs.

+ In your terminal, type `code home.html` and write code as follows:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates inline CSS with P tags -->
  
  <html lang="en">
      <head>
          <title>css</title>
      </head>
      <body>
          <p style="font-size: large; text-align: center;">
              John Harvard
          </p>
          <p style="font-size: medium; text-align: center;">
              Welcome to my home page!
          </p>
          <p style="font-size: small; text-align: center;">
              Copyright &#169; John Harvard
          </p>
      </body>
  </html>
  ```

  Notice that some `style` attributes are provided to the `<p>` tags. The `font-size` is set to `large`, `medium`, or `small`. Then `text-align` is set to center.

+ While correct, the above is not well-designed. We can remove redundancy by modifying our code as follows:

  ```auto
  <!DOCTYPE html>
  
  <!-- Removes outer DIV -->
  
  <html lang="en">
      <head>
          <title>css</title>
      </head>
      <body style="text-align: center">
          <div style="font-size: large">
              John Harvard
          </div>
          <div style="font-size: medium">
              Welcome to my home page!
          </div>
          <div style="font-size: small">
              Copyright &#169; John Harvard
          </div>
      </body>
  </html>
  ```

  Notice that `<div>` tags are used to divide up this HTML file into specific regions. `text-align: center` is invoked on the entire body of the HTML. Because everything inside `body` is a child of `body`, the `center` attribute cascades down to those children.

+ It turns out that there are newer semantic tags that are included in HTML. We can modify our code as follows:

  ```auto
  <!DOCTYPE html>
  
  <!-- Uses semantic tags instead of DIVs -->
  
  <html lang="en">
      <head>
          <title>css</title>
      </head>
      <body style="text-align: center">
          <header style="font-size: large">
              John Harvard
          </header>
          <main style="font-size: medium">
              Welcome to my home page!
          </main>
          <footer style="font-size: small">
              Copyright &#169; John Harvard
          </footer>
      </body>
  </html>
  ```

  Notice that the `header` and `footer` both have different styles assigned to them.

+ This practice of placing the style and information all in the same location is not good practice. We could move the elements of style to the top of the file as follows:

  ```auto
  <!-- Demonstrates class selectors -->
  
  <html lang="en">
      <head>
          <style>
  
              .centered
              {
                  text-align: center;
              }
  
              .large
              {
                  font-size: large;
              }
  
              .medium
              {
                  font-size: medium;
              }
  
              .small
              {
                  font-size: small;
              }
  
          </style>
          <title>css</title>
      </head>
      <body class="centered">
          <header class="large">
              John Harvard
          </header>
          <main class="medium">
              Welcome to my home page!
          </main>
          <footer class="small">
              Copyright &#169; John Harvard
          </footer>
      </body>
  </html>
  ```

  Notice all the style tags are placed up in the `head` in the `style` tag wrapper. Also notice that we’ve assigned *classes*, called `centered`, `large`, `medium`, and `small` to our elements, and that we select those classes by placing a dot before the name, as in `.centered`

+ It turns out that we can move all our style code into a special file called a *CSS* file. We can create a file called `style.css` and paste our classes there:

  ```auto
  .centered
  {
      text-align: center;
  }
  
  .large
  {
      font-size: large;
  }
  
  .medium
  {
      font-size: medium;
  }
  
  .small
  {
      font-size: small;
  }
  ```

  Notice that this is verbatim what appeared in our HTML file.

+ We then can tell the browser where to locate the CSS for this HTML file:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates external stylesheets -->
  
  <html lang="en">
      <head>
          <link href="style.css" rel="stylesheet">
          <title>css</title>
      </head>
      <body class="centered">
          <header class="large">
              John Harvard
          </header>
          <main class="medium">
              Welcome to my home page!
          </main>
          <footer class="small">
              Copyright &#169; John Harvard
          </footer>
      </body>
  </html>
  ```

  Notice that `style.css` is linked to this HTML file as a stylesheet, telling the browser where to locate the styles we created.

## Frameworks

+ Similar to third-party libraries we can leverage in Python, there are third-party libraries called *frameworks* that we can utilize with our HTML files.

+ *Bootstrap* is one of these frameworks that we can use to beautify our HTML and easily perfect design elements such that our pages are more readable.

+ Bootstrap can be utilized by adding the following `link` tag in the `head` of your html file:

  ```auto
  <head>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
      <title>favorites</title>
  </head>
  ```

+ Consider the following HTML:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates table -->
  
  <html lang="en">
      <head>
          <title>phonebook</title>
      </head>
      <body>
          <table>
              <thead>
                  <tr>
                      <th>Name</th>
                      <th>Number</th>
                  </tr>
              </thead>
              <tbody>
                  <tr>
                      <td>Carter</td>
                      <td>+1-617-495-1000</td>
                  </tr>
                  <tr>
                      <td>David</td>
                      <td>+1-617-495-1000</td>
                  </tr>
                  <tr>
                      <td>John</td>
                      <td>+1-949-468-2750</td>
                  </tr>
              </tbody>
          </table>
      </body>
  </html>
  ```

  Notice how when looking at a served version of this page, it’s quite plain.

+ Now consider the following HTML that implements the use of Bootstrap:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates table with Bootstrap -->
  
  <html lang="en">
      <head>
          <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
          <title>phonebook</title>
      </head>
      <body>
          <table class="table">
              <thead>
                  <tr>
                      <th scope="col">Name</th>
                      <th scope="col">Number</th>
                  </tr>
              </thead>
              <tbody>
                  <tr>
                      <td>Carter</td>
                      <td>+1-617-495-1000</td>
                  </tr>
                  <tr>
                      <td>David</td>
                      <td>+1-949-468-2750</td>
                  </tr>
              </tbody>
          </table>
      </body>
  </html>
  ```

  Notice how much prettier this website is now.

+ Similarly, consider to the following expansion of our search page created earlier:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates layout with Bootstrap -->
  
  <html lang="en">
      <head>
          <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
          <title>search</title>
      </head>
      <body>
  
          <div class="container-fluid">
  
              <ul class="m-3 nav">
                  <li class="nav-item">
                      <a class="nav-link text-dark" href="https://about.google/">About</a>
                  </li>
                  <li class="nav-item">
                      <a class="nav-link text-dark" href="https://store.google.com/">Store</a>
                  </li>
                  <li class="nav-item ms-auto">
                      <a class="nav-link text-dark" href="https://www.google.com/gmail/">Gmail</a>
                  </li>
                  <li class="nav-item">
                      <a class="nav-link text-dark" href="https://www.google.com/imghp">Images</a>
                  </li>
                  <li class="nav-item">
                      <a class="nav-link text-dark" href="https://www.google.com/intl/en/about/products">
                          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-grid-3x3-gap-fill" viewBox="0 0 16 16">
                              <path d="M1 2a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V2zM1 7a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V7zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V7zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V7zM1 12a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1v-2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1v-2zm5 0a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1v-2z"/>
                          </svg>
                      </a>
                  </li>
                  <li class="nav-item">
                      <a class="btn btn-primary" href="https://accounts.google.com/ServiceLogin" role="button">Sign in</a>
                  </li>
              </ul>
  
              <div class="text-center">
  
                  <!-- https://knowyourmeme.com/memes/happy-cat -->
                  <img alt="Happy Cat" class="img-fluid w-25" src="cat.gif">
  
                  <form action="https://www.google.com/search" class="mt-4" method="get">
                      <input autocomplete="off" autofocus class="form-control form-control-lg mb-4 mx-auto w-50" name="q" placeholder="Query" type="search">
                      <button class="btn btn-light">Google Search</button>
                      <button class="btn btn-light" name="btnI">I'm Feeling Lucky</button>
                  </form>
  
              </div>
  
          </div>
  
      </body>
  </html>
  ```

  This version of the page is exceedingly stylized, thanks to Bootstrap.

+ You can learn more about this in the [Bootstrap Documentation](https://getbootstrap.com/docs/).

## JavaScript

+ JavaScript is another programming language that allows for interactivity within web pages.

+ Consider the following implemntation of `hello.html` that includes both JavaScript and HTML:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates onsubmit -->
  
  <html lang="en">
      <head>
          <script>
  
              function greet()
              {
                  alert('hello, ' + document.querySelector('#name').value);
              }
  
          </script>
          <title>hello</title>
      </head>
      <body>
          <form onsubmit="greet(); return false;">
              <input autocomplete="off" autofocus id="name" placeholder="Name" type="text">
              <input type="submit">
          </form>
      </body>
  </html>
  ```

  Notice how this form uses an `onsubmit` property to trigger a `script` found at the top of the file. The script uses `alert` to create an alert pop-up. `#name.value` goes to the textbox on the page and obtains the value typed by the user.

+ Generally, it’s considered bad design to mix onsubmit and JavaScript. We can advance our code as follows:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates DOMContentLoaded -->
  
  <html lang="en">
      <head>
          <script>
  
              document.addEventListener('DOMContentLoaded', function() {
                  document.querySelector('form').addEventListener('submit', function(e) {
                      alert('hello, ' + document.querySelector('#name').value);
                      e.preventDefault();
                  });
              });
  
          </script>
          <title>hello</title>
      </head>
      <body>
          <form>
              <input autocomplete="off" autofocus id="name" placeholder="Name" type="text">
              <input type="submit">
          </form>
      </body>
  </html>
  ```

  Notice that this version of the code creates an `addEventListener` to listen to the form `submit` being triggered. Notice how `DOMContentLoaded` ensures that the whole page is loaded before executing the JavaScript.

+ JavaScript allows you to dynamically read and modify the html document loaded into memory such that the user need not reload to see changes.

+ Consider the following HTML:

  ```auto
  <!DOCTYPE html>
  
  <!-- Demonstrates programmatic changes to style -->
  
  <html lang="en">
      <head>
          <title>background</title>
      </head>
      <body>
          <button id="red">R</button>
          <button id="green">G</button>
          <button id="blue">B</button>
          <script>
  
              let body = document.querySelector('body');
              document.querySelector('#red').addEventListener('click', function() {
                  body.style.backgroundColor = 'red';
              });
              document.querySelector('#green').addEventListener('click', function() {
                  body.style.backgroundColor = 'green';
              });
              document.querySelector('#blue').addEventListener('click', function() {
                  body.style.backgroundColor = 'blue';
              });
  
          </script>
      </body>
  </html>
  ```

  Notice that JavaScript listens for when a specific button is clicked. Upon such a click, certain style attributes on the page are changed. `body` is defined as the body of the page. Then, an event listener waits for the clicking of one of the buttons. Then, the `body.style.backgroundColor` is changed.

+ Similarly, consider the following:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <script>
  
              // Toggles visibility of greeting
              function blink()
              {
                  let body = document.querySelector('body');
                  if (body.style.visibility == 'hidden')
                  {
                      body.style.visibility = 'visible';
                  }
                  else
                  {
                      body.style.visibility = 'hidden';
                  }
              }
  
              // Blink every 500ms
              window.setInterval(blink, 500);
  
          </script>
          <title>blink</title>
      </head>
      <body>
          hello, world
      </body>
  </html>
  ```

  This example blinks a text at a set interval. Notice that `window.setInterval` takes in two arguments: A function to be called and a wait period (in milliseconds) between function calls.

+ Consider the following:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
  
      <head>
          <title>autocomplete</title>
      </head>
  
      <body>
  
          <input autocomplete="off" autofocus placeholder="Query" type="text">
  
          <ul></ul>
  
          <script src="large.js"></script>
          <script>
        
              let input = document.querySelector('input');
              input.addEventListener('keyup', function(event) {
                  let html = '';
                  if (input.value) {
                      for (word of WORDS) {
                          if (word.startsWith(input.value)) {
                              html += `<li>${word}</li>`;
                          }
                      }
                  }
                  document.querySelector('ul').innerHTML = html;
              });
  
          </script>
  
      </body>
  </html>
  ```

  This is a JavaScript implementation of autocomplete. This pulls from a file (not pictured here) called `large.js` that is a list of words.

+ Interestingly, we can also geolocate using JavaScript:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <title>geolocation</title>
      </head>
      <body>
          <script>
            
              navigator.geolocation.getCurrentPosition(function(position) {
                  document.write(position.coords.latitude + ", " + position.coords.longitude);
              });
  
          </script>
      </body>
  </html>
  ```

  Notice that `navigator.geolocation` is used to `getCurrentPosition`. This will not work if your computer or browser does not allow for location tracking.

+ The capabilities of JavaScript are many and can be found in the [JavaScript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript).

## Summing Up

In this lesson, you learned how to create your own HTML files, style them, leverage third-party frameworks, and utilize JavaScript. Specifically, we discussed…

+   TCP/IP
+   DNS
+   HTML
+   Regular expressions.
+   CSS
+   Frameworks
+   JavaScript

See you next time!


# Lecture 9-Flask



+   [Welcome!](#welcome)
+   [Static to Dynamic](#static-to-dynamic)
+   [Flask](#flask)
+   [Forms](#forms)
+   [Layout](#layout)
+   [POST](#post)
+   [Frosh IMs](#frosh-ims)
+   [Flask and SQL](#flask-and-sql)
+   [Session](#session)
+   [Shopping Cart](#shopping-cart)
+   [Shows](#shows)
+   [AJAX and APIs](#ajax-and-apis)
+   [JSON](#json)
+   [Summing Up](#summing-up)

## Welcome!

+   In previous weeks, you have learned numerous programming languages, techniques, and strategies.
+   Indeed, this class has been far less of a *C class* or *Python class* and far more of a *programming class*, such that you can go on to follow future trends.
+   In these past several weeks, you have learned *how to learn* about programming.
+   Today, we will be moving from HTML and CSS into combining HTML, CSS, SQL, Python, and JavaScript so you can create your own web applications.

## Static to Dynamic

+   Up until this point, all HTML you saw was pre-written and static.
+   In the past, when you visited a page, the browser downloaded an HTML page, and you were able to view it. These are considered *static* pages, in that what programmed in the HTML is exactly what the user sees and downloads to their internet browser.
+   Dynamic pages refer to the ability of Python and similar languages to create HTML files on-the-fly. Accordingly, you can have web pages that are generated by options selected by your user.
+   You have used `http-server` in the past to serve your web pages. Today, we are going to utilize a new server that can parse out a web address and perform actions based on the URL provided.

## Flask

+ *Flask* is a third-party library that allows you to host web applications using the Flask framework, or a micro-framework, within Python.

+ You can run flask by executing `flask run` in your terminal window in [cs50.dev](https://cs50.dev/).

+ To do so, you will need a file called `app.py` and a folder called `templates`.

+ To get started, create a folder called `templates` and create a file called `index.html` with the following code:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>hello</title>
      </head>
      <body>
          hello, {{ name }}
      </body>
  </html>
    
  ```

  Notice the double `{{ name }}` that is a placeholder for something that will be later provided by our Flask server.

+ Then, in the same folder that the `templates` folder appears, create a file called `app.py` and add the following code:

  ```auto
  # Uses request.args.get
  
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  
  @app.route("/")
  def index():
      name = request.args.get("name", "world")
      return render_template("index.html", name=name)
  ```

  +   Notice that this code defines `app` as the Flask application. Then, it defines the `/` route of `app` as returning the contents of `index.html` with the argument of `name`. By default, the `request.args.get` function will look for the `name` being provided by the user. If no name is provided, it will default to `world`.
  +   `@app.route` is otherwise known as a decorator.

+ Finally, add a final file in the same folder as `app.py` called `requirements.txt` that has only a single line of code:

  Notice only `Flask` appears in this file.

+ You can run this file by typing `flask run` in the terminal window. If Flask does not run, ensure that your syntax is correct in each of the files above. Further, if Flask will not run, make sure your files are organized as follows:

  ```auto
  /templates
      index.html
  app.py
  requirements.txt
  ```

+ Once you get it running, you will be prompted to click a link. Once you navigate to that webpage, try adding `?name=[Your Name]` to the base URL in your browser’s URL bar.

## Forms

+ Improving upon our program, we know that most users will not type arguments into the address bar. Instead, programmers rely upon users to fill out forms on web pages. Accordingly, we can modify index.html as follows:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>hello</title>
      </head>
      <body>
          <form action="/greet" method="get">
              <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
              <button type="submit">Greet</button>
          </form>
      </body>
  </html>
  ```

  Notice that a form is now created that takes the user’s name and then passes it off to a route called `/greet`.

+ Further, we can change `app.py` as follows:

  ```auto
  # Adds a form, second route
  
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  
  @app.route("/")
  def index():
      return render_template("index.html")
  
  
  @app.route("/greet")
  def greet():
      return render_template("greet.html", name=request.args.get("name", "world"))
  ```

  Notice that the default path will display a form for the user to input their name. The `/greet` route will pass the `name` to that web page.

+ To finalize this implementation, you will need another template for `greet.html` in the `templates` folder as follows:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>hello</title>
      </head>
      <body>
          hello, {{ name }}
      </body>
  </html>
  ```

  Notice that this route will now render the greeting to the user, followed by their name.

## Layout

+ Both of our web pages, `index.html` and `greet.html`, have much of the same data. Wouldn’t it be nice to allow the body to be unique, but copy the same layout from page to page?

+ First, create a new template called `layout.html` and write code as follows:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>hello</title>
      </head>
      <body>
          {% block body %}{% endblock %}
      </body>
  </html>
  ```

  Notice that the `{% block body %}{% endblock %}` allows for the insertion of other code from other HTML files.

+ Then, modify your `index.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
  
      <form action="/greet" method="get">
          <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
          <button type="submit">Greet</button>
      </form>
  
  {% endblock %}
  ```

  Notice that the line `{% extends "layout.html" %}` tells the server where to get the layout of this page. Then, the `{% block body %}{% endblock %}` tells what code to be inserted into `layout.html`.

+ Finally, change `greet.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      hello, {{ name }}
  {% endblock %}
  ```

  Notice how this code is shorter and more compact.

## POST

+ You can imagine scenarios where it is not safe to utilize `get`, as usernames and passwords would show up in the URL.

+ We can utilize the method `post` to help with this problem by modifying `app.py` as follows:

  ```auto
  # Switches to POST
  
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  
  @app.route("/")
  def index():
      return render_template("index.html")
  
  
  @app.route("/greet", methods=["POST"])
  def greet():
      return render_template("greet.html", name=request.form.get("name", "world"))
  ```

  Notice that `POST` is added to the `/greet` route, and that we use `request.form.get` rather than `request.args.get`.

+ This tells the server to look *deeper* in the virtual envelope and not reveal the items in `post` in the URL.

+ Still, this code can be advanced further by utilizing a single route for both `get` and `post`. To do this, modify `app.py` as follows:

  ```auto
  # Uses a single route
  
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  
  @app.route("/", methods=["GET", "POST"])
  def index():
      if request.method == "POST":
          return render_template("greet.html", name=request.form.get("name", "world"))
      return render_template("index.html")
  ```

  Notice that both `get` and `post` are done in a single routing. However, `request.method` is utilized to properly route based upon the type of routing requested by the user.

+ Accordingly, you can modify your `index.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
  
      <form action="/" method="post">
          <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
          <button type="submit">Greet</button>
      </form>
  
  {% endblock %}
  ```

  Notice that the form `action` is changed.

+ Still, there is a bug still in this code. With our new implementation, when someone types in no name into the form, `Hello,` is displayed without a name. We can improve our code by editing `app.py` as follows:

  ```auto
  # Moves default value to template
  
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  
  @app.route("/", methods=["GET", "POST"])
  def index():
      if request.method == "POST":
          return render_template("greet.html", name=request.form.get("name"))
      return render_template("index.html")
  ```

  Notice that `name=request.form.get("name"))` is changed.

+ Finally, change `greet.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
  
      hello, {% if name %}{{ name }}{% else %}world{% endif %}
  
  {% endblock %}
  ```

  Notice how `hello,` is changed to allow for a default output when no name is identified.

+ As we’ve been changing many files, you may wish to compare your final code with [our final code](https://cdn.cs50.net/2023/fall/lectures/9/src9/hello8/).

## Frosh IMs

+ Frosh IMs or *froshims* is a web application that allows students to register for intramural sports.

+ Close all your `hello` related windows and create a folder by typing `mkdir froshims` in the terminal window. Then, type `cd froshims` to browse to this folder. Within, create a directory called templates by typing `mkdir templates`. Finally, type `code app.py` and write code as follows:

  ```auto
  # Implements a registration form using a select menu, validating sport server-side
  
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  SPORTS = [
      "Basketball",
      "Soccer",
      "Ultimate Frisbee"
  ]
  
  
  @app.route("/")
  def index():
      return render_template("index.html", sports=SPORTS)
  
  
  @app.route("/register", methods=["POST"])
  def register():
  
      # Validate submission
      if not request.form.get("name") or request.form.get("sport") not in SPORTS:
          return render_template("failure.html")
  
      # Confirm registration
      return render_template("success.html")
  ```

  Notice that a `failure` option is provided, such that a failure message will be displayed to the user if the `name` or `sport` field is not properly filled out.

+ Next, create a file in the `templates` folder called `index.html` by typing `code templates/index.html` and write code as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      <h1>Register</h1>
      <form action="/register" method="post">
          <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
          <select name="sport">
              <option disabled selected value="">Sport</option>
              {% for sport in sports %}
                  <option value="{{ sport }}">{{ sport }}</option>
              {% endfor %}
          </select>
          <button type="submit">Register</button>
      </form>
  {% endblock %}
  ```

+ Next, create a file called `layout.html` by typing `code templates/layout.html` and write code as follows:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>froshims</title>
      </head>
      <body>
          {% block body %}{% endblock %}
      </body>
  </html>
  ```

+ Fourth, create a file in templates called `success.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      You are registered!
  {% endblock %}
  ```

+ Finally, create a file in templates called `failure.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      You are not registered!
  {% endblock %}
  ```

+ You can imagine how we might want to see the various registration options using radio buttons. We can improve `index.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      <h1>Register</h1>
      <form action="/register" method="post">
          <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
          {% for sport in sports %}
              <input name="sport" type="radio" value="{{ sport }}"> {{ sport }}
          {% endfor %}
          <button type="submit">Register</button>
      </form>
  {% endblock %}
  ```

+ Executing `flask run` you can see how the interface has now changed.

+ We can further improve upon our program by enabling checkboxes. Modify `index.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      <h1>Register</h1>
      <form action="/register" method="post">
          <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
          {% for sport in sports %}
              <input name="sport" type="checkbox" value="{{ sport }}"> {{ sport }}
          {% endfor %}
          <button type="submit">Register</button>
      </form>
  {% endblock %}
  ```

  Notice that `type` is changed to `checkbox`.

+ To implement this, we will need to modify `app.py`:

  ```auto
  # Implements a registration form using checkboxes
  
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  SPORTS = [
      "Basketball",
      "Soccer",
      "Ultimate Frisbee"
  ]
  
  
  @app.route("/")
  def index():
      return render_template("index.html", sports=SPORTS)
  
  
  @app.route("/register", methods=["POST"])
  def register():
  
      # Validate submission
      if not request.form.get("name"):
          return render_template("failure.html")
      for sport in request.form.getlist("sport"):
          if sport not in SPORTS:
              return render_template("failure.html")
  
      # Confirm registration
      return render_template("success.html")
  ```

  Notice how `for sport in` allows iteration through all the sports selected by the user.

+ You can imagine how we might want to accept the registration of many different registrants. We can improve `app.py` as follows:

  ```auto
  # Implements a registration form, storing registrants in a dictionary, with error messages
  
  from flask import Flask, redirect, render_template, request
  
  app = Flask(__name__)
  
  REGISTRANTS = {}
  
  SPORTS = [
      "Basketball",
      "Soccer",
      "Ultimate Frisbee"
  ]
  
  
  @app.route("/")
  def index():
      return render_template("index.html", sports=SPORTS)
  
  
  @app.route("/register", methods=["POST"])
  def register():
  
      # Validate name
      name = request.form.get("name")
      if not name:
          return render_template("error.html", message="Missing name")
  
      # Validate sport
      sport = request.form.get("sport")
      if not sport:
          return render_template("error.html", message="Missing sport")
      if sport not in SPORTS:
          return render_template("error.html", message="Invalid sport")
  
      # Remember registrant
      REGISTRANTS[name] = sport
  
      # Confirm registration
      return redirect("/registrants")
  
  
  @app.route("/registrants")
  def registrants():
      return render_template("registrants.html", registrants=REGISTRANTS)
  ```

  Notice that a dictionary called `REGISTRANTS` is used to log the `sport` selected by `REGISTRANTS[name]`. Also, notice that `registrants=REGISTRANTS` passes the dictionary on to this template.

+ Additionally, we can implement `error.html`:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      <h1>Error</h1>
      <p>{{ message }}</p>
      <img alt="Grumpy Cat" src="/static/cat.jpg">
  {% endblock %}
  ```

+ Further, create a new template called `registrants.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      <h1>Registrants</h1>
      <table>
          <thead>
              <tr>
                  <th>Name</th>
                  <th>Sport</th>
              </tr>
          </thead>
          <tbody>
              {% for name in registrants %}
                  <tr>
                      <td>{{ name }}</td>
                      <td>{{ registrants[name] }}</td>
                  </tr>
              {% endfor %}
          </tbody>
      </table>
  {% endblock %}
  ```

  Notice that `{% for name in registrants %}...{% endfor %}` will iterate through each of the registrants. Very powerful to be able to iterate on a dynamic web page!

+ You now have a web application! However, there are some security flaws! Because everything is client-side, an adversary could change the HTML and *hack* a website. Further, this data will not persist if the server is shut down. Could there be some way we could have our data persist even when the server restarts?

## Flask and SQL

+ Just as we have seen how Python can interface with a SQL database, we can combine the power of Flask, Python, and SQL to create a web application where data will persist!

+ To implement this, you will need to take a number of steps.

+ First, modify `requirements.txt` as follows:

+ Modify `index.html` as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      <h1>Register</h1>
      <form action="/register" method="post">
          <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
          {% for sport in sports %}
              <input name="sport" type="radio" value="{{ sport }}"> {{ sport }}
          {% endfor %}
          <button type="submit">Register</button>
      </form>
  {% endblock %}
  ```

+ Modify `layout.html` as follows:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>froshims</title>
      </head>
      <body>
          {% block body %}{% endblock %}
      </body>
  </html>
  ```

+ Ensure `failure.html` appears as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      You are not registered!
  {% endblock %}
  ```

+ Modify `registrants.html` to appear as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
      <h1>Registrants</h1>
      <table>
          <thead>
              <tr>
                  <th>Name</th>
                  <th>Sport</th>
                  <th></th>
              </tr>
          </thead>
          <tbody>
              {% for registrant in registrants %}
                  <tr>
                      <td>{{ registrant.name }}</td>
                      <td>{{ registrant.sport }}</td>
                      <td>
                          <form action="/deregister" method="post">
                              <input name="id" type="hidden" value="{{ registrant.id }}">
                              <button type="submit">Deregister</button>
                          </form>
                      </td>
                  </tr>
              {% endfor %}
          </tbody>
      </table>
  {% endblock %}
  ```

  Notice that a hidden value `registrant.id` is included such that it’s possible to use this `id` later in `app.py`

+ Finally, modify `app.py` as follows:

  ```auto
  # Implements a registration form, storing registrants in a SQLite database, with support for deregistration
  
  from cs50 import SQL
  from flask import Flask, redirect, render_template, request
  
  app = Flask(__name__)
  
  db = SQL("sqlite:///froshims.db")
  
  SPORTS = [
      "Basketball",
      "Soccer",
      "Ultimate Frisbee"
  ]
  
  
  @app.route("/")
  def index():
      return render_template("index.html", sports=SPORTS)
  
  
  @app.route("/deregister", methods=["POST"])
  def deregister():
  
      # Forget registrant
      id = request.form.get("id")
      if id:
          db.execute("DELETE FROM registrants WHERE id = ?", id)
      return redirect("/registrants")
  
  
  @app.route("/register", methods=["POST"])
  def register():
  
      # Validate submission
      name = request.form.get("name")
      sport = request.form.get("sport")
      if not name or sport not in SPORTS:
          return render_template("failure.html")
  
      # Remember registrant
      db.execute("INSERT INTO registrants (name, sport) VALUES(?, ?)", name, sport)
  
      # Confirm registration
      return redirect("/registrants")
  
  
  @app.route("/registrants")
  def registrants():
      registrants = db.execute("SELECT * FROM registrants")
      return render_template("registrants.html", registrants=registrants)
  ```

  Notice that the `cs50` library is utilized. A route is included for `register` for the `post` method. This route will take the name and sport taken from the registration form and execute a SQL query to add the `name` and the `sport` to the `registrants` table. The `deregister` routes to a SQL query that will grab the user’s `id` and utilize that information to deregister this individual.

+ You can read more in the [Flask documentation](https://flask.palletsprojects.com/).

## Session

+ While the above code is useful from an administrative standpoint, where a back-office administrator could add and remove individuals from the database, one can imagine how this code is not safe to implement on a public server.

+ For one, bad actors could make decisions on behalf of other users by hitting the deregister button – effectively deleting their recorded answer from the server.

+ Web services like Google use login credentials to ensure users only have access to the right data.

+ We can actually implement this itself using *cookies*. Cookies are small files that are stored on your computer, such that your computer can communicate with the server and effectively say, “I’m an authorized user that has already logged in.” This authorization through this cookie is called a *session*.

+ In the simplest form, we can implement this by creating a folder called `login` and then adding the following files.

+ First, create a file called `requirements.txt` that reads as follows:

  Notice that in addition to `Flask`, we also include `Flask-Session`, which is required to support login sessions.

+ Second, in a `templates` folder, create a file called `layout.html` that appears as follows:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>login</title>
      </head>
      <body>
          {% block body %}{% endblock %}
      </body>
  </html>
  ```

  Notice this provides a very simple layout with a title and a body.

+ Third, create a file in the `templates` folder called `index.html` that appears as follows:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
  
      {% if name %}
          You are logged in as {{ name }}. <a href="/logout">Log out</a>.
      {% else %}
          You are not logged in. <a href="/login">Log in</a>.
      {% endif %}
  
  {% endblock %}
  ```

  Notice that this file looks to see if `session["name"]` exists (elaborated further in `app.py` below). If it does, it will display a welcome message. If not, it will recommend you browse to a page to log in.

+ Fourth, create a file called `login.html` and add the following code:

  ```auto
  {% extends "layout.html" %}
  
  {% block body %}
  
      <form action="/login" method="post">
          <input autocomplete="off" autofocus name="name" placeholder="Name" type="text">
          <button type="submit">Log In</button>
      </form>
  
  {% endblock %}
  ```

  Notice this is the layout of a basic login page.

+ Finally, create a file called `app.py` and write code as follows:

  ```auto
  from flask import Flask, redirect, render_template, request, session
  from flask_session import Session
  
  # Configure app
  app = Flask(__name__)
  
  # Configure session
  app.config["SESSION_PERMANENT"] = False
  app.config["SESSION_TYPE"] = "filesystem"
  Session(app)
  
  
  @app.route("/")
  def index():
      return render_template("index.html", name=session.get("name"))
  
  
  @app.route("/login", methods=["GET", "POST"])
  def login():
      if request.method == "POST":
          session["name"] = request.form.get("name")
          return redirect("/")
      return render_template("login.html")
  
  
  @app.route("/logout")
  def logout():
      session.clear()
      return redirect("/")
  ```

  Notice the modified *imports* at the top of the file, including `session`, which will allow for you to support sessions. Most important, notice how `session["name"]` is used in the `login` and `logout` routes. The `login` route will assign the login name provided and assign it to `session["name"]`. However, in the `logout` route, the logging out is implemented by clearing the value of `session`.

+ You can read more about sessions in the [Flask documentation](https://flask.palletsprojects.com/en/2.2.x/api/?highlight=session#flask.session).

## Shopping Cart

+ Moving on to a final example of utilizing Flask’s ability to enable a session.

+ We examined the following code for `store` in `app.py`. The following code was shown:

  ```auto
  from cs50 import SQL
  from flask import Flask, redirect, render_template, request, session
  from flask_session import Session
  
  # Configure app
  app = Flask(__name__)
  
  # Connect to database
  db = SQL("sqlite:///store.db")
  
  # Configure session
  app.config["SESSION_PERMANENT"] = False
  app.config["SESSION_TYPE"] = "filesystem"
  Session(app)
  
  
  @app.route("/")
  def index():
      books = db.execute("SELECT * FROM books")
      return render_template("books.html", books=books)
  
  
  @app.route("/cart", methods=["GET", "POST"])
  def cart():
  
      # Ensure cart exists
      if "cart" not in session:
          session["cart"] = []
  
      # POST
      if request.method == "POST":
          book_id = request.form.get("id")
          if book_id:
              session["cart"].append(book_id)
          return redirect("/cart")
  
      # GET
      books = db.execute("SELECT * FROM books WHERE id IN (?)", session["cart"])
      return render_template("cart.html", books=books)
  ```

  Notice that `cart` is implemented using a list. Items can be added to this list using the `Add to Cart` buttons in `books.html`. When clicking such a button, the `post` method is invoked, where the `id` of the item is appended to the `cart`. When viewing the cart, invoking the `get` method, SQL is executed to display a list of the books in the cart.

+ You can see the rest of the files that power this `flask` implementation in the [source code](https://cdn.cs50.net/2023/fall/lectures/9/src9/).

## Shows

+ We looked at a pre-designed program called `shows`, in `app.py`:

  ```auto
  # Searches for shows using LIKE
  
  from cs50 import SQL
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  db = SQL("sqlite:///shows.db")
  
  
  @app.route("/")
  def index():
      return render_template("index.html")
  
  
  @app.route("/search")
  def search():
      shows = db.execute("SELECT * FROM shows WHERE title LIKE ?", "%" + request.args.get("q") + "%")
      return render_template("search.html", shows=shows)
  ```

  Notice how the `search` route allows for a way by which to search for a `show`. This search looks for titles `LIKE` the one provided by the user.

+ You can see the rest of the files of this implementation in the [source code](https://cdn.cs50.net/2023/fall/lectures/9/src9/).

## AJAX and APIs

+ An *application program interface* or *API* is a series of specifications that allow you to interface with another service. For example, we could utilize IMDB’s API to interface with their database. We might even integrate APIs for handling specific types of data downloadable from a server.

+ Improving upon `shows`, looking at an improvement of `app.py`, we saw the following:

  ```auto
  # Searches for shows using Ajax
  
  from cs50 import SQL
  from flask import Flask, render_template, request
  
  app = Flask(__name__)
  
  db = SQL("sqlite:///shows.db")
  
  
  @app.route("/")
  def index():
      return render_template("index.html")
  
  
  @app.route("/search")
  def search():
      q = request.args.get("q")
      if q:
          shows = db.execute("SELECT * FROM shows WHERE title LIKE ? LIMIT 50", "%" + q + "%")
      else:
          shows = []
      return render_template("search.html", shows=shows)
  ```

  Notice that the `search` route executes a SQL query.

+ Looking at `search.html`, you’ll notice that it is very simple:

  ```auto
  {% for show in shows %}
      <li>{{ show["title"] }}</li>
  {% endfor %}
  ```

  Notice that it provides a bulleted list.

+ Finally, looking at `index.html`, notice that *AJAX* code is utilized to power the search:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>shows</title>
      </head>
      <body>
  
          <input autocomplete="off" autofocus placeholder="Query" type="search">
  
          <ul></ul>
  
          <script>
        
              let input = document.querySelector('input');
              input.addEventListener('input', async function() {
                  let response = await fetch('/search?q=' + input.value);
                  let shows = await response.text();
                  document.querySelector('ul').innerHTML = shows;
              });
  
          </script>
  
      </body>
  </html>
  ```

  Notice an event listener is utilized to dynamically query the server to provide a list that matches the title provided. This will locate the `ul` tag in the HTML and modify the web page accordingly to include the list of the matches.

+ You can read more in the [AJAX documentation](https://api.jquery.com/category/ajax/).

## JSON

+ *JavaScript Object Notation* or *JSON* is text file of dictionaries with keys and values. This is a raw, computer-friendly way to get lots of data.

+ JSON is a very useful way of getting back data from the server.

+ You can see this in action in the `index.html` we examined together:

  ```auto
  <!DOCTYPE html>
  
  <html lang="en">
      <head>
          <meta name="viewport" content="initial-scale=1, width=device-width">
          <title>shows</title>
      </head>
      <body>
  
          <input autocomplete="off" autofocus placeholder="Query" type="text">
  
          <ul></ul>
  
          <script>
        
              let input = document.querySelector('input');
              input.addEventListener('input', async function() {
                  let response = await fetch('/search?q=' + input.value);
                  let shows = await response.json();
                  let html = '';
                  for (let id in shows) {
                      let title = shows[id].title.replace('<', '&lt;').replace('&', '&amp;');
                      html += '<li>' + title + '</li>';
                  }
                  document.querySelector('ul').innerHTML = html;
              });
  
          </script>
  
      </body>
  </html>
  ```

  While the above may be somewhat cryptic, it provides a starting point for you to research JSON on your own to see how it can be implemented in your own web applications.

+ Further, we examined `app.py` to see how the JSON response is obtained:

  ```auto
  # Searches for shows using Ajax with JSON
  
  from cs50 import SQL
  from flask import Flask, jsonify, render_template, request
  
  app = Flask(__name__)
  
  db = SQL("sqlite:///shows.db")
  
  
  @app.route("/")
  def index():
      return render_template("index.html")
  
  
  @app.route("/search")
  def search():
      q = request.args.get("q")
      if q:
          shows = db.execute("SELECT * FROM shows WHERE title LIKE ? LIMIT 50", "%" + q + "%")
      else:
          shows = []
      return jsonify(shows)
  ```

  Notice how `jsonify` is used to convert the result into a readable format acceptible by contemporary web applications.

+ You can read more in the [JSON documentation](https://www.json.org/json-en.html).

## Summing Up

In this lesson, you learned how to utilize Python, SQL, and Flask to create web applications. Specifically, we discussed…

+   GET
+   POST
+   Flask
+   Session
+   APIs
+   AJAX
+   JSON

See you next time for our final lecture!



# Lecture 10-Cybersecurity

## Cybersecurity

+   [Recap](#recap)
+   [Looking Ahead](#looking-ahead)
+   [Cybersecurity](#cybersecurity-1)
+   [Passwords](#passwords)
+   [Phone Security](#phone-security)
+   [Password Managers](#password-managers)
+   [Two-factor Authentication](#two-factor-authentication)
+   [Hashing](#hashing)
+   [Cryptography](#cryptography)
+   [Passkeys](#passkeys)
+   [Encryption](#encryption)
+   [Deletion](#deletion)
+   [Summing Up](#summing-up)

## Recap

+   Over these past ten weeks, you have been drinking from the proverbial firehose.
+   While in this course, you learned how to program many programming languages; indeed, our great hope is that you *learned how to program* in all: Regardless of the programming language.
+   Further, we hope that you *learned how to solve problems* above all else.

## Looking Ahead

+   As you journey from the work of this course to the world outside CS50, you may want to take a number of steps to prepare.
+   To be able to execute commands on the terminal, much like you did on [CS50.dev](https://cs50.dev/), you can install command-line tools on your [Mac](https://developer.apple.com/xcode/) or [PC](https://learn.microsoft.com/en-us/windows/wsl/about).
+   You can learn more about [Git](https://youtu.be/MJUJ4wbFm_A).
+   You can [download](https://code.visualstudio.com/) and [learn](https://cs50.readthedocs.io/cs50.dev/) about VS Code.
+   You can host a website using [GitHub](https://pages.github.com/) or [Netlify](https://www.netlify.com/).
+   You can host a web app using [AWS](https://aws.amazon.com/education/awseducate/), [Azure](https://azure.microsoft.com/en-us/free/students/), or [Google Cloud](https://cloud.google.com/edu/students).
+   You can ask questions in relevant online communities.
+   You can ask questions using AI-based tools like [OpenAI](https://chat.openai.com/) and [GitHub Copilot](https://github.com/features/copilot).
+   You can take any of our other CS50 courses.
+   You can join one of our many [communities](https://cs50.harvard.edu/communities).

## Cybersecurity

+   Today will be a high-level overview of some of the cybersecurity-related topics.
+   Cybersecurity is understanding how our data is *secure* or *not secure*.

## Passwords

+ One cybersecurity concern relates to our passwords.

+ Passwords are one method used to secure data online.

+ There are common passwords that people use:

  ```auto
  1. 123456
  2. admin
  3. 12345678
  4. 123456789
  5. 1234
  6. 12345
  7. password
  8. 123
  9. Aa123456
  10. 1234567890
  ```

+ If you have one of the passwords above, most likely, millions of people have the same password as you!

+ Adversaries in the world will start with this list.

+ Bad guys can also guess most of the heuristics you use to add symbols to your password.

+ Adversaries can use *brute-force attacks*, using a dictionary of passwords to simply try every possible password.

+ Your password is likely not as secure as you think it is.

## Phone Security

+ Many phones are secured by a four-digit code.

+ The most simple form of attack would be to brute-force attempt all possible passwords.

+ There are 10,000 possible passwords when using a four-digit code.

+ If it takes one guess per second, it will take 10,000 seconds to crack the password.

+ However, if a programmer creates a program to generate all possible codes, the time required would be minimal. Consider the following code in Python:

  ```auto
  from string import digits
  from itertools import product
  
  for passcode in product(digits, repeat=4):
      print(passcode)
  ```

+ It should be quite disconcerting that the code above could take only a few seconds (at most!) to discover your password.

+ We could improve our security by switching to a four-letter password. This would result in 7,311,616 possible passwords.

+ Including uppercase and lowercase characters would create over 78 million possibilities.

+ Consider how we could modify your code to discover these passwords:

  ```auto
  from string import ascii_letters
  from itertools import product
  
  for passcode in product(ascii_letters, repeat=4):
      print(passcode)
  ```

+ We could even add the ability to look at all possible eight-digit passwords with letters, numbers, and punctuations:

  ```auto
  from string import ascii_letters, digits, punctuation
  from itertools import product
  
  for passcode in product(ascii_letters + digits + punctuation, repeat=8):
      print(passcode)
  ```

+ Expanding to eight characters, including upper and lowercase letters, numbers, and symbols, would result in 6,095,689,385,410,816 possible combinations.

+ In the digital world, you simply want your password to be better than other peoples’ passwords such that others would be attacked far before you—as you are a much less convenient target.

+ A downside of using such a long password is the downside of having to remember it.

+ Accordingly, there are other defenses that could be employed to slow down an attacker. For example, some phone manufacturers lock out those who guess a password incorrectly.

+ Security is about finding a “sweet spot” between the trade-offs of enhanced security while maintaining convenience.

## Password Managers

+   Password managers can be used to create very challenging passwords and remember them for you.
+   The probability of a password secured by a password manager being broken is very, very low.
+   You’d hope that such password managers are secure. However, if one gains access to your password manager, they would have access to all your passwords.
+   In the end, you are far less likely to be at risk by those you live with—and much more likely to be at risk by the billions of other people on the internet.
+   As mentioned prior, you can make a decision based on a balance between security and convenience.

## Two-factor Authentication

+   Adding another means by which you must authenticate adds further security. However, there is a human cost as you might not have access to your second factor.
+   These are implemented as one-time passwords of sorts that are sent to an email, device, or phone number.
+   Always, security policies attempt to balance the needs of security and human convenience.

## Hashing

+ Your account information and other sensitive data should not be stored as raw text in an online database.

+ If a database becomes compromised and all credentials are stored in plain text, credentials for other services at other websites are likely also compromised.

+ Hence, hashing algorithms, as discussed earlier in this course, are used to store only hashed values of passwords.

+ One-way hashing allows online services to actually *never* store the original password typed by the user: Only the hashed value of these passwords. Accordingly, if there is a breach, only the hashed value will be known.

+ *Rainbow tables* are huge dictionaries that adversaries use to attempt to pre-hash possible passwords as a means by which to attempt to break the hash algorithm.

+ As an additional process to heightened security, programmers may sometimes introduce *salting* where it becomes unlikely that multiple users may have the same hash value to represent their passwords. You can imagine this as follows:

  ![salt and password being fed to an algorithm outputting a hash](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week10Slide106.png)

## Cryptography

+   Similar to hashing, a cipher algorithm can use a *public key* and text to create ciphertext.
+   In turn, a *private key* and the ciphertext can be fed to the algorithm to decrypt the text.

## Passkeys

+ Passkeys are a new technology only emerging in the most recent months.

+ Through private keys and a challenge being fed to an algorithm, websites can authenticate you through the unique signature created by your device.

  ![public key and challenge being provided to an alogirthm resulting in a signature](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week10Slide125.png)

+ Hence, passwords and usernames may soon become obsolete.

## Encryption

+   Encryption is a way by which data is obscured such that only the sender and intended receiver can be read.
+   Early in this course, we learned a very simple algorithm to “shift” the text by one or more characters as a rudimentary form of encryption.
+   *End-to-end encryption* is a way by which encrypting and decrypting happen on the same system without a middleman. This prevents the middleman or a malicious actor from being able to snoop on your data. Zoom and Apple Messages can both utilize end-to-end encryption.

## Deletion

+ Trashing a file on your computer or emptying the trash can does not actually delete the actual bits of the file on your computer.

+ Instead, remnants of the files are left.

  ![remnants of a file on a hard drive](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week10Slide136.png)

+ *Secure deletion* is where the remnants of those files are turned into zeros and ones.

+ Still, some remnants may remain because of what is rendered inaccessible by the operating system.

+ *Full-disk encryption* allows your entire hard drive to be encrypted. Thus, your deleted files are less accessible to adversaries.

+ Considering encryption, it’s this same technology that adversaries use to create *ransomware* that can, quite literally, hold your hard drive for ransom.

## Summing Up

+   Use a password manager.
+   Use two-factor authentication.
+   Use (end-to-end) encryption.

