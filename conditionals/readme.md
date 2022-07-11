# javascript

## conditional Algorithms

Conditional statements control behavior in JavaScript and determine whether or not pieces of code can run.

-There are multiple different types of conditionals in JavaScript including:

---

## **1-“if” statements:**

- Use if to specify a block of code to be executed, if a specified condition is true.

- the if statement only runs if the condition enclosed in parentheses () is truthy.

#### **Syntax:**

    if (condition) {

     //  block of code to be executed if the condition is true

    }

#### **Example:**

    if (10 > 5) {
        console.log("if block");
    }

output:

    "if Block"

Here’s what’s happening in the example above:

- The keyword if tells JavaScript to start the conditional statement.
- (10 > 5) is the condition to test, which in this case is true — 10 is greater than 5.
- The part contained inside curly braces {} is the block of code to run.
- Because the condition passes, the variable outcome is assigned the value "if block".

---

## **2- The “else” statement:**

- Use the else statement to specify a block of code to be executed if the same condition is false.

- You can extend an _if statement_ with an _else statement_, which adds another block to run when the _if_ conditional doesn’t pass.

#### **Syntax:**

    if (condition) {
        //  block of code to be executed if the condition is true

    } else {
       //  block of code to be executed if the  condition is false

    }

#### **Example:**

    if ("cat" === "dog") {
        console.log("if block");

    } else {
        console.log("else block");
    }

output:

    "else block"

In the example above, "cat" and "dog" are not equal, so the else block runs and the variable outcome gets the value "else block".

---

## **3- The “else if” statement:**

- Use the _else if_ statement to specify a new condition to test, if the first condition is false.

- You can also extend an _if_ statement with an _else if_ statement, which adds another conditional with its own block.

#### **Syntax:**

    if (condition1) {

       //  block of code to be executed if condition1 is true

    } else if (condition2) {

       //  block of code to be executed if the  condition1 is false and condition2 is true

    } else {

       //  block of code to be executed if the condition1 is false and condition2 is false

    }

#### **Example:**

    const age = 25;

     if  ( age < 12 ) {

         console.log("child")

     } else if ( age >= 18 ) {

         console.log("adult")

     } else {

         console.log("teenager")

     }

output:

      "adult"

You can use multiple _if else_ conditionals, but note that JavaScript skips any remaining conditionals after it runs the first one that passes.

---

## **4- The “switch” statement:**

- Use the switch statement to select one of many code blocks to be executed.

#### **Syntax:**

    switch(expression) {

      case x:
        // code block
        break;

      case y:
        // code block
        break;

      default:
        // code block
    }

This is how it works:

- The switch expression is evaluated once.
- The value of the expression is compared with the values of each case.
- If there is a match, the associated block of code is executed.
- If there is no match, the default code block is executed.

#### **Example:**

    var flower = "tulip";

    switch (flower){
        case "rose":
            console.log("Roses are red");
            break;

        case "violet":
            console.log("Violets are blue");
            break;

        case "sunflower":
            console.log("Sunflowers are yellow");
            break;

        default:
            console.log("Please select another flower");
    }

What is happening in the example above is that the _switch_ statement will evaluate the value of the variable flower and then compare it with each _case_ clause to see if it returns true:

- The first _case_ will compare if flower === "rose"
- The second _case_ will compare if flower === "violet"
- The third _case_ will compare if flower === "sunflower"
- finally, when all three _case_ clauses return false , the _default_ case will be executed

output:

    "Please select another flower"

### _The default Keyword:_

- The _default_ keyword specifies the code to run if there is no case match.
- The _default_ case is optional, meaning you can simply run through the _switch_ statement without generating any output. But it's always better to include one _default_ case so that you know the _switch_ statement is properly executed by JavaScript.
- You can only include one _default_ case in a switch statement, or JavaScript will throw an error.

### _The break Keyword:_

- you need to include the break keyword in each case clause's body to stop the switch statement's execution once a matching case is found.
- If you omit the break keyword, JavaScript will continue to evaluate the expression until the last case clause.

#### **Example:**

    var flower = "rose";

    switch (flower){
        case "rose":
            console.log("Roses are red");

        case "violet":
            console.log("Violets are blue");

        case "sunflower":
            console.log("Sunflowers are yellow");

        default:
            console.log("Please select another flower");
    }

what will happen in this example above?

- The code above will print both "Roses are red" and "Please select another flower" because the break keyword is omitted from the case clauses, causing JavaScript to continue the expression comparison down to the last case, which is the default case.

- Even when the expression "rose" already found a match in the first case clause, JavaScript still continue running the switch statement because there is no break keyword.

**Note:**

it is not necessary to include the _break_ keyword in the last case, because the _switch_ statement will be executed completely by then.

### Summary:

here's how a _switch_ statement works:

- First, you need an expression that you want to compare with some conditionals.
- Then, you write all the conditionals to compare with the expression in each case clause, including a default case when there is no matching case
- Finally, write the code that you want to execute inside each case, followed by the break keyword to stop JavaScript from further comparing the expression with the case clauses.

When to use the switch statement:

- Both the switch statement and if..else statement are used to create conditionals.

but the difference between them is that:

- the _switch_ statement is only used when you have _**a precise value**_ for the conditionals.

while the _if..else_ statement can be used to compare an expression with _**an imprecise value**_ such as larger than or smaller than.

    var score = 70;

    if(score > 50){
        console.log("Score is higher than 50");

    } else {
        console.log("Score is 50 or lower");
    }

But you can't use score > 50 as a condition for a _case_ clause.

---

## Logical Operators and _if.. else_ statements in JavaScript:

### 1- The logical AND (&&) operator:\*\*

- The logical AND (&&) operator (logical conjunction) for a set of boolean operands will be true if and only if all the operands are true. Otherwise it will be false.
- In the logical AND (&&) operator, if both conditions are true, then the if block will be executed.
- If one or both of the conditions are false, then the else block will be executed.
- If you want to test multiple conditions without writing **_nested if...else_** statements, logical operators can help you.

### Syntax:

    if (expr1 && expr2) {

        // block of code to be executed if both of the expressions are true

    }

### Example:

     const x = 6;

     const y = 3;

     if (x < 10 && y >= 1) {
         console.log("the if statement is true")
     }

output:

    "the if statement is true"

the same example with nested if .. else statement would be:

    const x = 6;

    const y = 3;

    if (x< 10) {

        if ( y >= 1){

            console.log("the if statement is true")
        };
    }

### 2- The logical OR ( || ) operator:\*\*

- In the logical OR (||) operator, if one or both of the conditions are true, then the code inside the if statement will execute.

### Syntax:

    if (expr1 || expr2) {

          //  block of code to be executed if one or both of the expressions are true

    }

### Example:

    const vaccinated = false;
    const  negative = true;

    if (vaccinated || negative) {
        console.log("is allowed to enter the store")
    }

output:

    "is allowed to enter the store"

---

### A note on comparison operators:

Comparison operators are used to test the conditions inside our conditional statements. Our choices are:

- **_=== and !==_** : to test if one value is identical to, or not identical to, another.
- **_< and >_** : to test if one value is less than or greater than another.
- **_<= and >=_** : to test if one value is less than or equal to, or greater than or equal to, another.

---

## Ternary operator:

- The ternary or conditional operator is a small bit of syntax that tests a condition and returns one value/expression if it is true, and another if it is false.
- this can be useful in some situations, and can take up a lot less code than an if...else block if you have two choices that are chosen between via a true/false condition.

### Syntax:

    ( condition ) ? run this code : run this code instead

The condition goes before the ? mark and if it is true, then the code between the ? mark and : would execute. If the condition is false, then the code after the : would execute.

### Example:

    const age = 32;

    const citizen = age >= 18 ? "Can vote" : "Cannot vote";

    console.log(citizen);

output:

     "Can vote"

This is what the code would look like using an if else statement:

    const age = 32;

    let citizen;

    if (age >= 18) {

        citizen = "Can vote";

    } else {

        citizen = "Cannot vote";

    }

    console.log(citizen);

---

## Summary:

- if else statements will execute a block of code when the condition in the if statement is truthy. If the condition is falsy, then the else block will be executed.

- There will be times where you want to test multiple conditions and you can use an if...else if...else statement.

- If you feel like the if else statement is long and complicated, then a switch statement could be an alternative option.

- Using logical operators to test multiple conditions can replace nested if else statements.

- The ternary operator can be used to write shorter code for a simple if else statement.
