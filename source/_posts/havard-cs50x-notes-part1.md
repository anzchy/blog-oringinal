---
title: 哈佛 CS50x notes Lecture 0-5
date: 2024-08-10 09:31:32
categories:
- 编程
- 自学
tags:
- computer science
---



# Harvard CS50x Course Notes Lecture 1-5

# Lecture 0-Scratch



+   [Welcome!](#welcome)
+   [What’s Ahead](#whats-ahead)
+   [Community!](#community)
+   [Computer Science](#computer-science)
+   [ASCII](#ascii)
+   [Unicode](#unicode)
+   [Representation](#representation)
+   [Algorithms](#algorithms)
+   [Pseudocode](#pseudocode)
+   [Artificial Intelligence](#artificial-intelligence)
+   [Scratch](#scratch)
+   [Hello World](#hello-world)
+   [Hello, You](#hello-you)
+   [Meow and Abstraction](#meow-and-abstraction)
+   [Conditionals](#conditionals)
+   [Oscartime](#oscartime)
+   [Ivy’s Hardest Game](#ivys-hardest-game)
+   [Summing Up](#summing-up)

## Welcome!

+   This class is about more than computer programming!
+   Indeed, this class is about problem-solving in a way that is exceedingly empowering! You will likely take the problem solving that you learn here will likely be instantly applicable to your work beyond this course and even your career as a whole!
+   However, it will not be easy! You will be “drinking from the firehose” of knowledge during this course. You’ll be amazed at what you will be able to accomplish in the coming weeks.
+   This course is far more about you advancing “you” from “where you are today” than hitting some imagined standard.
+   The most important opening consideration in this course: Give the time you need to learn through this course. Everyone learns differently. If something does not work out well at the start, know that with time you will grow and grow in your skill.
+   Don’t be scared if this is your first computer science class! For most of your peers, this is their first computer science class too!

## What’s Ahead

+ You will be learning this week about Scratch, a visual programming language.

+ Then, in future weeks, you will learn about C. That will look something like this:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
    printf("hello, world\n");
  }
  ```

+ Further, as the weeks progress, you will learn about algorithms.

+ You will learn about memory.

+ You will learn about buggy code and what causes computer crashes.

+ You will learn about data structures such as a hash table.

+ Then, we will transition to a new, higher-level language called *Python*. Your code will look something like this:

+ This class will give you a strong understanding of how recent programming languages developed from the earlier ones.

+ You will learn SQL, JavaScript, HTML, and CSS.

+ We will also be looking at how we can use databases and third-party frameworks to build web applications.

## Community!

+   You are part of a community of those taking this course at Harvard College, Harvard Extension School, and via edX.org.
+   Puzzle Day and the CS50 Fair
+   You can attend CS50 Lunches and CS50 Hackathon, if you are student on Harvard’s campus.

## Computer Science

+ Essentially, computer programming is about taking some input and creating some output - thus solving a problem. What happens in between the input and output, what we could call *a black box,* is the focus of this course.

  ![Black box with input and output](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide38.png "Black box with input and output")

+ For example, we may need to take attendance for a class. We could use a system called *unary* to count, one finger at a time.

+ Computers today count using a system called *binary*. It’s from the term *binary digit* that we get a familiar term called *bit*. A *bit* is a zero or one: on or off.

+ Computers only speak in terms of zeros and ones. Zeros represent *off.* Ones represent *on.* Computers are millions, and perhaps billions, of transistors that are being turned on and off.

+ If you imagine using a light bulb, a single bulb can only count from zero to one.

+ However, if you were to have three light bulbs, there are more options open to you!

+ Using three light bulbs, the following could represent zero:

+ Similarly, the following would represent one:

+ By this logic, we could propose that the following equals two:

+ Extending this logic further, the following represents three:

+ Four would appear as:

+ We could, in fact, using only three light bulbs count as high as seven!

+ As a heuristic, we could imagine that the following values represent each possible place in our *binary digit*:

+ Computers use ‘base-2’ to count. This can be pictured as follows:

+ Therefore, you could say that it would require three bits (the four’s place, the two’s place, and the one’s place) to represent a number as high as seven.

+ Computers generally use eight bits (also known as a *byte*) to represent a number. For example, `00000101` is the number 5 in *binary*. `11111111` represents the number 255.

## ASCII

+ Just as numbers are binary patterns of ones and zeros, letters are represented using ones and zeros too!

+ Since there is an overlap between the ones and zeros that represent numbers and letters, the *ASCII* standard was created to map specific letters to specific numbers.

+ For example, the letter `A` was decided to map to the number 65. `01000001` represents the number 65 in binary.

+ If you received a text message, the binary under that message might represent the numbers 72, 73, and 33. Mapping these out to ASCII, your message would look as follows:

+ Thank goodness for standards like ASCII that allow us to agree upon these values!

+ Here is an expanded map of ASCII values:

  ![ASCII map](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide93.png "ASCII map")

+ If you wish, you can learn more about [ASCII](https://en.wikipedia.org/wiki/ASCII).

+ Since binary can only count up to *255* we are limited to the number of characters represented by ASCII.

## Unicode

+ As time has rolled on, there are more and more ways to communicate via text.

+ Since there were not enough digits in binary to represent all the various characters that could be represented by humans, the *Unicode* standard expanded the number of bits that can be transmitted and understood by computers. Unicode includes not only special characters, but emoji as well.

+ There are emoji that you probably use every day. The following may look familiar to you:

  ![emoji](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide103.png "emoji")

+ Computer scientists faced a challenge when wanting to assign various skin tones to each emoji to allow the communication to be further personalized. In this case, the creators and contributors of emoji decided that the initial bits would be the structure of the emoji itself, followed by skin tone.

+ For example, the unicode for a generic thumbs up is `U+1F44D`. However, the following represents the same thumbs up with a different skin tone: `U+1F44D U+1F3FD`.

+ More and more features are being added to the Unicode standard to represent further characters and emoji.

+ If you wish, you can learn more about [Unicode](https://en.wikipedia.org/wiki/Unicode).

+ If you wish, you can learn more about [emoji](https://en.wikipedia.org/wiki/Emoji).

## Representation

+ Zeros and ones can be used to represent color.

+ Red, green, and blue (called `RGB`) is a combination of three numbers.

  ![red green blue boxes](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide118.png "red green blue boxes")

+ Taking our previously used 72, 73, and 33, which said `HI!` via text, would be interpreted by image readers as a light shade of yellow. The red value would be 72, the green value would be 73, and the blue would be 33.

  ![yellow box](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide120.png "yellow box")

+ Further, zeros and ones can be used to represent images, videos, and music!

+ Images are simply collections of RGB values.

+ Videos are sequences of many images that are stored together, just like a flipbook.

+ Music can be represented through MIDI data.

## Algorithms

+ Problem-solving is central to computer science and computer programming.

+ Imagine the basic problem of trying to locate a single name in a phone book.

+ How might you go about this?

+ One approach could be to simply read from page one to the next to the next until reaching the last page.

+ Another approach could be to search two pages at a time.

+ A final and perhaps better approach could be to go to the middle of the phone book and ask, “Is the name I am looking for to the left or to the right?” Then, repeat this process, cutting the problem in half and half and half.

+ Each of these approaches could be called algorithms. The speed of each of these algorithms can be pictured as follows in what is called *big-O notation*:

  ![big o notation](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide141.png "big o notation")

  Notice that the first algorithm, highlighted in red, has a big-O of `n` because if there are 100 names in the phone book, it could take up to 100 tries to find the correct name. The second algorithm, where two pages were searched at a time, has a big-O of ‘n/2’ because we searched twice as fast through the pages. The final algorithm has a big-O of log2n as doubling the problem would only result in one more step to solve the problem.

## Pseudocode

+ The ability to create *pseudocode* is central to one’s success in both this class and in computer programming.

+ Pseudocode is a human-readable version of your code. For example, considering the third algorithm above, we could compose pseudocode as follows:

  ```auto
  1  Pick up phone book
  2  Open to middle of phone book
  3  Look at page
  4  If person is on page
  5      Call person
  6  Else if person is earlier in book
  7      Open to middle of left half of book
  8      Go back to line 3
  9  Else if person is later in book
  10     Open to middle of right half of book
  11     Go back to line 3
  12 Else
  13     Quit
  ```

+ Pseudocoding is such an important skill for at least two reasons. First, when you pseudocode before you create formal code, it allows you to think through the logic of your problem in advance. Second, when you pseudocode, you can later provide this information to others that are seeking to understand your coding decisions and how your code works.

+ Notice that the language within our pseudocode has some unique features. First, some of these lines begin with verbs like *pick up,* *open,* *look at.* Later, we will call these *functions*.

+ Second, notice that some lines include statements like `if` or `else if.` These are called *conditionals*.

+ Third, notice how there are expressions that can be stated as *true* or *false,* such as “person is earlier in the book.” We call these *boolean expressions*.

+ Finally, notice how these statements like “go back to line 3.” We call these *loops*.

+ These building blocks are the fundamentals of programming.

+ In the context of *Scratch*, which is discussed below, we will use each of the above basic building blocks of programming.

## Artificial Intelligence

+ Consider how we can utilize the building blocks above to start creating our own artificial intelligence. Look at the following pseudocode:

  ```auto
  If student says hello
      Say hello back
  Else if student says goodbye
      Say goodbye back
  Else if student asks how you are
      Say you're well
  Else if student asks why 111 in binary is 7 in decimal
  ...
  ```

  Notice how just to program a handful of interactions, many lines of code would be required. How many lines of code would be required for thousands or tens of thousands of possible interactions?

+ `large language models` look at patterns in large blocks of language. Such language models attempt to create a best guess of what words come after one another or alongside one another.

+ As very useful in many avenues of life and work, we stipulate that the utilization of AI-based software other than CS50’s own is *not reasonable*.

+ CS50’s own AI-based software tool called [CS50 Duck](https://cs50.ai/) is an AI helper that you can use during this course. It will help you, but not give away the entire answers to the course’s problems.

## Scratch

+ *Scratch* is a visual programming language developed by MIT.

+ Scratch utilizes the same essential coding building blocks that we covered earlier in this lecture.

+ Scratch is a great way to get into computer programming because it allows you to play with these building blocks in a visual manner, not having to be concerned about the syntax of curly braces, semicolons, parentheses, and the like.

+ Scratch `IDE` (integrated development environment) looks like the following:

  ![scratch interface](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide162.png "scratch interface")

  Notice that on the left, there are *building blocks* that you can use in your programming. To the immediate right of the building blocks, there is the area to which you can drag blocks to build a program. To the right of that, you see the *stage* where a cat stands. The stage is where your programming comes to life.

+ Scratch operates on a coordinate system as follows:

  ![scratch coordinate system](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide167.png "scratch coordinate system")

  Notice that the center of the stage is at coordinate (0,0). Right now, the cat’s position is at that same position.

## Hello World

+ To begin, drag the “when green flag clicked” building block to the programming area. Then, drag the `say` building block to the programming area and attach it to the previous block.

  ```scratch
  when green flag clicked
  say [hello, world]
  ```

  Notice that when you click the green flag now, on the stage, the cat says, “hello world.”

+ This illustrates quite well what we were discussing earlier regarding programming:

  ![scratch with black box](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Slide172.png "scratch with black box")

  Notice that the input `hello world` is passed to the function `say`, and the *side effect* of that function running is the cat saying `hello world`.

## Hello, You

+ We can make your program more interactive by having the cat say `hello` to someone specific. Modify your program as below:

  ```scratch
  when green flag clicked
  ask [What's your name?] and wait
  say (join [hello,] (answer))
  ```

  Notice that when the green flag is clicked, the function `ask` is run. The program prompts you, the user, `What's your name?` It then stores that name in the *variable* called `answer`. The program then passes `answer` to a special function called `join`, which combines two strings of text `hello`, and whatever name was provided. These collectively are passed to the `say` function. The cat says, `Hello,` and a name. Your program is now interactive.

+ Quite similarly, we can modify our program as follows:

  ```scratch
  when green flag clicked
  ask [What's your name?] and wait
  speak (join [hello,] (answer))
  ```

  Notice that this program, when the green flag is clicked, passes the same variable, joined with `hello`, to a function called `speak`.

## Meow and Abstraction

+ Along with pseudocoding, *abstraction* is an essential skill and concept within computer programming.

+ Abstraction is the act of simplifying a problem into smaller and smaller problems.

+ For example, if you were hosting a huge dinner for your friends, the *problem* of having to cook the entire meal could be quite overwhelming! However, if you break down the task of cooking the meal into smaller and smaller tasks (or problems), the big task of creating this delicious meal might feel less challenging.

+ In programming, and even within Scratch, we can see abstraction in action. In your programming area, program as follows:

  ```scratch
  when green flag clicked
  play sound (Meow v) until done
  wait (1) seconds
  play sound (Meow v) until done
  wait (1) seconds
  play sound (Meow v) until done
  ```

  Notice that you are doing the same thing over and over again. Indeed, if you see yourself repeatedly coding the same statements, it’s likely the case that you could program more artfully – abstracting away this repetitive code.

+ You can modify your code as follows:

  ```scratch
  when green flag clicked
  repeat (3)
  play sound (Meow v) until done
  wait (1) seconds
  ```

  Notice that the loop does exactly as the previous program did. However, the problem is simplified by abstracting away the repetition to a block that *repeats* the code for us.

+ We can even advance this further by using the `define` block, where you can create your own block (your own function)! Write code as follows:

  ```scratch
  define meow
  play sound (Meow v) until done
  wait (1) seconds
  
  when green flag clicked
  repeat (3)
  meow
  ```

  Notice that we are defining our own block called `meow`. The function plays the sound `meow`, then waits one second. Below that, you can see that when the green flag is clicked, our meow function is repeated three times.

+ We can even provide a way by which the function can take an input `n` and repeat a number of times:

  ```scratch
  define meow n times
  repeat (n)
   play sound [meow v] until done
   wait (1) seconds
  ```

  Notice how `n` is taken from “meow n times.” `n` is passed to the meow function through the `define` block.

+ The cat, by the way, we can call a `sprite` – a general term used in game programming for an object or character on the screen with which the player will interact.

## Conditionals

+ *conditionals* are an essential building block of programming, where the program looks to see if a specific condition has been met. If a condition is met, the program does something.

+ To illustrate a conditional, write code as follows:

  ```scratch
  when green flag clicked
  forever
  if <touching (mouse-pointer v)?> then
  play sound (Meow v) until done
  ```

  Notice that the `forever` block is utilized such that the `if` block is triggered over and over again, such that it can check continuously if the cat is touching the mouse pointer.

+ We can modify our program as follows to integrate video sensing:

  ```scratch
  when video motion > (50)
  play sound (Meow v) until done
  ```

+ Remember, programming is often a process of trial and error. If you get frustrated, take time to talk yourself through the problem at hand. What is the specific problem that you are working on right now? What is working? What is not working?

## Oscartime

+ We showed you in this lecture a number of Scratch programs to stoke your imagination.

+ *Oscartime* is one of David’s own Scratch programs – though the music may haunt him because of the number of hours he listened to it while creating this program. Take a few moments to play through the game yourself.

+ Building Oscartime ourselves, we first add the lamp post.

  ![oscartime interface](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week0Scratch10.png "oscartime interface")

+ Then, write code as follows:

  ```scratch
  when green flag clicked
  switch costume to (oscar1 v)
  forever
  if <touching (mouse-pointer v)?> then
  switch costume to (oscar2 v)
  else
  switch costume to (oscar1 v)
  ```

  Notice that moving your mouse over Oscar changes his costume. You can learn more by [exploring these code blocks](https://scratch.mit.edu/projects/565100517).

+ Then, modify your code as follow to create a falling piece of trash:

  ```scratch
  when green flag clicked
  go to x: (pick random (-240) to (240)) y: (180)
  forever
  if <(distance to (floor v)) > (0)> then
  change y by (-3)
  ```

  Notice that the trash’s position on the y-axis always begins at 180. The x position is randomized. While the trash is above the floor, it goes down 3 pixels at a time. You can learn more by [exploring these code blocks](https://scratch.mit.edu/projects/565117390).

+ Next, modify your code as follows to allow for the possibility of dragging trash.

  ```scratch
  when green flag clicked
  forever
  if <<mouse down?> and <touching (mouse-pointer v) ?>> then
  go to (mouse-pointer v)
  ```

  You can learn more by [exploring these code blocks](https://scratch.mit.edu/projects/565119737).

+ Next, we can implement the scoring variables as follows:

  ```scratch
  when green flag clicked
  forever
  if <touching (Oscar v) ?> then
  change (score) by (1)
  go to x: (pick random (-240) to (240)) y: (180)
  ```

  You can learn more by [exploring these code blocks](https://scratch.mit.edu/projects/565472267).

+ Go try the full game [Oscartime](https://scratch.mit.edu/projects/277537196).

## Ivy’s Hardest Game

+ Moving away from Oscartime to Ivy’s Hardest Game, we can now imagine how to implement movement within our program.

+ Our program has three main components.

+ First, write code as follows:

  ```scratch
  when green flag clicked
  go to x: (0) y: (0)
  forever
  listen for keyboard
  feel for walls
  ```

  Notice that when the green flag is clicked, our sprite moves to the center of the stage at coordinates (0,0) and then listens for the keyboard and checks for walls forever.

+ Second, add this second group of code blocks:

  ```scratch
  define listen for keyboard
  if <key (up arrow v) pressed?> then
  change y by (1)
  end
  if <key (down arrow v) pressed?> then
  change y by (-1)
  end
  if <key (right arrow v) pressed?> then
  change x by (1)
  end
  if <key (left arrow v) pressed?> then
  change x by (-1)
  end
  ```

  Notice how we have created a custom `listen for keyboard` script. For each of our arrow keys on the keyboard, it will move the sprite around the screen.

+ Finally, add this group of code blocks:

  ```scratch
  define feel for walls
  if <touching (left wall v) ?> then
  change x by (1)
  end
  if <touching (right wall v) ?> then
  change x by (-1)
  end
  ```

  Notice how we also have a custom `feel for walls` script. When a sprite touches a wall, it moves it back to a safe position – preventing it from walking off the screen.

+ You can learn more by [exploring these code blocks](https://scratch.mit.edu/projects/326129433).

+ Go try the full game [Ivy’s Hardest Game](https://scratch.mit.edu/projects/326129433/).

+ Scratch allows for many sprites to be on the screen at once.

+ Adding another sprite, add the following code blocks to your program:

  ```scratch
  when green flag clicked
  go to x: (0) y: (0)
  point in direction (90)
  forever
  if <<touching (left wall v)?> or <touching (right wall v)?>> then
  turn right (180) degrees
  end
  move (1) steps
  end
  ```

  Notice how the Yale sprite seems to get in the way of the Harvard sprite by moving back and forth. When it bumps into a wall, it turns around until it bumps the wall again. You can learn more by [exploring these code blocks](https://scratch.mit.edu/projects/565127193).

+ You can even make a sprite follow another sprite. Adding another sprite, add the following code blocks to your program:

  ```scratch
  when green flag clicked
  go to (random position v)
  forever
  point towards (Harvard v)
  move (1) steps
  ```

  Notice how the MIT logo now seems to follow around the Harvard one. You can learn more by [exploring these code blocks](https://scratch.mit.edu/projects/565479840).

+ Go try the full game [Ivy’s Hardest Game](https://scratch.mit.edu/projects/565742837).

## Summing Up

In this lesson, you learned how this course sits in the wide world of computer science and programming. You learned…

+   Few students come to this class with prior programming experience!
+   You are not alone! You are part of a community.
+   Problem solving is the essence of the work of computer scientists.
+   This course is not simply about programming – this course will introduce you to a new way of learning that you can apply to almost every area of life.
+   How numbers, text, images, music, and video are understood by computers.
+   The fundamental programming skill of pseudocoding.
+   Reasonable and unreasonable ways to utilize AI in this course.
+   How abstraction will play a role in your future work in this course.
+   The basic building blocks of programming, including functions, conditionals, loops, and variables.
+   How to build a project in Scratch.

See you next time!


# Lecture 1-C programming



+   [Welcome!](#welcome)
+   [Hello World](#hello-world)
+   [Functions](#functions)
+   [Variables](#variables)
+   [Conditionals](#conditionals)
+   [Loops](#loops)
+   [Operators and Abstraction](#operators-and-abstraction)
+   [Linux and the Command Line](#linux-and-the-command-line)
+   [Mario](#mario)
+   [Comments](#comments)
+   [Types](#types)
+   [Summing Up](#summing-up)

## Welcome!

+   In our previous session, we learned about Scratch, a visual programming language.
+   Indeed, all the essential programming concepts presented in Scratch will be utilized as you learn how to program any programming language.
+   Recall that machines only understand binary. Where humans write *source code*, a list of instructions for the computer that is human readable, machines only understand what we can now call *machine code*. This machine code is a pattern of ones and zeros that produces a desired effect.
+   It turns out that we can convert *source code* into `machine code` using a very special piece of software called a *compiler*. Today, we will be introducing you to a compiler that will allow you to convert source code in the programming language *C* into machine code.
+   Today, in addition to learning about how to code, you will be learning about how to write good code.
+   Code can be evaluated upon three axes. First, *correctness* refers to “does the code run as intended?” Second, *design* refers to “how well is the code designed?” Finally, *style* refers to “how aesthetically pleasing and consistent is the code?”

## Hello World

+ The integrated development environment (IDE) that is utilized for this course is *Visual Studio Code*, affectionately referred to as , which can be accessed via that same url, or simply as \*VS Code.\*

+ One of the most important reasons we utilize VS Code is that it has all the software required for the course already pre-loaded on it. This course and the instructions herein were designed with VS Code in mind.

+ Manually installing the necessary software for the course on your own computer is a cumbersome headache. Best always to utilize VS Code for assignments in this course.

+ You can open VS Code at [cs50.dev](https://cs50.dev/).

+ The compiler can be divided into a number of regions:

  ![IDE](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week1Slide017.png "IDE") Notice that there is a *file explorer* on the left side where you can find your files. Further, notice that there is a region in the middle called a *text editor* where you can edit your program. Finally, there is a `command line interface`, known as a *CLI*, *command line*, or *terminal window* where we can send commands to the computer in the cloud.

+ We will be using three commands to write, compile, and run our first program:

  ```auto
  code hello.c
  
  make hello
  
  ./hello
  
  ```

  The first command, `code hello.c` creates a file and allows us to type instructions for this program. The second command, `make hello`, *compiles* the file from our instructions in C and creates an executable file called `hello`. The last command, `./hello`, runs the program called `hello`.

+ We can build your first program in C by typing `code hello.c` into the terminal window. Notice that we deliberately lowercased the entire filename and included the `.c` extension. Then, in the text editor that appears, write code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      printf("hello, world\n");
  }
  ```

  Note that every single character above serves a purpose. If you type it incorrectly, the program will not run. `printf` is a function that can output a line of text. Notice the placement of the quotes and the semicolon. Further, notice that the `\n` creates a new line after the words `hello, world`.

+ Clicking back in the terminal window, you can compile your code by executing `make hello`. Notice that we are omitting `.c`. `make` is a compiler that will look for our `hello.c` file and turn it into a program called `hello`. If executing this command results in no errors, you can proceed. If not, double-check your code to ensure it matches the above.

+ Now, type `./hello` and your program will execute saying `hello, world`.

+ Now, open the *file explorer* on the left. You will notice that there is now both a file called `hello.c` and another file called `hello`. `hello.c` is able to be read by the compiler: It’s where your code is stored. `hello` is an executable file that you can run, but cannot be read by the compiler.

## Functions

+ In Scratch, we utilized the `say` block to display any text on the screen. Indeed, in C, we have a function called `printf` that does exactly this.

+ Notice our code already invokes this function:

  ```auto
  printf("hello, world\n");
  ```

  Notice that the printf function is called. The argument passed to printf is ‘hello, world\\n’. The statement of code is closed with a `;`.

+ A common error in C programming is the omission of a semicolon. Modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      printf("hello, world\n")
  }
  ```

  Notice the semicolon is now gone.

+ In your terminal window, run `make hello`. You will now be met with numerous errors! Placing the semicolon back in the correct position and running `make hello` again, the errors go away.

+ Notice also the special symbol `\n` in your code. Try removing those characters and *making* your program again by executing `make hello`. Typing `./hello` in the terminal window, how did your program change? This `\` character is called an *escape character* that tells the compiler that `\n` is a special instruction.

+ Restore your program to the following:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      printf("hello, world\n");
  }
  ```

  Notice the semicolon and `\n` have been restored.

+ The statement at the start of the code `#include <stdio.h>` is a very special command that tells the compile that you want to use the capabilities of a *library* called `stdio.h`, a *header file*. This allows you, among many other things, to utilize the `printf` function. You can read about all the capabilities of this library on the [Manual Pages](https://manual.cs50.io/). The Manual Pages provide a means by which to better understand what various commands do and how they function.

+ Libraries are collections of pre-written functions that others have written in the past that we can utilize in our code.

+ It turns out that CS50 has its own library called `cs50.h`. Let’s use this library in your program.

## Variables

+ Recall that in Scratch, we had the ability to ask the user “What’s your name?” and say “hello” with that name appended to it.

+ In C, we can do the same. Modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      string answer = get_string("What's your name? ");
      printf("hello, %s\n", answer);
  }
  ```

  The `get_string` function is used to get a string from the user. Then, the variable `answer` is passed to the `printf` function. `%s` tells the `printf` function to prepare itself to receive a `string`.

+ `answer` is a special holding place we call a *variable*. `answer` is of type `string` and can hold any string within it. There are many *data types*, such as `int`, `bool`, `char`, and many others.

+ `%s` is a placeholder called a *format code* that tells the `printf` function to prepare to receive a `string`. `answer` is the `string` being passed to `%s`.

+ Running `make hello` again in the terminal window, notice that numerous errors appear.

+ Looking at the errors `string` and `get_string` are not recognized by the compiler. We have to teach the compiler these features by adding a library called `cs50.h`:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string answer = get_string("What's your name? ");
      printf("hello, %s\n", answer);
  }
  ```

  Notice that `#include <cs50.h>` has been added to the top of your code.

+ Now running `make hello` again in the terminal window, you can run your program by typing `./hello`. The program now asks for your name and then says hello with your name attached, as intended.

+ `printf` allows for many format codes. Here is a noncomprehensive list of ones you may utilize in this course:

  `%s` is used for `string` variables. `%i` is used for `int` or integer variables. You can find out more about this on the [Manual Pages](https://manual.cs50.io/)

## Conditionals

+ Another building block you utilized within Scratch was that of *conditionals*. For example, you might want to do one thing if x is greater than y. Further, you might want to do something else if that condition is not met.

+ We look at a few examples from Scratch.

+ In C, you can assign a value to an `int` or integer as follows:

  Notice how a variable called `counter` of type `int` is assigned the value `0`.

+ C can also be programmed to add one to `counter` as follows:

  Notice how `1` is added to the value of `counter`.

+ This can be represented also as:

  Notice how `1` is added to the value of `counter`. However the `++` is used instead of `counter + 1`.

+ You can also subtract one from `counter` as follows:

  Notice how `1` is removed to the value of `counter`.

+ Using this new knowledge about how to assign values to variables, you can program your first conditional statement.

+ In the terminal window, type `code compare.c` and write code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      int x = get_int("What's x? ");
      int y = get_int("What's y? ");
  
      if (x < y)
      {
          printf("x is less than y\n");
      }
  }
  ```

  Notice that we create two variables, an `int` or integer called `x` and another called `y`. The values of these are populated using the `get_int` function.

+ You can run your code by executing `make compare` in the terminal window, followed by `./compare`. If you get any error messages, check your code for errors.

+ *Flow charts* are a way by which you can examine how a computer program functions. Such charts can be used to examine the efficiency of our code.

+ Looking at a flow chart of the above code, we can notice numerous shortcomings.

+ We can improve your program by coding as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      int x = get_int("What's x? ");
      int y = get_int("What's y? ");
  
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

  Notice that all potential outcomes are now accounted for.

+ You can re-make and re-run your program and test it out.

+ Examining this program on a flow chart, you can see the efficiency of our code design decisions.

+ Considering another data type called a `char` we can start a new program by typing `code agree.c` into the terminal window.

+ Where a `string` is a series of characters, a `char` is a single character.

+ In the text editor, write code as follows:

  ```auto
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

  Notice that single quotes are utilized for single characters. Further, notice that `==` ensure that something *is equal* to something else, where a single equal sign would have a very different function in C. Finally, notice that `||` effectively means *or*.

+ You can test your code by typing `make agree` into the terminal window, followed by `./agree`.

## Loops

+ We can also utilize the loops building block from Scratch in our C programs.

+ We look at a few examples from Scratch. Consider the following code:

  ```auto
  int counter = 3;
  while (counter > 0)
  {
      printf("meow\n");
      counter = counter - 1;
  }
  ```

  Notice that his code assigns the value of `3` to the `counter` variable. Then, the `while` loop says `meow` and removes one from the counter for each iteration. Once the counter is not greater than zero, the loop ends.

+ In your terminal window, type `code meow.c` and write code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      printf("meow\n");
      printf("meow\n");
      printf("meow\n");
  }
  ```

  Notice this does as intended but has an opportunity for better design.

+ We can improve our program by modifying your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      int i = 3;
      while (i > 0)
      {
          printf("meow\n");
          i--;
      }
  }
  ```

  Notice that we create an `int` called `i` and assign it the value `3`. Then, we create a `while` loop that will run as long as `i > 0`. Then, the loop runs. Every time `1` is subtracted to `i` using the `i--` statement.

+ Similarly, we can implement a count-up of sorts by modifying our code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      int i = 1;
      while (i <= 3)
      {
          printf("meow\n");
          i++;
      }
  }
  ```

  Notice how our counter `i` is started at `1`. Each time the loop runs, it will increment the counter by `1`. Once the counter is greater than `3`, it will stop the loop.

+ Generally, in computer science we count from zero. Best to revise your code as follows:

  ```auto
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

  Notice we now count from zero.

+ Another tool in our toolbox for looping is a `for` loop.

+ You can further improve the design of our `meow.c` program using a `for` loop. Modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      for (int i = 0; i < 3; i++)
      {
          printf("meow\n");
      }
  }
  ```

  Notice that the `for` loop includes three arguments. The first argument `int i = 0` starts our counter at zero. The second argument `i < 3` is the condition that is being checked. Finally, the argument `i++` tells the loop to increment by one each time the loop runs.

+ We can even loop forever using the following code:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      while (true)
      {
          printf("meow\n");
      }
  }
  ```

  Notice that `true` will always be the case. Therefore, the code will always run. You will lose control of your terminal window by running this code. You can break from an infinite by hitting `control-C` on your keyboard.

+ While we will provide much more guidance later, you can create your own function within C as follows:

  ```auto
  void meow(void)
  {
      printf("meow\n");
  }
  ```

  The initial `void` means that the function does not return any values. The `(void)` means that no values are being provided to the function.

+ This function can be used in the main function as follows:

  ```auto
  #include <stdio.h>
  
  void meow(void);
  
  int main(void)
  {
      for (int i = 0; i < 3; i++)
      {
          meow();
      }
  }
  
  void meow(void)
  {
      printf("meow\n");
  }
  ```

  Notice how the `meow` function is called with the `meow()` instruction. This is possible because the `meow` function is defined at the bottom of the code and the *prototype* of the function is provided at the top of the code as `void meow(void)`.

+ Your `meow` function can be further modified to accept input:

  ```auto
  #include <stdio.h>
  
  void meow(int n);
  
  int main(void)
  {
      meow(3);
  }
  
  // Meow some number of times
  void meow(int n)
  {
      for (int i = 0; i < n; i++)
      {
          printf("meow\n");
      }
  }
  ```

  Notice that the prototype has changed to `void meow(int n)` to show that `meow` accepts an `int` as its input.

## Operators and Abstraction

+ You can implement a calculator in C. In your terminal, type `code calculator.c` and write code as follows:

  ```auto
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

  Notice how the `get_int` function is utilized to obtain an integer from the user twice. One integer is stored in the `int` variable called `x`. Another is stored in the `int` variable called `y`. Then, the `printf` function prints the value of `x + y`, designated by the `%i` symbol.

+ *Operators* refer to the mathematical operations that are supported by your compiler. In C, these mathematical operators include:

  +   `+` for addition
  +   `-` for subtraction
  +   `*` for multiplication
  +   `/` for division
  +   `%` for remainder

+ *Abstraction* is the art of simplifying our code such that it deals with smaller and smaller problems.

+ Expanding on our previously acquired knowledge about functions, we could *abstract away* the addition into a function. Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int add(int a, int b);
  
  int main(void)
  {
      // Prompt user for x
      int x = get_int("x: ");
  
      // Prompt user for y
      int y = get_int("y: ");
  
      // Perform addition
      int z = add(x, y);
      printf("%i\n", z);
  }
  
  int add(int a, int b)
  {
      int c = a + b;
      return c;
  }
  ```

  Notice that the `add` function takes two variables as its input. These values are assigned to `a` and `b` and preforms a calculation, returning the value of `c`. Further, notice that the *scope* (or context in which variables exist) of `x` is the `main` function. The variable `c` is only within the scope of the `add` function.

+ The design of this program can be further improved as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int add(int a, int b);
  
  int main(void)
  {
      // Prompt user for x
      int x = get_int("x: ");
  
      // Prompt user for y
      int y = get_int("y: ");
  
      // Perform addition
      printf("%i\n", add(x, y));
  }
  
  int add(int a, int b)
  {
      return a + b;
  }
  ```

  Notice that `c` in the `add` function is removed entirely.

+ While very useful to be able to abstract away to an `add` function, you can also perform addition through *truncation* as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Prompt user for x
      long x = get_long("x: ");
  
      // Prompt user for y
      long y = get_long("y: ");
  
      // Perform addition
      printf("%li\n", x + y);
  }
  ```

  Notice that the addition is performed within the `printf` function.

+ Similarly, division can be performed as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Prompt user for x
      int x = get_int("x: ");
  
      // Prompt user for y
      int y = get_int("y: ");
  
      // Divide x by y
      printf("%i\n", x / y);
  }
  ```

  Notice that division is performed within the `printf` function.

## Linux and the Command Line

+   *Linux* is an operating system that is accessible via the command line in the terminal window in VS Code.
+   Some common command-line arguments we may use include:
    +   `cd`, for changing our current directory (folder)
    +   `cp`, for copying files and directories
    +   `ls`, for listing files in a directory
    +   `mkdir`, for making a directory
    +   `mv`, for moving (renaming) files and directories
    +   `rm`, for removing (deleting) files
    +   `rmdir`, for removing (deleting) directories
+   The most commonly used is `ls` which will list all the files in the current directory or directory. Go ahead and type `ls` into the terminal window and hit `enter`. You’ll see all the files in the current folder.
+   Another useful command is `mv`, where you can move a file from one file to another. For example, you could use this command to rename `Hello.c` (notice the uppercase `H`) to `hello.c` by typing `mv Hello.c hello.c`.
+   You can also create folders. You can type `mkdir pset1` to create a directory called `pset1`.
+   You can then use `cd pset1` to change your current directory to `pset1`.

## Mario

+ Everything we’ve discussed today has focused on various building-blocks of your work as an emerging computer scientist.

+ The following will help you orient toward working on a problem set for this class in general: How does one approach a computer science related problem?

+ Imagine we wanted to emulate the visual of the game Super Mario Bros. Considering the four question-blocks pictured, how could we create code that roughly represents these four horizontal blocks?

  ![Mario Question Marks](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week1Slide123.png "Mario Question Marks")

+ In the terminal window, type `code mario.c` and code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      for (int i = 0; i < 4; i++)
      {
          printf("?");
      }
      printf("\n");
  }
  ```

  Notice how four question marks are printed here using a loop.

+ Similarly, we can apply this same logic to be able to create three vertical blocks.

  ![Mario Blocks](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week1Slide125.png "Mario Blocks")

+ To accomplish this, modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      for (int i = 0; i < 3; i++)
      {
          printf("#\n");
      }
  }
  ```

  Notice how three vertical bricks are printed using a loop.

+ What if we wanted to combine these ideas to create a three-by-three group of blocks?

  ![Mario Grid](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week1Slide127.png "Mario Grid")

+ We can follow the logic above, combining the same ideas. Modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      for (int i = 0; i < 3; i++)
      {
          for (int j = 0; j < 3; j++)
          {
              printf("#");
          }
          printf("\n");
      }
  }
  ```

  Notice that one loop is inside another. The first loop defines what vertical row is being printed. For each row, three columns are printed. After each row, a new line is printed.

+ What if we wanted to ensure that the number of blocks to be *constant*, that is, unchangeable? Modify your code as follows:

  ```auto
  int main(void)
  {
      const int n = 3;
      for (int i = 0; i < n; i++)
      {
          for (int j = 0; j < n; j++)
          {
              printf("#");
          }
          printf("\n");
      }
  }
  ```

  Notice how `n` is now a constant. It can never be changed.

+ As illustrated earlier in this lecture, we can make our code prompt the user for the size of the grid. Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      int n = get_int("Size: ");
  
      for (int i = 0; i < n; i++)
      {
          for (int j = 0; j < n; j++)
          {
              printf("#");
          }
          printf("\n");
      }
  }
  ```

  Notice that `get_int` is used to prompt the user.

+ A general piece of advice within programming is that you should never fully trust your user. They will likely misbehave, typing incorrect values where they should not. We can protect our program from bad behavior by checking to make sure the user’s input satisfies our needs. Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      int n;
      do
      {
          n = get_int("Size: ");
      }
      while (n < 1);
  
      for (int i = 0; i < n; i++)
      {
          for (int j = 0; j < n; j++)
          {
              printf("#");
          }
          printf("\n");
      }
  }
  ```

  Notice how the user is continuously prompted for the size until the user’s input is 1 or greater.

## Comments

+ Comments are fundamental parts of a computer program, where you leave explanatory remarks to yourself and others that may be collaborating with you regarding your code.

+ All code you create for this course must include robust comments.

+ Typically each comment is a few words or more, providing the reader an opportunity to understand what is happening in a specific block of code. Further, such comments serve as a reminder for you later when you need to revise your code.

+ Comments involve placing `//` into your code, followed by a comment. Modify your code as follows to integrate comments:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Prompt user for positive integer
      int n;
      do
      {
          n = get_int("Size: ");
      }
      while (n < 1);
  
      // Print an n-by-n grid of bricks
      for (int i = 0; i < n; i++)
      {
          for (int j = 0; j < n; j++)
          {
              printf("#");
          }
          printf("\n");
      }
  }
  ```

  Notice how each comment begins with a `//`.

## Types

+   One of C’s shortcomings is the ease by which it managing memory. While C provides you immense control over how memory is utilized, programmers have to be very aware of potential pitfalls of memory management.
+   Types refer to the possible data that can be stored within a variable. For example, a `char` is designed to accommodate a single character like `a` or `2`.
+   Types are very important because each type has specific limits. For example, because of the limits in memory, the highest value of an `int` can be `4294967295`. If you attempt to count an `int` higher, *integer overflow* will result where an incorrect value will be stored in this variable.
+   The number of bits limits how high and low we can count.
+   Types with which you might interact during this course include:

    +   `bool`, a Boolean expression of either true or false
    +   `char`, a single character like a or 2
    +   `double`, a floating-point value with more digits than a float
    +   `float`, a floating-point value, or real number with a decimal value
    +   `int`, integers up to a certain size, or number of bits
    +   `long`, integers with more bits, so they can count higher than an int
    +   `string`, a string of characters
+   As you are coding, pay special attention to the types of variables you are using to avoid problems within your code.
+   We examined some examples of disasters that can occur through memory-related errors.

## Summing Up

In this lesson, you learned how to apply the building blocks you learned in Scratch to the C programming language. You learned…

+   How to create your first program in C.
+   Predefined functions that come natively with C and how to implement your own functions.
+   How to use variables, conditionals, and loops.
+   How to approach abstraction to simplify and improve your code.
+   How to approach problem-solving for a computer science problem.
+   How to use the Linux command line.
+   How to integrate comments into your code.
+   How to utilize types and operators.

See you next time!

+   


# Lecture 2-Arrays



+   [Welcome!](#welcome)
+   [Compiling](#compiling)
+   [Debugging](#debugging)
+   [Arrays](#arrays)
+   [Strings](#strings)
+   [String Length](#string-length)
+   [Command-Line Arguments](#command-line-arguments)
+   [Exit Status](#exit-status)
+   [Cryptography](#cryptography)
+   [Summing Up](#summing-up)

## Welcome!

+   In our previous session, we learned about C, a text-based programming language.
+   This week, we are going to take a deeper look at additional building-blocks that will support our goals of learning more about programming from the bottom up.
+   Fundamentally, in addition to the essentials of programming, this course is about problem-solving. Accordingly, we will also focus further on how to approach computer science problems.

## Compiling

+ *Encryption* is the act of hiding plain text from prying eyes. *decrypting*, then, is the act of taking an encrypted piece of text and returning it to a human-readable form.

+ An encrypted piece of text may look like the following:

  ![encryption](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide008-20240811152537859.png "encryption")

+ Recall that last week you learned about a *compiler*, a specialized computer program that converts *source code* into *machine code* that can be understood by a computer.

+ For example, you might have a computer program that looks like this:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      printf("hello, world\n");
  }
  ```

+ A compiler will take the above code and turn it into the following machine code:

  ![machine code](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide012.png "machine code")

+ *VS Code*, the programming environment provided to you as a CS50 student, utilizes a compiler called `clang` or *c language*.

+ If you were to type `make hello`, it runs a command that executes clang to create an output file that you can run as a user.

+ VS Code has been pre-programmed such that `make` will run numerous command line arguments along with clang for your convenience as a user.

+ Consider the following code:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string name = get_string("What's your name? ");
      printf("hello, %s\n", name);
  }
  ```

+ You can attempt to enter into the terminal window: `clang -o hello hello.c`. You will be met by an error that indicates that clang does not know where to find the `cs50.h` library.

+ Attempting again to compile this code, run the following command in the terminal window: `clang -o hello hello.c -lcs50`. This will enable the compiler to access the `cs50.h` library.

+ Running in the terminal window `./hello`, your program will run as intended.

+ While the above is offered as an illustration, such that you can understand more deeply the process and concept of compiling code, using `make` in CS50 is perfectly fine and the expectation!

+ Compiling involves major steps, including the following:

  + First, *preprocessing* is where the header files in your code, designated by a `#` (such as `#include <cs50.h>`) are effectively copied and pasted into your file. During this step, the code from `cs50.h` is copied into your program. Similarly, just as your code contains `#include <stdio.h>`, code contained within `stdio.h` somewhere on your computer is copied to your program. This step can be visualized as follows:

    ```auto
    string get_string(string prompt);
    int printf(string format, ...);
    
    int main(void)
    {
        string name = get_string("What's your name? ");
        printf("hello, %s\n", name);
    }
    ```

  + Second, *compiling* is where your program is converted into assembly code. This step can be visualized as follows:

    ![compiling](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide033-20240811152537979.png "compiling")

  + Third, *assembling* involves the compiler converting your assembly code into machine code. This step can be visualized as follows:

    ![assembling](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide038.png "assembling")

  + Finally, during the *linking* step, code from your included libraries are converted also into machine code and combined with your code. The final executable file is then outputted.

    ![linking](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide049.png "linking")

## Debugging

+ Everyone will make mistakes while coding.

+ Consider the following image from last week:

  ![mario](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide061.png "mario")

+ Further, consider the following code that has a bug purposely inserted within it:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      for (int i = 0; i <= 3; i++)
      {
          printf("#\n");
      }
  }
  ```

+ Type `code buggy0.c` into the terminal window and write the above code.

+ Running this code, four bricks appear instead of the intended three.

+ `printf` is a very useful way of debugging your code. You could modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      for (int i = 0; i <= 3; i++)
      {
          printf("i is %i\n", i);
          printf("#\n");
      }
  }
  ```

+ Running this code, you will see numerous statements, including `i is 0`, `i is 1`, `i is 2`, and `i is 3`. Seeing this, you might realize that Further code needs to be corrected as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      for (int i = 0; i < 3; i++)
      {
          printf("#\n");
      }
  }
  ```

  Notice the `<=` has been replaced with `<`.

+ This code can be further improved as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  void print_column(int height);
  
  int main(void)
  {
      int h = get_int("Height: ");
      print_column(h);
  }
  
  void print_column(int height)
  {
      for (int i = 0; i <= height; i++)
      {
          printf("#\n");
      }
  }
  ```

  Notice that compiling and running this code still results in a bug.

+ To address this bug, we will use a new tool at our disposal.

+ A second tool in debugging is called a *debugger*, a software tool created by programmers to help track down bugs in code.

+ In VS Code, a preconfigured debugger has been provided to you.

+ To utilize this debugger, first set a *breakpoint* by clicking to the left of a line of your code, just to the left of the line number. When you click there, you will see a red dot appearing. Imagine this as a stop sign, asking the compiler to pause such that you can consider what’s happening in this part of your code.

  ![break point](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Debugging.png "break point")

+ Second, run `debug50 ./buggy0`. You will notice that after the debugger comes to life that a line of your code will illuminate in a gold-like color. Quite literally, the code has *paused* at this line of code. Notice in the top left corner how all local variables are being displayed, including `h`, which has a current does not have a value. At the top of your window, you can click the `step over` button and it will keep moving through your code. Notice how the value of `h` increases.

+ While this tool will not show you where your bug is, it will help you slow down and see how your code is running step by step. You can use `step into` as a way to look further into the details of your buggy code.

+ A final form of debugging is called *rubber duck debugging*. When you are having challenges with your code, consider how speaking out loud to, quite literally, a rubber duck about the code problem. If you’d rather not talk to a small plastic duck, you are welcome to speak to a human near you! They need not understand how to program: Speaking with them is an opportunity for you to speak about your code.

## Arrays

+ In Week 0, we talked about *data types* such as `bool`, `int`, `char`, `string`, etc.

+ Each data type requires a certain amount of system resources:

  +   `bool` 1 byte
  +   `int` 4 bytes
  +   `long` 8 bytes
  +   `float` 4 bytes
  +   `double` 8 bytes
  +   `char` 1 byte
  +   `string` ? bytes

+ Inside of your computer, you have a finite amount of memory available.

  ![memory](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide084.png "memory")

+ Physically, on the memory of your computer, you can imagine how specific types of data are stored on your computer. You might imagine that a `char`, which only requires 1 byte of memory, may look as follows:

  ![1 byte](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide087.png "1 byte")

+ Similarly, an `int`, which requires 4 bytes might look as follows:

  ![4 bytes](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide088.png "4 bytes")

+ We can create a program that explores these concepts. Inside your terminal, type `code scores.c` and write code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      // Scores
      int score1 = 72;
      int score2 = 73;
      int score3 = 33;
  
      // Print average
      printf("Average: %f\n", (score1 + score2 + score3) / 3.0);
  }
  ```

  Notice that the number on the right is a floating point value of `3.0`, such that the calculation is rendered as a floating point value in the end.

+ Running `make scores`, the program runs.

+ You can imagine how these variables are stored in memory:

  ![scores in memory](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide098-20240811152539099.png "scores in memory")

+ *Arrays* are a way of storing data back-to-back in memory such that this data is easily accessible.

+ `int scores[3]` is a way of telling the compiler to provide you three back-to-back places in memory of size `int` to store three `scores`. Considering our program, you can revise your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Get scores
      int scores[3];
      scores[0] = get_int("Score: ");
      scores[1] = get_int("Score: ");
      scores[2] = get_int("Score: ");
  
      // Print average
      printf("Average: %f\n", (scores[0] + scores[1] + scores[2]) / 3.0);
  }
  ```

  Notice that `score[0]` examines the value at this location of memory by `indexing into` the array called `scores` at location `0` to see what value is stored there.

+ You can see how while the above code works, there is still an opportunity for improving our code. Revise your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Get scores
      int scores[3];
      for (int i = 0; i < 3; i++)
      {
          scores[i] = get_int("Score: ");
      }
  
      // Print average
      printf("Average: %f\n", (scores[0] + scores[1] + scores[2]) / 3.0);
  }
  ```

  Notice how we index into `scores` by using `scores[i]` where `i` is supplied by the `for` loop.

+ We can simplify or *abstract away* the calculation of the average. Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  // Constant
  const int N = 3;
  
  // Prototype
  float average(int length, int array[]);
  
  int main(void)
  {
      // Get scores
      int scores[N];
      for (int i = 0; i < N; i++)
      {
          scores[i] = get_int("Score: ");
      }
  
      // Print average
      printf("Average: %f\n", average(N, scores));
  }
  
  float average(int length, int array[])
  {
      // Calculate average
      int sum = 0;
      for (int i = 0; i < length; i++)
      {
          sum += array[i];
      }
      return sum / (float) length;
  }
  ```

  Notice that a new function called `average` is declared. Further, notice that a `const` or constant value of `N` is declared. Most importantly, notice how the `average` function takes `int array[]`, which means that the compiler passes an array to this function.

+ Not only can arrays be containers: They can be passed between functions.

## Strings

+ A `string` is simply an array of variables of type `char`: an array of characters.

+ Considering the following image, you can see how a string is an array of characters that begins with the first character and ends with a special character called a `NUL character`:

  ![hi with terminator](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide116-20240811152539394.png "hi with terminator")

+ Imagining this in decimal, your array would look like the following:

  ![hi with decimal](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide117-20240811152539457.png "hi with decimal")

+ Implementing this in your own code, type `code hi.c` in the terminal window and write code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      char c1 = 'H';
      char c2 = 'I';
      char c3 = '!';
  
      printf("%c%c%c\n", c1, c2, c3);
  }
  ```

  Notice that this will output a string of characters.

+ Similarly, make the following modification to your code:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      char c1 = 'H';
      char c2 = 'I';
      char c3 = '!';
  
      printf("%i %i %i\n", c1, c2, c3);
  }
  ```

  Notice that that ASCII codes are printed by replacing `%c` with `%i`.

+ To further understand how a `string` works, revise your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string s = "HI!";
      printf("%c%c%c\n", s[0], s[1], s[2]);
  }
  ```

  Notice how the `printf` statement presents three values from our array called `s`.

+ As before, we can replace `%c` with `%i` as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string s = "HI!";
      printf("%i %i %i %i\n", s[0], s[1], s[2], s[3]);
  }
  ```

  Notice that this prints the string’s ASCII codes, including NUL.

+ Let’s imagine we want to say both `HI!` and `BYE!`. Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string s = "HI!";
      string t = "BYE!";
  
      printf("%s\n", s);
      printf("%s\n", t);
  }
  ```

  Notice that two strings are declared and used in this example.

+ You can visualize this as follow:

  ![hi and bye](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide126-20240811152539241.png "hi and bye")

+ We can further improve this code. Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string words[2];
  
      words[0] = "HI!";
      words[1] = "BYE!";
  
      printf("%s\n", words[0]);
      printf("%s\n", words[1]);
  }
  ```

  Notice that both strings are stored within a single array of type `string`.

## String Length

+ A common problem within programming, and perhaps C more specifically, is to discover the length of an array. How could we implement this in code? Type `code length.c` in the terminal window and code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Prompt for user's name
      string name = get_string("Name: ");
  
      // Count number of characters up until '\0' (aka NUL)
      int n = 0;
      while (name[n] != '\0')
      {
          n++;
      }
      printf("%i\n", n);
  }
  ```

  Notice that this code loops until the `NUL` character is found.

+ This code can ben improved by abstracting away the counting as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int string_length(string s);
  
  int main(void)
  {
      // Prompt for user's name
      string name = get_string("Name: ");
      int length = string_length(name);
      printf("%i\n", length);
  }
  
  int string_length(string s)
  {
      // Count number of characters up until '\0' (aka NUL)
      int n = 0;
      while (s[n] != '\0')
      {
          n++;
      }
      return n;
  }
  ```

+ Since this is such a common problem within programming, other programmers have created code in the `string.h` library to find the length of a string. You can find the length of a string by modifying your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      // Prompt for user's name
      string name = get_string("Name: ");
      int length = strlen(name);
      printf("%i\n", length);
  }
  ```

  Notice that this code uses the `string.h` library, declared at the top of the file. Further, it uses a function from that library called `strlen`, which calculates the length of the string passed to it.

+ `ctype.h` is another library that is quite useful. Imagine we wanted to create a program that converted all lowercase characters to uppercase ones. In the terminal window type `code uppercase.c` and write code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      string s = get_string("Before: ");
      printf("After:  ");
      for (int i = 0, n = strlen(s); i < n; i++)
      {
          if (s[i] >= 'a' && s[i] <= 'z')
          {
              printf("%c", s[i] - 32);
          }
          else
          {
              printf("%c", s[i]);
          }
      }
      printf("\n");
  }
  ```

  Notice that this code *iterates* through each value in the string. The program looks at each character. If the character is lowercase, it subtracts the value 32 from it to convert it to uppercase.

+ Recalling our previous work from last week, you might remember this ASCII values chart:

  ![ascii](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide120.png "ascii")

+ When a lowercase character has `32` subtracted from it, it results in an uppercase version of that same character.

+ While the program does what we want, there is an easier way using the `ctype.h` library. Modify your program as follows:

  ```auto
  #include <cs50.h>
  #include <ctype.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      string s = get_string("Before: ");
      printf("After:  ");
      for (int i = 0, n = strlen(s); i < n; i++)
      {
          if (islower(s[i]))
          {
              printf("%c", toupper(s[i]));
          }
          else
          {
              printf("%c", s[i]);
          }
      }
      printf("\n");
  }
  ```

  Notice that the program iterates through each character of the string. The `toupper` function is passed `s[i]`. Each character (if lowercase) is converted to uppercase.

+ It’s worth mentioning that `toupper` automatically knows to uppercase only lowercase characters. Hence, your code can be simplified as follows:

  ```auto
  #include <cs50.h>
  #include <ctype.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      string s = get_string("Before: ");
      printf("After:  ");
      for (int i = 0, n = strlen(s); i < n; i++)
      {
          printf("%c", toupper(s[i]));
      }
      printf("\n");
  }
  ```

  Notice that this code uppercases a string using the `ctype` library.

+ You can read about all the capabilities of the `ctype` library on the [Manual Pages](https://manual.cs50.io/#ctype.h).

## Command-Line Arguments

+ `Command-line arguments` are those arguments that are passed to your program at the command line. For example, all those statements you typed after `clang` are considered command line arguments. You can use these arguments in your own programs!

+ In your terminal window, type `code greet.c` and write code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string answer = get_string("What's your name? ");
      printf("hello, %s\n", answer);
  }
  ```

  Notice that this says `hello` to the user.

+ Still, would it not be nice to be able to take arguments before the program even runs? Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(int argc, string argv[])
  {
      if (argc == 2)
      {
          printf("hello, %s\n", argv[1]);
      }
      else
      {
          printf("hello, world\n");
      }
  }
  ```

  Notice that this program knows both `argc`, the number of command line arguments, and `argv` which is an array of the characters passed as arguments at the command line.

+ Therefore, using the syntax of this program, executing `./greet David` would result in the program saying `hello, David`.

## Exit Status

+ When a program ends, a special exit code is provided to the computer.

+ When a program exits without error, a status code of `0` is provided the computer. Often, when an error occurs that results in the program ending, a status of `1` is provided by the computer.

+ You could write a program as follows that illustrates this by typing `code status.c` and writing code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(int argc, string argv[])
  {
      if (argc != 2)
      {
          printf("Missing command-line argument\n");
          return 1;
      }
      printf("hello, %s\n", argv[1]);
      return 0;
  }
  ```

  Notice that if you fail to provide `./status David`, you will get an exit status of `1`. However, if you do provide `./status David`, you will get an exit status of `0`.

+ You can imagine how you might use portions of the above program to check if a user provided the correct number of command-line arguments.

## Cryptography

+ Cryptography is the art of ciphering and deciphering a message.

+ `plaintext` and a `key` are provided to a `cipher`, resulting in ciphered text.

  ![cryptography](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week2Slide153.png "cryptography")

+ The key is a special argument passed to the cipher along with the plaintext. The cipher uses the key to make decisions about how to implement its cipher algorithm.

## Summing Up

In this lesson, you learned more details about compiling and how data is stored within a computer. Specifically, you learned…

+   Generally, how a compiler works.
+   How to debug your code using four methods.
+   How to utilize arrays within your code.
+   How arrays store data in back to back portions of memory.
+   How strings are simply arrays of characters.
+   How to interact with arrays in your code.
+   How command-line arguments can be passed to your programs.
+   The basic building-blocks of cryptography.

See you next time!


# Lecture 3-Algorithms



+   [Welcome!](#welcome)
+   [Linear Search](#linear-search)
+   [Binary Search](#binary-search)
+   [Running Time](#running-time)
+   [search.c](#searchc)
+   [Data Structures](#data-structures)
+   [Sorting](#sorting)
+   [Bubble Sort](#bubble-sort)
+   [Recursion](#recursion)
+   [Merge Sort](#merge-sort)
+   [Summing Up](#summing-up)

## Welcome!

+ In week zero, we introduced the idea of an *algorithm*: a black box that may take an input and creates an output.

+ This week, we are going to expand upon our understanding of algorithms through pseudocode and into code itself.

+ Also, we are going to consider the efficiency of these algorithms. Indeed, we are going to be building upon our understanding of how to use some of the *lower-level* concepts we discussed last week in building algorithms.

+ Recall back to earlier in the course when we introduced the following graph:

  ![chart with: "size of problem" as x-axis; "time to solve" as y-axis; red, steep straight line from origin to top of graph close to yellow, less steep straight line from origin to top of graph both labeled "n"; green, curved line that gets less and less steep from origin to right of graph labeled "log n)](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week3Slide010.png "complexity")

+ As we step into this week, you should consider how the way an algorithm works with a problem may determine the time it takes to solve a problem! Algorithms can be designed to be more and more efficient, to a limit.

+ Today, we will focus upon the design of algorithms and how to measure their efficiency.

## Linear Search

+ Recall that last week you were introduced to the idea of an *array*, blocks of memory that are consecutive: side-by-side with one another.

+ You can metaphorically imagine an array like a series of seven red lockers as follows:

  ![Seven red lockers side by side](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week3Slide018-20240811153957551.png "lockers")

+ We can imagine that we have an essential problem of wanting to know, “Is the number 50 inside an array?” A computer must look at each locker to be able to see if the number 50 is inside. We call this process of finding such a number, character, string, or other item *searching*.

+ We can potentially hand our array to an algorithm, wherein our algorithm will search through our lockers to see if the number 50 is behind one of the doors: Returning the value true or false.

  ![seven red lockers pointing to an empty box. Out of the empty box comes and output of bool](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week3Slide022-20240811153957279.png "lockers as algorithm")

+ We can imagine various instructions we might provide our algorithm to undertake this task as follows:

  ```auto
  For each door from left to right
      If 50 is behind door
          Return true
  Return false
  ```

  Notice that the above instructions are called *pseudocode*: A human-readable version of the instructions that we could provide the computer.

+ A computer scientist could translate that pseudocode as follows:

  ```auto
  For i from 0 to n-1
      If 50 is behind doors[i]
          Return true
  Return false
  ```

  Notice that the above is still not code, but it is a pretty close approximation of what the final code might look like.

## Binary Search

+ *Binary search* is another *search algorithm* that could be employed in our task of finding the 50.

+ Assuming that the values within the lockers have been arranged from smallest to largest, the pseudocode for binary search would appear as follows:

  ```auto
  If no doors left
      Return false
  If 50 is behind middle door
      Return true
  Else if 50 < middle door
      Search left half
  Else if 50 > middle door
      Search right half
  ```

+ Using the nomenclature of code, we can further modify our algorithm as follows:

  ```auto
  If no doors left
      Return false
  If 50 is behind doors[middle]
      Return true
  Else if 50 < doors[middle]
      Search doors[0] through doors[middle - 1]
  Else if 50 > doors[middle]
      Search doors[middle + 1] through doors[n - 1]
  ```

  Notice, looking at this approximation of code, you can nearly imagine what this might look like in actual code.

## Running Time

+ *running time* involves an analysis using *big O* notation. Take a look at the following graph:

  ![chart with: "size of problem" as x-axis; "time to solve" as y-axis; red, steep straight line from origin to top of graph close to yellow, less steep straight line from origin to top of graph both labeled "O(n)"; green, curved line that gets less and less steep from origin to right of graph labeled "O(log n)](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week3Slide042.png "big o graphed")

+ Rather than being ultra-specific about the mathematical efficiency of an algorithm, computer scientists discuss efficiency in terms of *the order of* various running times.

+ In the above graph, the first algorithm is \\(O(n)\\) or *in the order of n*. The second is in \\(O(n)\\) as well. The third is in \\(O(\\log n)\\).

+ It’s the shape of the curve that shows the efficiency of an algorithm. Some common running times we may see are:

  +   \\(O(n^2)\\)
  +   \\(O(n \\log n)\\)
  +   \\(O(n)\\)
  +   \\(O(\\log n)\\)
  +   \\(O(1)\\)

+ Of the running times above, \\(O(n^2)\\) is considered the worst running time, \\(O(1)\\) is the fastest.

+ Linear search was of order \\(O(n)\\) because it could take *n* steps in the worst case to run.

+ Binary search was of order \\(O(\\log n)\\) because it would take fewer and fewer steps to run even in the worst case.

+ Programmers are interested in both the worst case, or *upper bound*, and the best case, or *lower bound*.

+ The \\(\\Omega\\) symbol is used to denote the best case of an algorithm, such as \\(\\Omega(\\log n)\\).

+ The \\(\\Theta\\) symbol is used to denote where the upper bound and lower bound are the same, where the best case and the worst case running times are the same.

+ As you continue to develop your knowledge in computer science, you will explore these topics in more detail in future courses.

## search.c

+ You can implement linear search ourselves by typing `code search.c` in your terminal window and by writing code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // An array of integers
      int numbers[] = {20, 500, 10, 5, 100, 1, 50};
  
      // Search for number
      int n = get_int("Number: ");
      for (int i = 0; i < 7; i++)
      {
          if (numbers[i] == n)
          {
              printf("Found\n");
              return 0;
          }
      }
      printf("Not found\n");
      return 1;
  }
  ```

  Notice that the line beginning with `int numbers[]` allows us to define the values of each element of the array as we create it. Then, in the `for` loop, we have an implementation of linear search. `return 0` is used to indicate success and exit the program. `return 1` is used to exist the program with an error (failure).

+ We have now implemented linear search ourselves in C!

+ What if we wanted to search for a string within an array? Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      // An array of strings
      string strings[] = {"battleship", "boot", "cannon", "iron", "thimble", "top hat"};
  
      // Search for string
      string s = get_string("String: ");
      for (int i = 0; i < 6; i++)
      {
          if (strcmp(strings[i], s) == 0)
          {
              printf("Found\n");
              return 0;
          }
      }
      printf("Not found\n");
      return 1;
  }
  ```

  Notice that we cannot utilize `==` as in our previous iteration of this program. Instead, we use `strcmp`, which comes from the `string.h` library. `strcmp` will return `0` if the strings are the same.

+ Indeed, running this code allows us to iterate over this array of strings to see if a certain string was within it. However, if you see a *segmentation fault*, where a part of memory was touched by your program that it should not have access to, do make sure you have `i < 6` noted above instead of `i < 7`.

+ We can combine these ideas of both numbers and strings into a single program. Type `code phonebook.c` into your terminal window and write code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      // Arrays of strings
      string names[] = {"Carter", "David", "John"};
      string numbers[] = {"+1-617-495-1000", "+1-617-495-1000", "+1-949-468-2750"};
  
      // Search for name
      string name = get_string("Name: ");
      for (int i = 0; i < 3; i++)
      {
          if (strcmp(names[i], name) == 0)
          {
              printf("Found %s\n", numbers[i]);
              return 0;
          }
      }
      printf("Not found\n");
      return 1;
  }
  ```

  Notice that Carter’s number begins with `+1-617`, David’s phone number starts with `+1-617`, and John’s number starts with `+1-949`. Therefore, `names[0]` is Carter and `numbers[0]` is Carter’s number. This code will allow us to search the phonebook to for a person’s specific number.

+ While this code works, there are numerous inefficiencies. Indeed, there is a chance that people’s names and numbers may not correspond. Wouldn’t be nice if we could create our own data type where we could associate a person with the phone number?

## Data Structures

+ It turns out that C allows a way by which we can create our own data types via a `struct`.

+ Would it not be useful to create our own data type called a `person`, that has inside of it a `name` and `number`.

+ Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  #include <string.h>
  
  typedef struct
  {
      string name;
      string number;
  }
  person;
  
  int main(void)
  {
      person people[3];
  
      people[0].name = "Carter";
      people[0].number = "+1-617-495-1000";
  
      people[1].name = "David";
      people[1].number = "+1-617-495-1000";
  
      people[2].name = "John";
      people[2].number = "+1-949-468-2750";
  
      // Search for name
      string name = get_string("Name: ");
      for (int i = 0; i < 3; i++)
      {
          if (strcmp(people[i].name, name) == 0)
          {
              printf("Found %s\n", people[i].number);
              return 0;
          }
      }
      printf("Not found\n");
      return 1;
  }
  ```

  Notice that the code begins with `typedef struct` where a new datatype called `person` is defined. Inside a `person` is a string called `name` and a `string` called number. In the `main` function, begin by creating an array called `people` that is of type `person` that is a size of 3. Then, we update the names and phone numbers of the two people in our `people` array. Most important, notice how the *dot notation* such as `people[0].name` allows us to access the `person` at the 0th location and assign that individual a name.

## Sorting

+ *Sorting* is the act of taking an unsorted list of values and transforming this list into a sorted one.

+ When a list is sorted, searching that list is far less taxing on the computer. Recall that we can use binary search on a sorted list, but not on an unsorted one.

+ It turns out that there are many different types of sorting algorithms.

+ *Selection sort* is one such search algorithm.

+ We can represent an array as follows:

  ![Seven red lockers side by side with the last labeled as n-1](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week3Slide104-20240811153957751.png "red lockers")

+ The algorithm for selection sort in pseudocode is:

  ```auto
  For i from 0 to n–1
      Find smallest number between numbers[i] and numbers[n-1]
      Swap smallest number with numbers[i]
  ```

+ Summarizing those steps, the first time iterating through the list took `n - 1` steps. The second time, it took `n - 2` steps. Carrying this logic forward, the steps required could be represented as follows:

  ```auto
  (n - 1) + (n - 2) + (n - 3) + ... + 1
  ```

+ This could be simplified to n(n-1)/2 or, more simply, \\(O(n^2)\\).

## Bubble Sort

+ *Bubble sort* is another sorting algorithm that works by repeatedly swapping elements to “bubble” larger elements to the end.

+ The pseudocode for bubble sort is:

  ```auto
  Repeat n-1 times
      For i from 0 to n–2
          If numbers[i] and numbers[i+1] out of order
              Swap them
      If no swaps
          Quit
  ```

+ As we further sort the array, we know more and more of it becomes sorted, so we only need to look at the pairs of numbers that haven’t been sorted yet.

+ Analyzing selection sort, we made only seven comparisons. Representing this mathematically, where *n* represents the number of cases, it could be said that selection sort can be analyzed as:

  ```auto
    (n - 1) + (n - 2) + (n - 3) + ... + 1
  ```

  or, more simply \\(n^2/2 - n/2\\).

+ Considering that mathematical analysis, n2 is really the most influential factor in determining the efficiency of this algorithm. Therefore, selection sort is considered to be of the order of \\(O(n^2)\\) in the worst case where all values are unsorted. Even when all values are sorted, it will take the same number of steps. Therefore, the best case can be noted as \\(\\Omega(n^2)\\). Since both the upper bound and lower bound cases are the same, the efficiency of this algorithm as a whole can be regarded as \\(\\Theta(n^2)\\).

+ Analyzing bubble sort, the worst case is \\(O(n^2)\\). The best case is \\(\\Omega(n)\\).

+ You can [visualize](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html) a comparison of these algorithms.

## Recursion

+ How could we improve our efficiency in our sorting?

+ *Recursion* is a concept within programming where a function calls itself. We saw this earlier when we saw…

  ```auto
  If no doors left
      Return false
  If number behind middle door
      Return true
  Else if number < middle door
      Search left half
  Else if number > middle door
      Search right half
  ```

  Notice that we are calling `search` on smaller and smaller iterations of this problem.

+ Similarly, in our pseudocode for Week 0, you can see where recursion was implemented:

  ```auto
  1  Pick up phone book
  2  Open to middle of phone book
  3  Look at page
  4  If person is on page
  5      Call person
  6  Else if person is earlier in book
  7      Open to middle of left half of book
  8      Go back to line 3
  9  Else if person is later in book
  10     Open to middle of right half of book
  11     Go back to line 3
  12 Else
  13     Quit
  ```

+ This code could have been simplified, to highlight its recursive properties as follows:

  ```auto
  1  Pick up phone book
  2  Open to middle of phone book
  3  Look at page
  4  If person is on page
  5      Call person
  6  Else if person is earlier in book
  7      Search left half of book
  9  Else if person is later in book
  10     Search right half of book
  12 Else
  13     Quit
  ```

+ Consider how in Week 1 we wanted to create a pyramid structure as follows:

+ To implement this using recursion, type `code recursion.c` into your terminal window and write code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  void draw(int n);
  
  int main(void)
  {
      draw(1);
  }
  
  void draw(int n)
  {
      for (int i = 0; i < n; i++)
      {
          printf("#");
      }
      printf("\n");
  
      draw(n + 1);
  }
  ```

  Notice that the draw function calls itself. Further, note that your code may get caught in an infinite loop. To break from this loop, if you get stuck, hit `ctrl-c` on your keyboard. The reason this creates an infinite loop is that there is nothing telling the program to end. There is no case where the program is done.

+ We can correct our code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  void draw(int n);
  
  int main(void)
  {
      // Get height of pyramid
      int height = get_int("Height: ");
  
      // Draw pyramid
      draw(height);
  }
  
  void draw(int n)
  {
      // If nothing to draw
      if (n <= 0)
      {
          return;
      }
  
      // Draw pyramid of height n - 1
      draw(n - 1);
  
      // Draw one more row of width n
      for (int i = 0; i < n; i++)
      {
          printf("#");
      }
      printf("\n");
  }
  ```

  Notice the *base case* will ensure the code does not run forever. The line `if (n <= 0)` terminates the recursion because the problem has been solved. Every time `draw` calls itself, it calls itself by `n-1`. At some point, `n-1` will equal `0`, resulting in the `draw` function returning and the program will end.

## Merge Sort

+ We can now leverage recursion in our quest for a more efficient sort algorithm and implement what is called *merge sort*, a very efficient sort algorithm.

+ The pseudocode for merge sort is quite short:

  ```auto
  If only one number
      Quit
  Else
      Sort left half of number
      Sort right half of number
      Merge sorted halves
  ```

+ Consider the following list of numbers:

+ First, merge sort asks, “is this one number?” The answer is “no,” so the algorithm continues.

+ Second, merge sort will now split the numbers down the middle (or as close as it can get) and sort the left half of numbers.

+ Third, merge sort would look at these numbers on the left and ask, “is this one number?” Since the answer is no, it would then split the numbers on the left down the middle.

+ Fourth, merge sort will again ask , “is this one number?” The answer is yes this time! Therefore, it will quit this task and return to the last task it was running at this point:

+ Fifth, merge sort will sort the numbers on the left.

+ Now, we return to where we left off in the pseudocode now that the left side has been sorted. A similar process of steps 3-5 will occur with the right-hand numbers. This will result in:

+ Both halves are now sorted. Finally, the algorithm will merge both sides. It will look at the first number on the left and the first number on the right. It will put the smaller number first, then the second smallest. The algorithm will repeat this for all numbers, resulting in:

+ Merge sort is complete, and the program quits.

+ Merge sort is a very efficient sort algorithm with a worst case of \\(O(n \\log n)\\). The best case is still \\(\\Omega(n \\log n)\\) because the algorithm still must visit each place in the list. Therefore, merge sort is also \\(\\Theta(n \\log n)\\) since the best case and worst case are the same.

+ A final [visualization](https://www.youtube.com/watch?v=ZZuD6iUe3Pc) was shared.

## Summing Up

In this lesson, you learned about algorithmic thinking and building your own data types. Specifically, you learned…

+   Algorithms.
+   Big *O* notation.
+   Binary search and linear search.
+   Various sort algorithms, including bubble sort, selection sort, and merge sort.
+   Recursion.

See you next time!


# Lecture 4-Memory



+   [Welcome!](#welcome)
+   [Pixel Art](#pixel-art)
+   [Hexadecimal](#hexadecimal)
+   [Memory](#memory)
+   [Pointers](#pointers)
+   [Strings](#strings)
+   [Pointer Arithmetic](#pointer-arithmetic)
+   [String Comparison](#string-comparison)
+   [Copying](#copying)
+   [malloc and Valgrind](#malloc-and-valgrind)
+   [Garbage Values](#garbage-values)
+   [Pointer Fun with Binky](#pointer-fun-with-binky)
+   [Swap](#swap)
+   [Overflow](#overflow)
+   [`scanf`](#scanf)
+   [File I/O](#file-io)
+   [Summing Up](#summing-up)

## Welcome!

+   In previous weeks, we talked about images being made of smaller building blocks called pixels.
+   Today, we will go into further detail about the zeros and ones that make up these images. In particular, we will be going deeper into the fundamental building blocks that make up files, including images.
+   Further, we will discuss how to access the underlying data stored in computer memory.

## Pixel Art

+ Pixels are squares, individual dots, of color that are arranged on an up-down, left-right grid.

+ You can imagine as an image as a map of bits, where zeros represent black and ones represent white.

  ![Zeros and ones being converted to a black and white smiley](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide015.png "smiley")

+ *RGB*, or *red, green, blue*, are numbers that represent the amount of each of these colors. In Adobe Photoshop, you can see these settings as follows:

  ![A photoshop panel with RGB values and hexidecimal input](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide016.png "hex in photoshop")

  Notice how the amount of red, blue, and green changes the color selected.

+ You can see by the image above that color is not just represented in three values. At the bottom of the window, there is a special value made up of numbers and characters. `255` is represented as `FF`. Why might this be?

## Hexadecimal

+ *Hexadecimal* is a system of counting that has 16 counting values. They are as follows:

  ```auto
    0 1 2 3 4 5 6 7 8 9 a b c d e f
  ```

  Notice that `F` represents `15`.

+ Hexadecimal is also known as *base-16*.

+ When counting in hexadecimal, each column is a power of 16.

+ The number `0` is represented as `00`.

+ The number `1` is represented as `01`.

+ The number `9` is represented by `09`.

+ The number `10` is represented as `0A`.

+ The number `15` is represented as `0F`.

+ The number `16` is represented as `10`.

+ The number `255` is represented as `FF`, because 16 x 15 (or `F`) is 240. Add 15 more to make 255. This is the highest number you can count using a two-digit hexadecimal system.

+ Hexadecimal is useful because it can be represented using fewer digits. Hexadecimal allows us to represent information more succinctly.

## Memory

+ In weeks past, you may recall our artist rendering of concurrent blocks of memory. Applying hexadecimal numbering to each of these blocks of memory, you can visualize these as follows:

  ![Blocks of memory numbered in hex](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide065-20240811154040385.png "memory hex")

+ You can imagine how there may be confusion regarding whether the `10` block above may represent a location in memory or the value `10`. Accordingly, by convention, all hexadecimal numbers are often represented with the `0x` prefix as follows:

  ![blocks of memory numbered in hex with 0x](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide066.png "0x")

+ In your terminal window, type `code addresses.c` and write your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      int n = 50;
      printf("%i\n", n);
  }
  ```

  Notice how `n` is stored in memory with the value `50`.

+ You can visualize how this program stores this value as follows:

  ![the value 50 stored in a memory location with hex](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide070-20240811154041145.png "hex")

+ The `C` language has two powerful operators that relate to memory:

  ```auto
    & Provides the address of something stored in memory.
    * Instructs the compiler to go to a location in memory.
  ```

+ We can leverage this knowledge by modifying our code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      int n = 50;
      printf("%p\n", &n);
  }
  ```

  Notice the `%p`, which allows us to view the address of a location in memory. `&n` can be literally translated as “the address of `n`.” Executing this code will return an address of memory beginning with `0x`.

## Pointers

+ A *pointer* is a variable that contains the address of some value. Most succinctly, a pointer is an address in your computer’s memory.

+ Consider the following code:

  Notice that `p` is a pointer that contains the address of an integer `n`.

+ Modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      int n = 50;
      int *p = &n;
      printf("%p\n", p);
  }
  ```

  Notice that this code has the same effect as our previous code. We have simply leveraged our new knowledge of the `&` and `*` operators.

+ To illustrate the use of the `*` operator, consider the following:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      int n = 50;
      int *p = &n;
      printf("%i\n", *p);
  }
  ```

  Notice that the `printf` line prints the integer at the location of `p`. `int *p` creates a pointer whose job is to store the memory address of an integer.

+ You can visualize our code as follows:

  ![Same value of 50 in a memory location with a pointer value stored elsewhere](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide078.png "pointer")

  Notice the pointer seems rather large. Indeed, a pointer is usually stored as an 8-byte value. `p` is storing the address of the `50`.

+ You can more accurately visualize a pointer as one address that points to another:

  ![A pointer as an arrow, pointing from one location of memory to another](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide079-20240811154040656.png "pointer")

## Strings

+ Now that we have a mental model for pointers, we can peel back a level of simplification that was offered earlier in this course.

+ Recall that a string is simply an array of characters. For example, `string s = "HI!"` can be represented as follows:

  ![The string HI with an exclaimation point stored in memory](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide085-20240811154041039.png "hi")

+ However, what is `s` really? Where is the `s` stored in memory? As you can imagine, `s` needs to be stored somewhere. You can visualize the relationship of `s` to the string as follows:

  ![Same string HI with a pointer pointing to it](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide086-20240811154040698.png "hi pointer")

  Notice how a pointer called `s` tells the compiler where the first byte of the string exists in memory.

+ Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      string s = "HI!";
      printf("%p\n", s);
      printf("%p\n", &s[0]);
      printf("%p\n", &s[1]);
      printf("%p\n", &s[2]);
      printf("%p\n", &s[3]);
  }
  ```

  Notice the above prints the memory locations of each character in the string `s`. The `&` symbol is used to show the address of each element of the string. When running this code, notice that elements `0`, `1`, `2`, and `3` are next to one another in memory.

+ Likewise, you can modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      char *s = "HI!";
      printf("%s\n", s);
  }
  ```

  Notice that this code will present the string that starts at the location of `s`. This code effectively removes the training wheels of the `string` data type offered by `cs50.h`. This is raw C code, without the scaffolding of the cs50 library.

+ You can imagine how a string, as a data type, is created.

+ Last week, we learned how to create your own data type as a struct.

+ The cs50 library includes a struct as follows: `typedef char *string`

+ This struct, when using the cs50 library, allows one to use a custom data type called `string`.

## Pointer Arithmetic

+ You can modify your code to accomplish the same thing in a longer form as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      char *s = "HI!";
      printf("%c\n", s[0]);
      printf("%c\n", s[1]);
      printf("%c\n", s[2]);
  }
  ```

  Notice that we are printing each character at the location of `s`.

+ Further, you can modify your code as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      char *s = "HI!";
      printf("%c\n", *s);
      printf("%c\n", *(s + 1));
      printf("%c\n", *(s + 2));
  }
  ```

  Notice that the first character at the location of `s` is printed. Then, the character at the location `s + 1` is printed, and so on.

## String Comparison

+ A string of characters is simply an array of characters identified by its first byte.

+ Earlier in the course, we considered the comparison of integers. We could represent this in code by typing `code compare.c` into the terminal window and writing code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Get two integers
      int i = get_int("i: ");
      int j = get_int("j: ");
  
      // Compare integers
      if (i == j)
      {
          printf("Same\n");
      }
      else
      {
          printf("Different\n");
      }
  }
  ```

  Notice that this code takes two integers from the user and compares them.

+ In the case of strings, however, one cannot compare two strings using the `==` operator.

+ Utilizing the `==` operator in an attempt to compare strings will attempt to compare the memory locations of the strings instead of the characters therein. Accordingly, we recommended the use of `strcmp`.

+ To illustrate this, modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Get two strings
      char *s = get_string("s: ");
      char *t = get_string("t: ");
  
      // Compare strings' addresses
      if (s == t)
      {
          printf("Same\n");
      }
      else
      {
          printf("Different\n");
      }
  }
  ```

  Noticing that typing in `HI!` for both strings still results in the output of `Different`.

+ Why are these strings seemingly different? You can use the following to visualize why:

  ![two strings stored separately in memory](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide115-20240811154041212.png "two strings")

+ Therefore, the code for `compare.c` above is actually attempting to see if the memory addresses are different: not the strings themselves.

+ Using `strcmp`, we can correct our code:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      // Get two strings
      char *s = get_string("s: ");
      char *t = get_string("t: ");
  
      // Compare strings
      if (strcmp(s, t) == 0)
      {
          printf("Same\n");
      }
      else
      {
          printf("Different\n");
      }
  }
  ```

  Notice that `strcmp` can return `0` if the strings are the same.

+ To further illustrate how these two strings are living in two locations, modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Get two strings
      char *s = get_string("s: ");
      char *t = get_string("t: ");
  
      // Print strings
      printf("%s\n", s);
      printf("%s\n", t);
  }
  ```

  Notice how we now have two separate strings stored likely at two separate locations.

+ You can see the locations of these two stored strings with a small modification:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  
  int main(void)
  {
      // Get two strings
      char *s = get_string("s: ");
      char *t = get_string("t: ");
  
      // Print strings' addresses
      printf("%p\n", s);
      printf("%p\n", t);
  }
  ```

  Notice that the `%s` has been changed to `%p` in the print statement.

## Copying

+ A common need in programming is to copy one string to another.

+ In your terminal window, type `code copy.c` and write code as follows:

  ```auto
  #include <cs50.h>
  #include <ctype.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      // Get a string
      string s = get_string("s: ");
  
      // Copy string's address
      string t = s;
  
      // Capitalize first letter in string
      t[0] = toupper(t[0]);
  
      // Print string twice
      printf("s: %s\n", s);
      printf("t: %s\n", t);
  }
  ```

  Notice that `string t = s` copies the address of `s` to `t`. This does not accomplish what we are desiring. The string is not copied – only the address is.

+ You can visualize the above code as follows:

  ![two pointers pointing at the same memory location with a string](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide124-20240811154041360.png "two strings")

  Notice that `s` and `t` are still pointing at the same blocks of memory. This is not an authentic copy of a string. Instead, these are two pointers pointing at the same string.

+ Before we address this challenge, it’s important to ensure that we don’t experience a *segmentation fault* through our code, where we attempt to copy `string s` to `string t`, where `string t` does not exist. We can employ the `strlen` function as follows to assist with that:

  ```auto
  #include <cs50.h>
  #include <ctype.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      // Get a string
      string s = get_string("s: ");
  
      // Copy string's address
      string t = s;
  
      // Capitalize first letter in string
      if (strlen(t) > 0)
      {
          t[0] = toupper(t[0]);
      }
  
      // Print string twice
      printf("s: %s\n", s);
      printf("t: %s\n", t);
  }
  ```

  Notice that `strlen` is used to make sure `string t` exists. If it does not, nothing will be copied.

+ To be able to make an authentic copy of the string, we will need to introduce two new building blocks. First, `malloc` allows you, the programmer, to allocate a block of a specific size of memory. Second, `free` allows you to tell the compiler to *free up* that block of memory you previously allocated.

+ We can modify our code to create an authentic copy of our string as follows:

  ```auto
  #include <cs50.h>
  #include <ctype.h>
  #include <stdio.h>
  #include <stdlib.h>
  #include <string.h>
  
  int main(void)
  {
      // Get a string
      char *s = get_string("s: ");
  
      // Allocate memory for another string
      char *t = malloc(strlen(s) + 1);
  
      // Copy string into memory, including '\0'
      for (int i = 0; i <= strlen(s); i++)
      {
          t[i] = s[i];
      }
  
      // Capitalize copy
      t[0] = toupper(t[0]);
  
      // Print strings
      printf("s: %s\n", s);
      printf("t: %s\n", t);
  }
  ```

  Notice that `malloc(strlen(s) + 1)` creates a block of memory that is the length of the string `s` plus one. This allows for the inclusion of the *null* `\0` character in our final, copied string. Then, the `for` loop walks through the string `s` and assigns each value to that same location on the string `t`.

+ It turns out that there is an inefficiency in our code. Modify your code as follows:

  ```auto
  #include <cs50.h>
  #include <ctype.h>
  #include <stdio.h>
  #include <stdlib.h>
  #include <string.h>
  
  int main(void)
  {
      // Get a string
      char *s = get_string("s: ");
  
      // Allocate memory for another string
      char *t = malloc(strlen(s) + 1);
  
      // Copy string into memory, including '\0'
      for (int i = 0, n = strlen(s); i <= n; i++)
      {
          t[i] = s[i];
      }
  
      // Capitalize copy
      t[0] = toupper(t[0]);
  
      // Print strings
      printf("s: %s\n", s);
      printf("t: %s\n", t);
  }
  ```

  Notice that `n = strlen(s)` is defined now in the left-hand side of the `for loop`. It’s best not to call unneeded functions in the middle condition of the `for` loop, as it will run over and over again. When moving `n = strlen(s)` to the left-hand side, the function `strlen` only runs once.

+ The `C` Language has a built-in function to copy strings called `strcpy`. It can be implemented as follows:

  ```auto
  #include <cs50.h>
  #include <ctype.h>
  #include <stdio.h>
  #include <stdlib.h>
  #include <string.h>
  
  int main(void)
  {
      // Get a string
      char *s = get_string("s: ");
  
      // Allocate memory for another string
      char *t = malloc(strlen(s) + 1);
  
      // Copy string into memory
      strcpy(t, s);
  
      // Capitalize copy
      t[0] = toupper(t[0]);
  
      // Print strings
      printf("s: %s\n", s);
      printf("t: %s\n", t);
  }
  ```

  Notice that `strcpy` does the same work that our `for` loop previously did.

+ Both `get_string` and `malloc` return `NULL`, a special value in memory, in the event that something goes wrong. You can write code that can check for this `NULL` condition as follows:

  ```auto
  #include <cs50.h>
  #include <ctype.h>
  #include <stdio.h>
  #include <stdlib.h>
  #include <string.h>
  
  int main(void)
  {
      // Get a string
      char *s = get_string("s: ");
      if (s == NULL)
      {
          return 1;
      }
  
      // Allocate memory for another string
      char *t = malloc(strlen(s) + 1);
      if (t == NULL)
      {
          return 1;
      }
  
      // Copy string into memory
      strcpy(t, s);
  
      // Capitalize copy
      if (strlen(t) > 0)
      {
          t[0] = toupper(t[0]);
      }
  
      // Print strings
      printf("s: %s\n", s);
      printf("t: %s\n", t);
  
      // Free memory
      free(t);
      return 0;
  }
  ```

  Notice that if the string obtained is of length `0` or malloc fails, `NULL` is returned. Further, notice that `free` lets the computer know you are done with this block of memory you created via `malloc`.

## malloc and Valgrind

+ *Valgrind* is a tool that can check to see if there are memory-related issues with your programs wherein you utilized `malloc`. Specifically, it checks to see if you `free` all the memory you allocated.

+ Consider the following code for `memory.c`:

  ```auto
  #include <stdio.h>
  #include <stdlib.h>
  
  int main(void)
  {
      int *x = malloc(3 * sizeof(int));
      x[1] = 72;
      x[2] = 73;
      x[3] = 33;
  }
  ```

  Notice that running this program does not cause any errors. While `malloc` is used to allocate enough memory for an array, the code fails to `free` that allocated memory.

+ If you type `make memory` followed by `valgrind ./memory`, you will get a report from valgrind that will report where memory has been lost as a result of your program. One error that valgrind reveals is that we attempted to assign the value of `33` at the 4th position of the array, where we only allocated an array of size `3`. Another error is that we never freed `x`.

+ You can modify your code as follows:

  ```auto
  #include <stdio.h>
  #include <stdlib.h>
  
  int main(void)
  {
      int *x = malloc(3 * sizeof(int));
      x[0] = 72;
      x[1] = 73;
      x[2] = 33;
      free(x);
  }
  ```

  Notice that running valgrind again now results in no memory leaks.

## Garbage Values

+ When you ask the compiler for a block of memory, there is no guarantee that this memory will be empty.

+ It’s very possible that this memory that you allocated was previously utilized by the computer. Accordingly, you may see *junk* or *garbage values*. This is a result of you getting a block of memory but not initializing it. For example, consider the following code for `garbage.c`:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      int scores[1024];
      for (int i = 0; i < 1024; i++)
      {
          printf("%i\n", scores[i]);
      }
  }
  ```

  Notice that running this code will allocate `1024` locations in memory for your array, but the `for` loop will likely show that not all values therein are `0`. It’s always best practice to be aware of the potential for garbage values when you do not initialize blocks of memory to some other value like zero or otherwise.

## Pointer Fun with Binky

+   We watched a [video from Stanford University](https://www.youtube.com/watch?v=5VnDaHBi8dM) that helped us visualize and understand pointers.

## Swap

+ In the real world, a common need in programming is to swap two values. Naturally, it’s hard to swap two variables without a temporary holding space. In practice, you can type `code swap.c` and write code as follows to see this in action:

  ```auto
  #include <stdio.h>
  
  void swap(int a, int b);
  
  int main(void)
  {
      int x = 1;
      int y = 2;
  
      printf("x is %i, y is %i\n", x, y);
      swap(x, y);
      printf("x is %i, y is %i\n", x, y);
  }
  
  void swap(int a, int b)
  {
      int tmp = a;
      a = b;
      b = tmp;
  }
  ```

  Notice that while this code runs, it does not work. The values, even after being sent to the `swap` function, do not swap. Why?

+ When you pass values to a function, you are only providing copies. In previous weeks, we discussed the concept of *scope*. The values of `x` and `y` created in the curly `{}` braces of the `main` function only have the scope of the `main` function. Consider the following image:

  ![a rectangle with machine code at top followed by globals heap and stack](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide163-20240811154041360.png "stack and heap")

  Notice that *global* variables, which we have not used in this course, live in one place in memory. Various functions are stored in the `stack` in another area of memory.

+ Now, consider the following image:

  ![a rectangle with main function at bottom and swap function directly above it](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide167-20240811154041129.png "frames")

  Notice that `main` and `swap` have two separate *frames* or areas of memory. Therefore, we cannot simply pass the values from one function to another to change them.

+ Modify your code as follows:

  ```auto
  #include <stdio.h>
  
  void swap(int *a, int *b);
  
  int main(void)
  {
      int x = 1;
      int y = 2;
  
      printf("x is %i, y is %i\n", x, y);
      swap(&x, &y);
      printf("x is %i, y is %i\n", x, y);
  }
  
  void swap(int *a, int *b)
  {
      int tmp = *a;
      *a = *b;
      *b = tmp;
  }
  ```

  Notice that variables are not passed by *value* but by *reference*. That is, the addresses of `a` and `b` are provided to the function. Therefore, the `swap` function can know where to make changes to the actual `a` and `b` from the main function.

+ You can visualize this as follows:

  ![a and b stored in main function being passed by reference to the swap function](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week4Slide198-20240811154041418.png "swap by reference")

## Overflow

+   A *heap overflow* is when you overflow the heap, touching areas of memory you are not supposed to.
+   A *stack overflow* is when too many functions are called, overflowing the amount of memory available.
+   Both of these are considered *buffer overflows*.

## `scanf`

+ In CS50, we have created functions like `get_int` to simplify the act of getting input from the user.

+ `scanf` is a built-in function that can get user input.

+ We can reimplement `get_int` rather easily using `scanf` as follows:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      int x;
      printf("x: ");
      scanf("%i", &x);
      printf("x: %i\n", x);
  }
  ```

  Notice that the value of `x` is stored at the location of `x` in the line `scanf("%i", &x)`.

+ However, attempting to reimplement `get_string` is not easy. Consider the following:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      char *s;
      printf("s: ");
      scanf("%s", s);
      printf("s: %s\n", s);
  }
  ```

  Notice that no `&` is required because strings are special. Still, this program will not function. Nowhere in this program do we allocate the amount of memory required for our string. Indeed, we don’t know how long of a string may be inputted by the user!

+ Further, your code could be modified as follows. However, we have to pre-allocate a certain amount of memory for a string:

  ```auto
  #include <stdio.h>
  #include <stdlib.h>
  
  int main(void)
  {
      char *s = malloc(4);
      if (s == NULL)
      {
          return 1;
      }
      printf("s: ");
      scanf("%s", s);
      printf("s: %s\n", s);
      free(s);
      return 0;
  }
  ```

  Notice that if a string that is six bytes is provided you *might* get an error.

+ Simplifying our code as follows we can further understand this essential problem of pre-allocation:

  ```auto
  #include <stdio.h>
  
  int main(void)
  {
      char s[4];
      printf("s: ");
      scanf("%s", s);
      printf("s: %s\n", s);
  }
  ```

  Notice that if we pre-allocate an array of size `4`, we can type `cat` and the program functions. However, a string larger than this *could* create an error.

+ Sometimes, the compiler or the system running it may allocate more memory than we indicate. Fundamentally, though, the above code is unsafe. We cannot trust that the user will input a string that fits into our pre-allocated memory.

## File I/O

+ You can read from and manipulate files. While this topic will be discussed further in a future week, consider the following code for `phonebook.c`:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      // Open CSV file
      FILE *file = fopen("phonebook.csv", "a");
  
      // Get name and number
      char *name = get_string("Name: ");
      char *number = get_string("Number: ");
  
      // Print to file
      fprintf(file, "%s,%s\n", name, number);
  
      // Close file
      fclose(file);
  }
  ```

  Notice that this code uses pointers to access the file.

+ You can create a file called `phonebook.csv` in advance of running the above code. After running the above program and inputting a name and phone number, you will notice that this data persists in your CSV file.

+ If we want to ensure that `phonebook.csv` exists prior to running the program, we can modify our code as follows:

  ```auto
  #include <cs50.h>
  #include <stdio.h>
  #include <string.h>
  
  int main(void)
  {
      // Open CSV file
      FILE *file = fopen("phonebook.csv", "a");
      if (!file)
      {
          return 1;
      }
  
      // Get name and number
      char *name = get_string("Name: ");
      char *number = get_string("Number: ");
  
      // Print to file
      fprintf(file, "%s,%s\n", name, number);
  
      // Close file
      fclose(file);
  }
  ```

  Notice that this program protects against a `NULL` pointer by invoking `return 1`.

+ We can implement our own copy program by typing `code cp.c` and writing code as follows:

  ```auto
  #include <stdio.h>
  #include <stdint.h>
  
  typedef uint8_t BYTE;
  
  int main(int argc, char *argv[])
  {
      FILE *src = fopen(argv[1], "rb");
      FILE *dst = fopen(argv[2], "wb");
  
      BYTE b;
  
      while (fread(&b, sizeof(b), 1, src) !=0)
      {
          fwrite(&b, sizeof(b), 1, dst);
      }
  
      fclose(dst);
      fclose(src);
  }
  ```

  Notice that this file creates our own data type called a `BYTE` that is the size of a `uint8_t`. Then, the file reads a `BYTE` and writes it to a file.

+ BMPs are also assortments of data that we can examine and manipulate. This week, you will be doing just that in your problem sets!

## Summing Up

In this lesson, you learned about pointers that provide you with the ability to access and manipulate data at specific memory locations. Specifically, we delved into…

+   Pixel art
+   Hexadecimal
+   Memory
+   Pointers
+   Strings
+   Pointer Arithmetic
+   String Comparison
+   Copying
+   malloc and Valgrind
+   Garbage values
+   Swapping
+   Overflow
+   `scanf`
+   File I/O

See you next time!


# Lecture 5-Data Structures



- [Welcome!](https://cs50.harvard.edu/x/2024/notes/5/#welcome)
- [Data Structures](https://cs50.harvard.edu/x/2024/notes/5/#data-structures)
- [Stacks and Queues](https://cs50.harvard.edu/x/2024/notes/5/#stacks-and-queues)
- [Jack Learns the Facts](https://cs50.harvard.edu/x/2024/notes/5/#jack-learns-the-facts)
- [Resizing Arrays](https://cs50.harvard.edu/x/2024/notes/5/#resizing-arrays)
- [Linked Lists](https://cs50.harvard.edu/x/2024/notes/5/#linked-lists)
- [Trees](https://cs50.harvard.edu/x/2024/notes/5/#trees)
- [Dictionaries](https://cs50.harvard.edu/x/2024/notes/5/#dictionaries)
- [Hashing and Hash Tables](https://cs50.harvard.edu/x/2024/notes/5/#hashing-and-hash-tables)
- [Tries](https://cs50.harvard.edu/x/2024/notes/5/#tries)
- [Summing Up](https://cs50.harvard.edu/x/2024/notes/5/#summing-up)



## [Welcome!](https://cs50.harvard.edu/x/2024/notes/5/#welcome)

- All the prior weeks have presented you with the fundamental building blocks of programming.
- All you have learned in C will enable you to implement these building blocks in higher-level programming languages such as Python.
- Today, we are going to talk about organizing data in memory and design possibilities that emerge from your growing knowledge.



## [Data Structures](https://cs50.harvard.edu/x/2024/notes/5/#data-structures)

- *Data structures* essentially are forms of organization in memory.
- There are many ways to organize data in memory.
- *Abstract data structures* are those that we can conceptually imagine. When learning about computer science, it’s often useful to begin with these conceptual data structures. Learning these will make it easier later to understand how to implement more concrete data structures.



## [Stacks and Queues](https://cs50.harvard.edu/x/2024/notes/5/#stacks-and-queues)

- *Queues* are one form of abstract data structure.

- Queues have specific properties. Namely, they are *FIFO* or “first in first out.” You can imagine yourself in a line for a ride at an amusement park. The first person in the line gets to go on the ride first. The last person gets to go on the ride last.

- Queues have specific actions associated with them. For example, an item can be *enqueued*; that is, the item can join the line or queue. Further, an item can be *dequeued* or leave the queue once it reaches the front of the line.

- Queues contrast a *stack*. Fundamentally, the properties of a stack are different than a queue. Specifically, it is *LIFO* or “last in first out.” Just like stacking trays in a cafeteria, a tray that is placed in a stack last is the first that may be picked up.

- Stacks have specific actions associated with them. For example, *push* places something on top of a stack. *Pop* is removing something from the top of the stack.

- 

  In code, you might imagine a stack as follows:

  ```
  typedef struct
  {
      person people[CAPACITY];
      int size;
  }
  stack;
  ```

  Notice that an array called people is of type `person`. The `CAPACITY` is how high the stack could be. The integer `size` is how full the stack actually is, regardless of how much it *could* hold.

- You might imagine that the above code has a limitation. Since the capacity of the array is always predetermined in this code. Therefore, the stack may always be oversized. You might imagine only using one place in the stack out of 5000.

- It would be nice for our stack to be dynamic – able to grow as items are added to it.



## [Jack Learns the Facts](https://cs50.harvard.edu/x/2024/notes/5/#jack-learns-the-facts)

- We watched a video called [Jack Learns the Facts](https://www.youtube.com/watch?v=ItAG3s6KIEI) by Professor Shannon Duvall of Elon University.



## [Resizing Arrays](https://cs50.harvard.edu/x/2024/notes/5/#resizing-arrays)

- Rewinding to Week 2, we introduced you to your first data structure.

- An array is a block of contiguous memory.

- 

  You might imagine an array as follows:

  ![three boxes with 1 2 3](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide019-20240811153850828.png)

- 

  In memory, there are other values being stored by other programs, functions, and variables. Many of these may be unused garbage values that were utilized at one point but are available now for use.

  ![three boxes with 1 2 3 among lots of other memory elements](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide022.png)

- 

  Imagine you wanted to store a fourth value `4` in our array? What would be needed is to allocate a new area of memory and move the old array to a new one. Initially, this new area of memory would be populated with garbage values.

  ![Three boxes with 1 2 3 above four boxes with garbage values](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide025.png)

- 

  As values are added to this new area of memory, old garbage values would be overwritten.

  ![Three boxes with 1 2 3 above four boxes with 1 2 3 and a garbage value](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide026.png)

- 

  Eventually, all old garbage values would be overwritten with our new data.

  ![Three boxes with 1 2 3 above four boxes with 1 2 3 4](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide027.png)

- One of the drawbacks of this approach is that it’s bad design: Every time we add a number, we have to copy the array item by item.

- Wouldn’t it be nice if we were able to put the `4` somewhere else in memory? By definition, this would no longer be an array because `4` would no longer be in contiguous memory.

- 

  In your terminal, type `code list.c` and write code as follows:

  ```
  // Implements a list of numbers with an array of fixed size
  
  #include <stdio.h>
  
  int main(void)
  {
      // List of size 3
      int list[3];
  
      // Initialize list with numbers
      list[0] = 1;
      list[1] = 2;
      list[2] = 3;
  
      // Print list
      for (int i = 0; i < 3; i++)
      {
          printf("%i\n", list[i]);
      }
  }
  ```

  Notice that the above is very much like what we learned earlier in this course. We have memory being preallocated for three items.

- 

  Building upon our knowledge obtained more recently, we can leverage our understanding of pointers to create a better design in this code. Modify your code as follows:

  ```
  // Implements a list of numbers with an array of dynamic size
  
  #include <stdio.h>
  #include <stdlib.h>
  
  int main(void)
  {
      // List of size 3
      int *list = malloc(3 * sizeof(int));
      if (list == NULL)
      {
          return 1;
      }
  
      // Initialize list of size 3 with numbers
      list[0] = 1;
      list[1] = 2;
      list[2] = 3;
  
      // List of size 4
      int *tmp = malloc(4 * sizeof(int));
      if (tmp == NULL)
      {
          free(list);
          return 1;
      }
  
      // Copy list of size 3 into list of size 4
      for (int i = 0; i < 3; i++)
      {
          tmp[i] = list[i];
      }
  
      // Add number to list of size 4
      tmp[3] = 4;
  
      // Free list of size 3
      free(list);
  
      // Remember list of size 4
      list = tmp;
  
      // Print list
      for (int i = 0; i < 4; i++)
      {
          printf("%i\n", list[i]);
      }
  
      // Free list
      free(list);
      return 0;
  }
  ```

  Notice that a list of size three integers is created. Then, three memory addresses can be assigned the values `1`, `2`, and `3`. Then, a list of size four is created. Next, the list is copied from the first to the second. The value for the `4` is added to the `tmp` list. Since the block of memory that `list` points to is no longer used, it is freed using the command `free(list)`. Finally, the compiler is told to point `list` pointer now to the block of memory that `tmp` points to. The contents of `list` are printed and then freed.

- It’s useful to think about `list` and `tmp` as both signs that point at a chunk of memory. As in the example above, `list` at one point *pointed* to an array of size 3. By the end, `list` was told to point to a chunk of memory of size 4. Technically, by the end of the above code, `tmp` and `list` both pointed to the same block of memory.

- One may be tempted to allocate way more memory than required for the list, such as 30 items instead of the required 3 or 4. However, this is bad design as it taxes system resources when they are not potentially needed. Further, there is little guarantee that memory for more than 30 items will be needed eventually.



## [Linked Lists](https://cs50.harvard.edu/x/2024/notes/5/#linked-lists)

- In recent weeks, you have learned about three useful primitives. A `struct` is a data type that you can define yourself. A `.` in *dot notation* allows you to access variables inside that structure. The `*` operator is used to declare a pointer or dereference a variable.

- Today, you are introduced to the `->` operator. It is an arrow. This operator goes to an address and looks inside of a structure.

- A *linked list* is one of the most powerful data structures within C. A linked list allows you to include values that are located at varying areas of memory. Further, they allow you to dynamically grow and shrink the list as you desire.

- 

  You might imagine three values stored at three different areas of memory as follows:

  ![Three boxes with 1 2 3 in separate areas of memory](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide036.png)

- How could one stitch together these values in a list?

- 

  We could imagine this data pictured above as follows:

  ![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide037-20240811153851089.png)

- 

  We could utilize more memory to keep track of where the next item is.

  ![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached where memory addresses are in those attached boxes](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide041-20240811153851315.png)

  Notice that NULL is utilized to indicate that nothing else is *next* in the list.

- 

  By convention, we would keep one more element in memory, a pointer, that keeps track of the first item in the list.

  ![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached where memory addresses are in those attached boxes now with a final box with the memory address of the first box](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide042.png)

- 

  Abstracting away the memory addresses, the list would appear as follows:

  ![Three boxes with in separate areas of memory with smaller boxes with a final box where the one box points to another and another until the end of the boxes](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide043.png)

- 

  These boxes are called *nodes*. A *node* contains both an *item* and a pointer called *next*. In code, you can imagine a node as follows:

  ```
  typedef struct node
  {
      int number;
      struct node *next;
  }
  node;
  ```

  Notice that the item contained within this node is an integer called `number`. Second, a pointer to a node called `next` is included, which will point to another node somewhere in memory.

- 

  Conceptually, we can imagine the process of creating a linked list. First, `node *list` is declared, but it is of a garbage value.

  ![One garbage value](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide055.png)

- 

  Next, a node called `n` is allocated in memory.

  ![One garbage value called n with another pointer called list](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide059-20240811153851815.png)

- 

  Next, the `number` of node is assigned the value `1`.

  ![n pointing to a node with 1 as the number and garbage value as the next](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide064.png)

- 

  Next, the node’s `next` field is assigned `NULL`.

  ![n pointing to a node with 1 as the number and null as the value of next](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide066.png)

- 

  Next, `list` is pointed at the memory location to where `n` points. `n` and `list` now point to the same place.

  ![n and list both pointing to a node with 1 as the number and null as the value of next](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide068-20240811153851850.png)

- 

  A new node is then created. Both the `number` and `next` field are both filled with garbage values.

  ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with garbage values](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide073.png)

- 

  The `number` value of `n`’s node (the new node) is updated to `2`.

  ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and garbage as the next](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide075.png)

- 

  Also, the `next` field is updated as well.

  ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and null as the next](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide077.png)

- 

  Most important, we do not want to lose our connection to any of these nodes lest they be lost forever. Accordingly, `n`’s `next` field is pointed to the same memory location as `list`.

  ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and null as the next](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide084.png)

- 

  Finally, `list` is updated to point at `n`. We now have a linked list of two items.

  ![list pointing to a node with 1 as the number and next pointing to a node with an n pointing the same place the node with one points to a node with 2 as the number and null as the next](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide086.png)

- 

  To implement this in code, modify your code as follows:

  ```
  // Prepends numbers to a linked list, using while loop to print
  
  #include <cs50.h>
  #include <stdio.h>
  #include <stdlib.h>
  
  typedef struct node
  {
      int number;
      struct node *next;
  }
  node;
  
  int main(int argc, char *argv[])
  {
      // Memory for numbers
      node *list = NULL;
  
      // For each command-line argument
      for (int i = 1; i < argc; i++)
      {
          // Convert argument to int
          int number = atoi(argv[i]);
  
          // Allocate node for number
          node *n = malloc(sizeof(node));
          if (n == NULL)
          {
              return 1;
          }
          n->number = number;
          n->next = NULL;
  
          // Prepend node to list
          n->next = list;
          list = n;
      }
  
      // Print numbers
      node *ptr = list;
      while (ptr != NULL)
      {
          printf("%i\n", ptr->number);
          ptr = ptr->next;
      }
  
      // Free memory
      ptr = list;
      while (ptr != NULL)
      {
          node *next = ptr->next;
          free(ptr);
          ptr = next;
      }
  }
  ```

  Notice that what the user inputs at the command line is put into the `number` field of a node called `n`, and then that node is added to the `list`. For example, `./list 1 2` will put the number `1` into the `number` field of a node called `n`, then put a pointer to `list` into the `next` field of the node, and then update `list` to point to `n`. That same process is repeated for `2`. Next, `node *ptr = list` creates a temporary variable that points at the same spot that `list` points to. The `while` prints what at the node `ptr` points to, and then updates `ptr` to point to the `next` node in the list. Finally, all the memory is freed.

- In this example, inserting into the list is always in the order of O(1), as it only takes a very small number of steps to insert at the front of a list.

- Considering the amount of time required to search this list, it is in the order of O(n), as in the worst case the entire list must always be searched to find an item. The time complexity for adding a new element to the list will depend on where that element is added. This is illustrated in the examples below.

- Linked lists are not stored in a contiguous block of memory. They can grow as large as you wish, provided that enough system resources exist. The downside, however, is that more memory is required to keep track of the list instead of an array. This is because for each element, you must store not just the value of the element, but also a pointer to the next node. Further, linked lists cannot be indexed into like is possible in an array because we need to pass through the first n−1 elements to find the location of the nth element. Because of this, the list pictured above must be linearly searched. Binary search, therefore, is not possible in a list constructed as above.

- 

  Further, you could place numbers at the end of the list as illustrated in this code:

  ```
  // Implements a list of numbers using a linked list
  
  #include <cs50.h>
  #include <stdio.h>
  #include <stdlib.h>
  
  typedef struct node
  {
      int number;
      struct node *next;
  }
  node;
  
  int main(int argc, char *argv[])
  {
      // Memory for numbers
      node *list = NULL;
  
      // For each command-line argument
      for (int i = 1; i < argc; i++)
      {
          // Convert argument to int
          int number = atoi(argv[i]);
  
          // Allocate node for number
          node *n = malloc(sizeof(node));
          if (n == NULL)
          {
              return 1;
          }
          n->number = number;
          n->next = NULL;
  
          // If list is empty
          if (list == NULL)
          {
              // This node is the whole list
              list = n;
          }
  
          // If list has numbers already
          else
          {
              // Iterate over nodes in list
              for (node *ptr = list; ptr != NULL; ptr = ptr->next)
              {
                  // If at end of list
                  if (ptr->next == NULL)
                  {
                      // Append node
                      ptr->next = n;
                      break;
                  }
              }
          }
      }
  
      // Print numbers
      for (node *ptr = list; ptr != NULL; ptr = ptr->next)
      {
          printf("%i\n", ptr->number);
      }
  
      // Free memory
      node *ptr = list;
      while (ptr != NULL)
      {
          node *next = ptr->next;
          free(ptr);
          ptr = next;
      }
  }
  ```

  Notice how this code *walks down* this list to find the end. When appending an element, (adding to the end of the list) our code will run in O(n), as we have to go through our entire list before we can add the final element.

- 

  Further, you could sort your list as items are added:

  ```
  // Implements a sorted list of numbers using a linked list
  
  #include <cs50.h>
  #include <stdio.h>
  #include <stdlib.h>
  
  typedef struct node
  {
      int number;
      struct node *next;
  }
  node;
  
  int main(int argc, char *argv[])
  {
      // Memory for numbers
      node *list = NULL;
  
      // For each command-line argument
      for (int i = 1; i < argc; i++)
      {
          // Convert argument to int
          int number = atoi(argv[i]);
  
          // Allocate node for number
          node *n = malloc(sizeof(node));
          if (n == NULL)
          {
              return 1;
          }
          n->number = number;
          n->next = NULL;
  
          // If list is empty
          if (list == NULL)
          {
              list = n;
          }
  
          // If number belongs at beginning of list
          else if (n->number < list->number)
          {
              n->next = list;
              list = n; 
          }
  
          // If number belongs later in list
          else
          {
              // Iterate over nodes in list
              for (node *ptr = list; ptr != NULL; ptr = ptr->next)
              {
                  // If at end of list
                  if (ptr->next == NULL)
                  {
                      // Append node
                      ptr->next = n;
                      break;
                  }
  
                  // If in middle of list
                  if (n->number < ptr->next->number)
                  {
                      n->next = ptr->next;
                      ptr->next = n;
                      break;
                  }
              }
          }
      }
  
      // Print numbers
      for (node *ptr = list; ptr != NULL; ptr = ptr->next)
      {
          printf("%i\n", ptr->number);
      }
  
      // Free memory
      node *ptr = list;
      while (ptr != NULL)
      {
          node *next = ptr->next;
          free(ptr);
          ptr = next;
      }
  }
  ```

  Notice how this list is sorted as it is built. To insert an element in this specific order, our code will still run in O(n) for each insertion, as in the worst case we will have to look through all current elements.



## [Trees](https://cs50.harvard.edu/x/2024/notes/5/#trees)

- *Binary search trees* are another data structure that can be used to store data more efficiently such that it can be searched and retrieved.

- 

  You can imagine a sorted sequence of numbers.

  ![1 2 3 4 5 6 7 in boxes next to each other](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide118.png)

- 

  Imagine then that the center value becomes the top of a tree. Those that are less than this value are placed to the left. Those values that are more than this value are to the right.

  ![1 2 3 4 5 6 7 in boxes arranged in a hierarchy 4 is at the top 3 and 5 are below that and 1 2 6 7 are below those](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide119.png)

- 

  Pointers can then be used to point to the correct location of each area of memory such that each of these nodes can be connected.

  ![1 2 3 4 5 6 7 in boxes arranged in a hierarchy 4 is at the top 3 and 5 are below that and 1 2 6 7 are below those arrows connect them in a tree formation](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide120.png)

- 

  In code, this can be implemented as follows.

  ```
  // Implements a list of numbers as a binary search tree
  
  #include <stdio.h>
  #include <stdlib.h>
  
  // Represents a node
  typedef struct node
  {
      int number;
      struct node *left;
      struct node *right;
  }
  node;
  
  void free_tree(node *root);
  void print_tree(node *root);
  
  int main(void)
  {
      // Tree of size 0
      node *tree = NULL;
  
      // Add number to list
      node *n = malloc(sizeof(node));
      if (n == NULL)
      {
          return 1;
      }
      n->number = 2;
      n->left = NULL;
      n->right = NULL;
      tree = n;
  
      // Add number to list
      n = malloc(sizeof(node));
      if (n == NULL)
      {
          free_tree(tree);
          return 1;
      }
      n->number = 1;
      n->left = NULL;
      n->right = NULL;
      tree->left = n;
  
      // Add number to list
      n = malloc(sizeof(node));
      if (n == NULL)
      {
          free_tree(tree);
          return 1;
      }
      n->number = 3;
      n->left = NULL;
      n->right = NULL;
      tree->right = n;
  
      // Print tree
      print_tree(tree);
  
      // Free tree
      free_tree(tree);
      return 0;
  }
  
  void free_tree(node *root)
  {
      if (root == NULL)
      {
          return;
      }
      free_tree(root->left);
      free_tree(root->right);
      free(root);
  }
  
  void print_tree(node *root)
  {
      if (root == NULL)
      {
          return;
      }
      print_tree(root->left);
      printf("%i\n", root->number);
      print_tree(root->right);
  }
  ```

  Notice this search function begins by going to the location of `tree`. Then, it uses recursion to search for `number`. The `free_tree` function recursively frees the tree. `print_tree` recursively prints the tree.

- A tree like the above offers dynamism that an array does not offer. It can grow and shrink as we wish.

- Further, this structure offers a search time of O(logn).



## [Dictionaries](https://cs50.harvard.edu/x/2024/notes/5/#dictionaries)

- *Dictionaries* are another data structure.

- Dictionaries, like actual book-form dictionaries that have a word and a definition, have a *key* and a *value*.

- 

  The *holy grail* of algorithmic time complexity is O(1) or *constant time*. That is, the ultimate is for access to be instantaneous.

  ![a graph of various time comlexities where O of log n is second best and O of 1 is best](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide151.png)

- Dictionaries can offer this speed of access through hashing.



## [Hashing and Hash Tables](https://cs50.harvard.edu/x/2024/notes/5/#hashing-and-hash-tables)

- *Hashing* is the idea of taking a value and being able to output a value that becomes a shortcut to it later.

- For example, hashing *apple* may hash as a value of `1`, and *berry* may be hashed as `2`. Therefore, finding *apple* is as easy as asking the *hash* algorithm where *apple* is stored. While not ideal in terms of design, ultimately, putting all *a*’s in one bucket and *b*’s in another, this concept of *bucketizing* hashed values illustrates how you can use this concept: a hashed value can be used to shortcut finding such a value.

- A *hash function* is an algorithm that reduces a larger value to something small and predictable. Generally, this function takes in an item you wish to add to your hash table, and returns an integer representing the array index in which the item should be placed.

- A *hash table* is a fantastic combination of both arrays and linked lists. When implemented in code, a hash table is an *array* of *pointers* to *node*s.

- 

  A hash table could be imagined as follows:

  ![a verticle column of 26 boxes one for each letter of the alphabet](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide157.png)

  Notice that this is an array that is assigned each value of the alphabet.

- 

  Then, at each location of the array, a linked list is used to track each value being stored there:

  ![a verticle column of 26 boxes one for each letter of the alphabet with various names from themario unverise emerging to the right luigi is with l and mario is with m](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide169.png)

- *Collisions* are when you add values to the hash table, and something already exists at the hashed location. In the above, collisions are simply appended to the end of the list.

- 

  Collisions can be reduced by better programming your hash table and hash algorithm. You can imagine an improvement upon the above as follows:

  ![a verticle column of various boxeds arranged by L A K and L I N with lakitu emerging from L A K and link emerging from L I N](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide184.png)

- 

  Consider the following example of a hash algorithm:

  ![luigi being given to a hash algorithm outputting 11](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide173.png)

- 

  This could be implemented in code as:

  ```
  #include <ctype.h>
  
  unsigned int hash(const char *word)
  {
      return toupper(word[0]) - 'A';
  }
  ```

  Notice how the hash function returns the value of `toupper(word[0]) - 'A'`.

- You, as the programmer, have to make a decision about the advantages of using more memory to have a large hash table and potentially reducing search time or using less memory and potentially increasing search time.



## [Tries](https://cs50.harvard.edu/x/2024/notes/5/#tries)

- *Tries* are another form of data structure.

- *Tries* are always searchable in constant time.

- One downside to *Tries* is that they tend to take up a large amount of memory. Notice that we need 26×4=104 `node`s just to store *Toad*!

- 

  *Toad* would be stored as follows:

  ![toad being spelled with one letter at a time where one letter is associated with one list T from one list O from another and so on ](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide207.png)

- 

  *Tom* would then be stored as follows:

  ![toad being spelled with one letter at a time where one letter is associated with one list T from one list O from another and so on and tom being spelled similarly where toad and tom share a two common letters T and O](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/cs50Week5Slide209.png)

- The downside of this structure is how many resources are required to use it.



## [Summing Up](https://cs50.harvard.edu/x/2024/notes/5/#summing-up)

In this lesson, you learned about using pointers to build new data structures. Specifically, we delved into…

- Data structures
- Stacks and queues
- Resizing arrays
- Linked lists
- Dictionaries
- Tries

See you next time!



