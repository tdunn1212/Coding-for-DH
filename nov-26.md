# Nov. 26 Notes (Module 4)
## Part One: Basic Structure of Python Code
- Creating an object is made up of parts
    1. Variables (store data types)
        - variable names can have numbers in them, just not at the start
    2. Pre-installed commands/methods
    3. Solutions/conditionals
- Question: does python automatically select the variable type? Yes it does, you don't have to assign them
- You can comment things out with Cmd + / or with # 

### Variables
- Integers: store whole numbers (and equations)
- Floats: store decimal numbers (and equations)
- Strings: store text in quotation marks
- Lists: series of numbers/text
  - Syntax is `name = ["name","name", etc.]
- you can use the type() function to check the type of your variables

### Operators
|Operator|Meaning|
|---|---|
|==|Equal to|
|!=|Not equal to|
|<|Less than|
|>|Greater than|
|<=|Less than or equal to|
|>=|Greater than or equal to|
**Boolean Operators:**
- The 3 key boolean operators are simply `and`, `or`, and `not`. 
- `and` means both values must evaluate to true to return true
- `or` means that one or both values must evaluate to true to return true
- `not` is used to flip the boolean value following it (e.g. `not False returns true`)

## Part Two: Conditions
The `if` statement is the most basic way to tell your computer to do something independently. To verbalize the concept, you're telling the computer "If this condition I specified is met, then do this thing." To specify the condition? You use comparison and boolean operators!

**Syntax**
```
if variableX == variableY:
    print(yippee true)
elif variableX == variableZ:
    print(also true)
else:
    print(bad, false)
```

**Syntax Example:**
```
surname = "Young"

if surname == "Dowling" and birth_year == 2007:
    print(surname + ", " + str(birth_year))
else: 
    # since the surname is "Young" rather than "Dowling", the computer skips to the else statement and performs that action instead
    print("The surname or birth year is incorrect.")
```

**Syntax with else if or `elif`:**
```
if surname == "Dowling" and birth_year == 2007:
    print(surname + ", " + str(birth_year))
elif surname == "Dowling" or birth_year == 2007:
    # you can nest if statements to create more descriptive outputs! This if statement determines if either the surname or year is False/incorrect. 
    if surname == "Dowling":
        print("The year is incorrect.")
    else:
        print("The surname is incorrect.")
else: 
    print("Person not found")
```

## Part Three: Loops
- Loops instruct the computer to repeat conditional statements/tasks (e.g. going through a text multiple times to find answers)
- Code uses true/false answers to express the right instructions for this process.
- Loops are executed based on certain condition(s)
- For (item you'd like to iterate over): perform action
- For DH processes, loops are good to allow you to search a large amount of data very quickly
- While loops allow you to search over something while its condition is set to true and stops when it is set to false; we will not use these
**For Loop Pseudocode:**
```
for every sentence on this page:
    if this is the quote I am looking for:
        I can stop reading, I've found it!
    if this isn't the quote:
        Let's read the next sentence.
```
**Syntax:**
```
for variableX in listY:
    print(variableX[1])
    # this can also be an if statement or other function
```
**Syntax Example:**
```
only_dobsons = []

for name in list_of_names:
    # we check if this name includes "Dobson"
    if "Dobson" in name:
        # if this is True, we add this name to our new list
        only_dobsons.append(name)

print(only_dobsons)
```
- It's good practice to define a variable inside the for loop, since that variable is updated with every iteration of the list
```
for name in list_of_names:
    print(name)

# NOTE: "name" is a variable declared only in the loop, and it stores the item that the loop is presently looking at
# in our case, in the first loop "name" = "George Atherton", and then after that name is printed, the loop repeats and "name" = "Marian Hyde", in the next loop "name" = "Sybil Dickenson", and so on until the end of the list
```

**Practice Activity**
```
little_women_quotes = [
                        "...I do think washing dishes and keeping things tidy is the worst work in the world. It makes me cross; and my hands get so stiff, I can't practise well at all.",
                        "I don't see how you can write and act such splendid things, Jo. You're a regular Shakespeare!",
                        "But it does seem so nice to have little suppers and bouquets, and go to parties, and drive home, and read and rest, and not work. It's like other people, you know, and I always envy girls who do such things; I'm so fond of luxury",
                        "She caught up her knitting, which had dropped out of her hands, gave me a sharp look through her specs, and said, in her short way, 'Finish the chapter, and don't be impertinent, miss.'",
                        "You may try your experiment for a week, and see how you like it. I think by Saturday night you will find that all play and no work is as bad as all work and no play."
                    ]

work_quotes=[]

# for quote in little_women_quotes:
#      if "work" in quote:
#        print("'",quote,"'")

for quote in little_women_quotes:
    if "work" in quote:
        work_quotes.append(quote)

for quote in work_quotes:
    print(quote)
```
This prints: 
...I do think washing dishes and keeping things tidy is the worst work in the world. It makes me cross; and my hands get so stiff, I can't practise well at all.
But it does seem so nice to have little suppers and bouquets, and go to parties, and drive home, and read and rest, and not work. It's like other people, you know, and I always envy girls who do such things; I'm so fond of luxury
You may try your experiment for a week, and see how you like it. I think by Saturday night you will find that all play and no work is as bad as all work and no play.

### Homework: Thoughts on the Python documentation website
- Doesn't feel very accessible as a super beginner... I don't know where to start
