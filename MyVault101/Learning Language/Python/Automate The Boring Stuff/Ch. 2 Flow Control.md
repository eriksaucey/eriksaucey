Comparison Operators
![[python_operators_2.jpg]]

Evaluate to true or false 
	42 == 42
True
	42 == 99
False
	2 != 3
True
	2 != 2
True

== compares two values to see if they are the same
= Assigns the right value to the left variable

Boolean Operators

and, or. not

The and operator evaaluates an experession to True if both Boolean values are true

The Truth Table for "And" Operator
	True and True = True
	True and False = False
	False and True = False
	False and False = False
	

The Truth Table for "Or" Operator
	True or True = True
	True or False = Tue
	False or True = True
	False or False = False

The Truth Table for "Not" Operator
	not True = false
	not False = True

Flow Control Statements

If Statement
	The "if" statements clause will execute if the statements condition is true
	The clause is skipped if the condition is false
		Ex:
			if name == 'Alice':  
			    print('Hi, Alice.')
All flow control statements end with a colon and are followed by a new block of code called the clause

![[python_flow_1.jpg]]

else Statements
An if clause can be followed by an else statement. Else is executed when the if statements condition is False

Ex:
	if name == 'Alice':  
	    print('Hi, Alice.')  
else:  
    print('Hello, stranger.')

![[python_flow_2_Else.jpg]]

elif Statements
Else if statement that always follows an if or another elif statement
	Provides another condition that is checked only if all previous conditions were false

Ex:
	if name == 'Alice':  
	    print('Hi, Alice.')  
	elif age < 12:  
	    print('You are not Alice, kiddo.')

![[python_flow_2_elif.jpg]]

Order of elif statements MATTERS
____________________
   name = 'Carol'  
   age = 3000  
   if name == 'Alice':  
       print('Hi, Alice.')  
   elif age < 12:  
       print('You are not Alice, kiddo.')  
➊ elif age > 100:  
       print('You are not Alice, grannie.')  
   elif age > 2000:  
       print('Unlike you, Alice is not an undead, immortal vampire.')
____________________
Running this will cause an unexpected error

Putting "else" at the end of the last elif statement will guarantee at least one of the clauses will be executed

________________________________
name = 'Carol'  
age = 3000  
if name == 'Alice':  
    print('Hi, Alice.')  
elif age < 12:  
    print('You are not Alice, kiddo.')  
else:  
    print('You are neither Alice nor a little kid.')
________________________________
 While Loop Statements
 While statements let you execute a block of code over and over  again
Executed as long as the while statement is TRUE 
_______________
spam = 0  
if spam < 5:  
    print('Hello, world.')  
    spam = spam + 1

**With a "while" statement**

spam = 0  
while spam < 5:  
    print('Hello, world.')  
    spam = spam + 1
_____________________________________
For the if statement, the output is "Hello, world."

For the while statement, it's "Hello, world." repeated x5