A major purpose of functions is to group code that gets executed multiple times. Without a function defined, you would have to copy and paste this code each time, and the program would look like this:

Create your own function:
ex: helloFunc.py

**Def Statements w/Parameters**

def hello(name)
	print('Hello, ' + name)
hello('Alice')
hello('Bob')
__________________
### **Return Values and return Statements**

When you call the len() function and pass it an argument such as 'Hello', the function call evaluates to the integer value 5, which is the length of the string you passed it. In general, the value that a function call evaluates to is called the _return value_ of the function.

When creating a function using the def statement, you can specify what the return value should be with a return statement. A return statement consists of the following:

-   The return keyword
-   The value or expression that the function should return

When an expression is used with a return statement, the return value is what this expression evaluates to. For example, the following program defines a function that returns a different string depending on what number it is passed as an argument. Enter this code into the file editor and save it as _magic8Ball.py_:

➊ import random  
  
➋ def getAnswer(answerNumber):  
    ➌ if answerNumber == 1:  
           return 'It is certain'  
       elif answerNumber == 2:  
           return 'It is decidedly so'  
       elif answerNumber == 3:  
           return 'Yes'  
       elif answerNumber == 4:  
           return 'Reply hazy try again'  
       elif answerNumber == 5:  
           return 'Ask again later'  
       elif answerNumber == 6:  
           return 'Concentrate and ask again'  
       elif answerNumber == 7:  
           return 'My reply is no'  
       elif answerNumber == 8:  
           return 'Outlook not so good'  
       elif answerNumber == 9:  
           return 'Very doubtful'  
  
➍ r = random.randint(1, 9)  
➎ fortune = getAnswer(r)  
➏ print(fortune)

You can view the execution of this program at _[https://autbor.com/magic8ball/](https://autbor.com/magic8ball/)_. When this program starts, Python first imports the random module ➊. Then the getAnswer() function is defined ➋. Because the function is being defined (and not called), the execution skips over the code in it. Next, the random.randint() function is called with two arguments: 1 and 9 ➍. It evaluates to a random integer between 1 and 9 (including 1 and 9 themselves), and this value is stored in a variable named r.

The getAnswer() function is called with r as the argument ➎. The program execution moves to the top of the getAnswer() function ➌, and the value r is stored in a parameter named answerNumber. Then, depending on the value in answerNumber, the function returns one of many possible string values. The program execution returns to the line at the bottom of the program that originally called getAnswer() ➎. The returned string is assigned to a variable named fortune, which then gets passed to a print() call ➏ and is printed to the screen.

### **The Call Stack**

Imagine that you have a meandering conversation with someone. You talk about your friend Alice, which then reminds you of a story about your coworker Bob, but first you have to explain something about your cousin Carol. You finish you story about Carol and go back to talking about Bob, and when you finish your story about Bob, you go back to talking about Alice. But then you are reminded about your brother David, so you tell a story about him, and then get back to finishing your original story about Alice. Your conversation followed a _stack_-like structure, like in [Figure 3-1](https://automatetheboringstuff.com/2e/chapter3/#calibre_link-1213). The conversation is stack-like because the current topic is always at the top of the stack.

![image](https://automatetheboringstuff.com/2e/images/000109.jpg)

_Figure 3-1: Your meandering conversation stack_

Similar to our meandering conversation, calling a function doesn’t send the execution on a one-way trip to the top of a function. Python will remember which line of code called the function so that the execution can return there when it encounters a return statement. If that original function called other functions, the execution would return to _those_ function calls first, before returning from the original function call.

Open a file editor window and enter the following code, saving it as _abcdCallStack.py_:

   def a():  
       print('a() starts')  
    ➊ b()  
    ➋ d()  
       print('a() returns')  
  
   def b():  
       print('b() starts')  
    ➌ c()  
       print('b() returns')  
  
   def c():  
    ➍ print('c() starts')  
       print('c() returns')  
  
   def d():  
       print('d() starts')  
       print('d() returns')  
  
➎ a()

If you run this program, the output will look like this:

a() starts  
b() starts  
c() starts  
c() returns  
b() returns  
d() starts  
d() returns  
a() returns

You can view the execution of this program at _[https://autbor.com/abcdcallstack/](https://autbor.com/abcdcallstack/)_. When a() is called ➎, it calls b() ➊, which in turn calls c() ➌. The c() function doesn’t call anything; it just displays c() starts ➍ and c() returns before returning to the line in b() that called it ➌. Once execution returns to the code in b() that called c(), it returns to the line in a() that called b() ➊. The execution continues to the next line in the b() function ➋, which is a call to d(). Like the c() function, the d() function also doesn’t call anything. It just displays d() starts and d() returns before returning to the line in b() that called it. Since b() contains no other code, the execution returns to the line in a() that called b() ➋. The last line in a() displays a() returns before returning to the original a() call at the end of the program ➎.

The _call stack_ is how Python remembers where to return the execution after each function call. The call stack isn’t stored in a variable in your program; rather, Python handles it behind the scenes. When your program calls a function, Python creates a _frame object_ on the top of the call stack. Frame objects store the line number of the original function call so that Python can remember where to return. If another function call is made, Python puts another frame object on the call stack above the other one.

When a function call returns, Python removes a frame object from the top of the stack and moves the execution to the line number stored in it. Note that frame objects are always added and removed from the top of the stack and not from any other place. [Figure 3-2](https://automatetheboringstuff.com/2e/chapter3/#calibre_link-1214) illustrates the state of the call stack in _abcdCallStack.py_ as each function is called and returns.

![image](https://automatetheboringstuff.com/2e/images/000054.jpg)

_Figure 3-2: The frame objects of the call stack as_ abcdCallStack.py _calls and returns from functions_

The top of the call stack is which function the execution is currently in. When the call stack is empty, the execution is on a line outside of all functions.

The call stack is a technical detail that you don’t strictly need to know about to write programs. It’s enough to understand that function calls return to the line number they were called from. However, understanding call stacks makes it easier to understand local and global scopes, described in the next section.

### **Local and Global Scope**

Parameters and variables that are assigned in a called function are said to exist in that function’s _local scope_. Variables that are assigned outside all functions are said to exist in the _global scope_. A variable that exists in a local scope is called a _local variable_, while a variable that exists in the global scope is called a _global variable_. A variable must be one or the other; it cannot be both local and global.

Think of a _scope_ as a container for variables. When a scope is destroyed, all the values stored in the scope’s variables are forgotten. There is only one global scope, and it is created when your program begins. When your program terminates, the global scope is destroyed, and all its variables are forgotten. Otherwise, the next time you ran a program, the variables would remember their values from the last time you ran it.

A local scope is created whenever a function is called. Any variables assigned in the function exist within the function’s local scope. When the function returns, the local scope is destroyed, and these variables are forgotten. The next time you call the function, the local variables will not remember the values stored in them from the last time the function was called. Local variables are also stored in frame objects on the call stack.

Scopes matter for several reasons:

-   Code in the global scope, outside of all functions, cannot use any local variables.
-   However, code in a local scope can access global variables.
-   Code in a function’s local scope cannot use variables in any other local scope.
-   You can use the same name for different variables if they are in different scopes. That is, there can be a local variable named spam and a global variable also named spam.

The reason Python has different scopes instead of just making everything a global variable is so that when variables are modified by the code in a particular call to a function, the function interacts with the rest of the program only through its parameters and the return value. This narrows down the number of lines of code that may be causing a bug. If your program contained nothing but global variables and had a bug because of a variable being set to a bad value, then it would be hard to track down where this bad value was set. It could have been set from anywhere in the program, and your program could be hundreds or thousands of lines long! But if the bug is caused by a local variable with a bad value, you know that only the code in that one function could have set it incorrectly.

While using global variables in small programs is fine, it is a bad habit to rely on global variables as your programs get larger and larger.

#### **_Local Variables Cannot Be Used in the Global Scope_**

Consider this program, which will cause an error when you run it:

def spam():  
➊ eggs = 31337  
spam()  
print(eggs)

If you run this program, the output will look like this:

Traceback (most recent call last):  
  File "C:/test1.py", line 4, in <module>  
    print(eggs)  
NameError: name 'eggs' is not defined

The error happens because the eggs variable exists only in the local scope created when spam() is called ➊. Once the program execution returns from spam, that local scope is destroyed, and there is no longer a variable named eggs. So when your program tries to run print(eggs), Python gives you an error saying that eggs is not defined. This makes sense if you think about it; when the program execution is in the global scope, no local scopes exist, so there can’t be any local variables. This is why only global variables can be used in the global scope.

#### **_Local Scopes Cannot Use Variables in Other Local Scopes_**

A new local scope is created whenever a function is called, including when a function is called from another function. Consider this program:

  def spam():  
    ➊ eggs = 99  
    ➋ bacon()  
    ➌ print(eggs)  
  
   def bacon():  
       ham = 101  
    ➍ eggs = 0  
  
➎ spam()

You can view the execution of this program at _[https://autbor.com/otherlocalscopes/](https://autbor.com/otherlocalscopes/)_. When the program starts, the spam() function is called ➎, and a local scope is created. The local variable eggs ➊ is set to 99. Then the bacon() function is called ➋, and a second local scope is created. Multiple local scopes can exist at the same time. In this new local scope, the local variable ham is set to 101, and a local variable eggs—which is different from the one in spam()’s local scope—is also created ➍ and set to 0.

When bacon() returns, the local scope for that call is destroyed, including its eggs variable. The program execution continues in the spam() function to print the value of eggs ➌. Since the local scope for the call to spam() still exists, the only eggs variable is the spam() function’s eggs variable, which was set to 99. This is what the program prints.

The upshot is that local variables in one function are completely separate from the local variables in another function.

#### **_Global Variables Can Be Read from a Local Scope_**

Consider the following program:

def spam():  
    print(eggs)  
eggs = 42  
spam()  
print(eggs)

You can view the execution of this program at _[https://autbor.com/readglobal/](https://autbor.com/readglobal/)_. Since there is no parameter named eggs or any code that assigns eggs a value in the spam() function, when eggs is used in spam(), Python considers it a reference to the global variable eggs. This is why 42 is printed when the previous program is run.

#### **_Local and Global Variables with the Same Name_**

Technically, it’s perfectly acceptable to use the same variable name for a global variable and local variables in different scopes in Python. But, to simplify your life, avoid doing this. To see what happens, enter the following code into the file editor and save it as _localGlobalSameName.py_:

   def spam():  
    ➊ eggs = 'spam local'  
       print(eggs)    # prints 'spam local'  
  
   def bacon():  
    ➋ eggs = 'bacon local'  
       print(eggs)    # prints 'bacon local'  
       spam()  
       print(eggs)    # prints 'bacon local'  
  
➌ eggs = 'global'  
   bacon()  
   print(eggs)        # prints 'global'

When you run this program, it outputs the following:

bacon local  
spam local  
bacon local  
global

You can view the execution of this program at _[https://autbor.com/localglobalsamename/](https://autbor.com/localglobalsamename/)_. There are actually three different variables in this program, but confusingly they are all named eggs. The variables are as follows:

➊ A variable named eggs that exists in a local scope when spam() is called.

➋ A variable named eggs that exists in a local scope when bacon() is called.

➌ A variable named eggs that exists in the global scope.

Since these three separate variables all have the same name, it can be confusing to keep track of which one is being used at any given time. This is why you should avoid using the same variable name in different scopes.

### **The global Statement**

If you need to modify a global variable from within a function, use the global statement. If you have a line such as global eggs at the top of a function, it tells Python, “In this function, eggs refers to the global variable, so don’t create a local variable with this name.” For example, enter the following code into the file editor and save it as _globalStatement.py_:

def spam():  
  ➊ global eggs  
  ➋ eggs = 'spam'  
  
eggs = 'global'  
spam()  
print(eggs)

When you run this program, the final print() call will output this:

spam

You can view the execution of this program at _[https://autbor.com/globalstatement/](https://autbor.com/globalstatement/)_. Because eggs is declared global at the top of spam() ➊, when eggs is set to 'spam' ➋, this assignment is done to the globally scoped eggs. No local eggs variable is created.

There are four rules to tell whether a variable is in a local scope or global scope:

-   If a variable is being used in the global scope (that is, outside of all functions), then it is always a global variable.
-   If there is a global statement for that variable in a function, it is a global variable.
-   Otherwise, if the variable is used in an assignment statement in the function, it is a local variable.
-   But if the variable is not used in an assignment statement, it is a global variable.

To get a better feel for these rules, here’s an example program. Enter the following code into the file editor and save it as _sameNameLocalGlobal.py_:

def spam():  
  ➊ global eggs  
     eggs = 'spam' # this is the global  
  
def bacon():  
  ➋ eggs = 'bacon' # this is a local  
  
def ham():  
  ➌ print(eggs) # this is the global  
  
eggs = 42 # this is the global  
spam()  
print(eggs)

In the spam() function, eggs is the global eggs variable because there’s a global statement for eggs at the beginning of the function ➊. In bacon(), eggs is a local variable because there’s an assignment statement for it in that function ➋. In ham() ➌, eggs is the global variable because there is no assignment statement or global statement for it in that function. If you run _sameNameLocalGlobal.py_, the output will look like this:

spam

You can view the execution of this program at _[https://autbor.com/sameNameLocalGlobal/](https://autbor.com/sameNameLocalGlobal/)_. In a function, a variable will either always be global or always be local. The code in a function can’t use a local variable named eggs and then use the global eggs variable later in that same function.

**NOTE**

_If you ever want to modify the value stored in a global variable from in a function, you must use a global statement on that variable._

If you try to use a local variable in a function before you assign a value to it, as in the following program, Python will give you an error. To see this, enter the following into the file editor and save it as _sameNameError.py_:

   def spam():  
       print(eggs) # ERROR!  
    ➊ eggs = 'spam local'  
  
➋ eggs = 'global'  
   spam()

If you run the previous program, it produces an error message.

Traceback (most recent call last):  
  File "C:/sameNameError.py", line 6, in <module>  
    spam()  
  File "C:/sameNameError.py", line 2, in spam  
    print(eggs) # ERROR!  
UnboundLocalError: local variable 'eggs' referenced before assignment

You can view the execution of this program at _[https://autbor.com/sameNameError/](https://autbor.com/sameNameError/)_. This error happens because Python sees that there is an assignment statement for eggs in the spam() function ➊ and, therefore, considers eggs to be local. But because print(eggs) is executed before eggs is assigned anything, the local variable eggs doesn’t exist. Python will _not_ fall back to using the global eggs variable ➋.

**FUNCTIONS AS “BLACK BOXES”**

Often, all you need to know about a function are its inputs (the parameters) and output value; you don’t always have to burden yourself with how the function’s code actually works. When you think about functions in this high-level way, it’s common to say that you’re treating a function as a “black box.”

This idea is fundamental to modern programming. Later chapters in this book will show you several modules with functions that were written by other people. While you can take a peek at the source code if you’re curious, you don’t need to know how these functions work in order to use them. And because writing functions without global variables is encouraged, you usually don’t have to worry about the function’s code interacting with the rest of your program.

### **Exception Handling**

Right now, getting an error, or _exception_, in your Python program means the entire program will crash. You don’t want this to happen in real-world programs. Instead, you want the program to detect errors, handle them, and then continue to run.

For example, consider the following program, which has a divide-by-zero error. Open a file editor window and enter the following code, saving it as _zeroDivide.py_:

def spam(divideBy):  
    return 42 / divideBy  
  
print(spam(2))  
print(spam(12))  
print(spam(0))  
print(spam(1))

We’ve defined a function called spam, given it a parameter, and then printed the value of that function with various parameters to see what happens. This is the output you get when you run the previous code:

21.0  
3.5  
Traceback (most recent call last):  
  File "C:/zeroDivide.py", line 6, in <module>  
    print(spam(0))  
  File "C:/zeroDivide.py", line 2, in spam  
    return 42 / divideBy  
ZeroDivisionError: division by zero

You can view the execution of this program at _[https://autbor.com/zerodivide/](https://autbor.com/zerodivide/)_. A ZeroDivisionError happens whenever you try to divide a number by zero. From the line number given in the error message, you know that the return statement in spam() is causing an error.

Errors can be handled with try and except statements. The code that could potentially have an error is put in a try clause. The program execution moves to the start of a following except clause if an error happens.

You can put the previous divide-by-zero code in a try clause and have an except clause contain code to handle what happens when this error occurs.

def spam(divideBy):  
    try:  
        return 42 / divideBy  
    except ZeroDivisionError:  
        print('Error: Invalid argument.')  
  
print(spam(2))  
print(spam(12))  
print(spam(0))  
print(spam(1))

When code in a try clause causes an error, the program execution immediately moves to the code in the except clause. After running that code, the execution continues as normal. The output of the previous program is as follows:

21.0  
3.5  
Error: Invalid argument.  
None  
42.0

You can view the execution of this program at _[https://autbor.com/tryexceptzerodivide/](https://autbor.com/tryexceptzerodivide/)_. Note that any errors that occur in function calls in a try block will also be caught. Consider the following program, which instead has the spam() calls in the try block:

def spam(divideBy):  
    return 42 / divideBy  
  
try:  
    print(spam(2))  
    print(spam(12))  
    print(spam(0))  
    print(spam(1))  
except ZeroDivisionError:  
    print('Error: Invalid argument.')

When this program is run, the output looks like this:

21.0  
3.5  
Error: Invalid argument.

You can view the execution of this program at _[https://autbor.com/spamintry/](https://autbor.com/spamintry/)_. The reason print(spam(1)) is never executed is because once the execution jumps to the code in the except clause, it does not return to the try clause. Instead, it just continues moving down the program as normal.

### **A Short Program: Zigzag**

Let’s use the programming concepts you’ve learned so far to create a small animation program. This program will create a back-and-forth, zigzag pattern until the user stops it by pressing the Mu editor’s Stop button or by pressing CTRL-C. When you run this program, the output will look something like this:

    ********  
   ********  
  ********  
 ********  
********  
 ********  
  ********  
   ********  
    ********

Type the following source code into the file editor, and save the file as _zigzag.py_:

import time, sys  
indent = 0 # How many spaces to indent.  
indentIncreasing = True # Whether the indentation is increasing or not.  
  
try:  
    while True: # The main program loop.  
        print(' ' * indent, end='')  
        print('********')  
        time.sleep(0.1) # Pause for 1/10 of a second.  
  
        if indentIncreasing:  
            # Increase the number of spaces:  
            indent = indent + 1  
            if indent == 20:  
                # Change direction:  
                indentIncreasing = False  
  
        else:  
            # Decrease the number of spaces:  
            indent = indent - 1  
            if indent == 0:  
                # Change direction:  
                indentIncreasing = True  
except KeyboardInterrupt:  
    sys.exit()

Let’s look at this code line by line, starting at the top.

import time, sys  
indent = 0 # How many spaces to indent.  
indentIncreasing = True # Whether the indentation is increasing or not.

First, we’ll import the time and sys modules. Our program uses two variables: the indent variable keeps track of how many spaces of indentation are before the band of eight asterisks and indentIncreasing contains a Boolean value to determine if the amount of indentation is increasing or decreasing.

try:  
    while True: # The main program loop.  
        print(' ' * indent, end='')  
        print('********')  
        time.sleep(0.1) # Pause for 1/10 of a second.

Next, we place the rest of the program inside a try statement. When the user presses CTRL-C while a Python program is running, Python raises the KeyboardInterrupt exception. If there is no try-except statement to catch this exception, the program crashes with an ugly error message. However, for our program, we want it to cleanly handle the KeyboardInterrupt exception by calling sys.exit(). (The code for this is in the except statement at the end of the program.)

The while True: infinite loop will repeat the instructions in our program forever. This involves using ' ' * indent to print the correct amount of spaces of indentation. We don’t want to automatically print a newline after these spaces, so we also pass end='' to the first print() call. A second print() call prints the band of asterisks. The time.sleep() function hasn’t been covered yet, but suffice it to say that it introduces a one-tenth-second pause in our program at this point.

        if indentIncreasing:  
            # Increase the number of spaces:  
            indent = indent + 1  
            if indent == 20:  
                indentIncreasing = False # Change direction.

Next, we want to adjust the amount of indentation for the next time we print asterisks. If indentIncreasing is True, then we want to add one to indent. But once indent reaches 20, we want the indentation to decrease.

        else:  
            # Decrease the number of spaces:  
            indent = indent - 1  
            if indent == 0:  
                indentIncreasing = True # Change direction.

Meanwhile, if indentIncreasing was False, we want to subtract one from indent. Once indent reaches 0, we want the indentation to increase once again. Either way, the program execution will jump back to the start of the main program loop to print the asterisks again.

except KeyboardInterrupt:  
    sys.exit()

If the user presses CTRL-C at any point that the program execution is in the try block, the KeyboardInterrrupt exception is raised and handled by this except statement. The program execution moves inside the except block, which runs sys.exit() and quits the program. This way, even though the main program loop is an infinite loop, the user has a way to shut down the program.