# Nov. 19 Notes (Module 3)

## Part One - Humanistic Coding

- Submit link to Markdown notes/GitHub
- Pushing to GitHub syntax:
  - `git add -A`
  - `git commit -m "message"`
  - `git push`

### Analog Coding in the Humanities
- Analog coding interprets texts according to their themes, patterns, and connections
- there are a variety of approaches and methods of analog coding

##### Activity: Reading an interview transcript to find themes and frequent ideas
- Highlight the instances of gendered words/phrases
- Do a word frequency count based on that

###### Findings:
- Words either matched a more general gendered theme or more general labouring theme
- the word family (4) and various conjugations of work (9) were the most frequent.
- the theme of domestic words had 12 instances, whereas labouring had 15 instances
- Our coding methods were similar in their findings, but had different methodologies in our processes
- Divorcing words from their context was challenging
- **Every group performed analysis differently even though they found the same concepts and results**
- We could also encode based on sentiment (positive/negative), action words, adjectives, etc.
- *Can computers code and analyze in the same way?*
  - They could be more reliable with things like word frequency, but understanding the nuance and sentiments of things like gender would not be possible in the same way

## Part Two - Literate Programming and Python
> “I believe that the time is ripe for significantly better documentation of programs and that we can best achieve this by considering programs to be works of literature ... the practitioner of literature programming can be regarded as an essayist, whose main concern is with exposition and excellence of style.”
 
  Donald Knuth, Literate programming (1984), p. 99

##### Python supports literary coding
- It is relatively accessible and can write unique and access existing codes
- It is useful for scraping text, creating small loops, and data analysis
- It integrates natural and computer languages
- Python is readable, easier to debug, and processes data quickly
- Its constraints are that its automation might reduce speed (it is less memory efficient than lower level languages), and it occasionally sacrifices machine-friendliness for the sake of human-friendliness.

##### Jupyter Notebook
- A Python coding environment
- Allows individual chunks of code to be run, and keeps projects in one place rather than individual files
- allows commentary to be added to code via Markdown, making it *reproducible*
  - this is a big DH component
- Our uses will `git clone` notebooks to use in the workshops

#### Analyzing Python Code
##### What are your observations and thoughts based on the code provided?
###### What's happening in the code?
- The Python code is opening a text file, reading words in it (with the exception of stopwords), and tallying how frequently they appear in the text file.
- what does text split regex mean?
###### What problem is being solved?
- This code is solving the problem of looking for word frequencies and patterns in the Bette Smith transcript
- That makes the process much easier and eliminates possibilities for human oversight
- Allows for automated text analysis, which helps with larger files
###### What are the elements/computational tasks of the code?
- Importing the python libraries that contain universal functions (like counter)
- Naming the variables
- Naming the stop words that don't relate to the theme in a list variable
- Reading the file
- Transforming the string into a list (?)
- Removing the "stop words"
- Tallying the significant words and putting them into a list in order of their frequency
##### What are challenges of coding? Is your code literate?
- We didn't understand the function of converting the string into a list
- It's hard to implement comments into your work while you're coding, but without this step, your code is not easily replicated for yourself and for others
- I would say that this code is literate, but I also have prior knowledge

###### Steps Based on Instructors
1. Importing a library that allows us to parse words, and a function that counts items in a list (both libraries are built in)(1-2)
2. declaring a string variable that names the filepath of a text file for later, then declares an integer of 50 (we will call back to it later without having to declare it). (4-8) Then, declaring a list of stopwords for later.(11-25)
   - Declaring these variables prevents us from having issues with having to call them within our separate functions, making the functions more readable
3. Declaring a variable that instructs our code to open the file with UTF-8 encoding, then reading all the text as lowercase
4. Declaring a variable that calls on the regex library that splits all the text in the file as its own individual word variable(31)
5. Declaring an empty list variable for us to use later (35)
6. Making a for loop, for every word in the text string that is not in the stopword and is an alphabetical character, we add it to the empty word list (for the entire length of the file if it meets conditions) (37-9)
7. Counting the instances of the significant words (42)
8. Counting the 50 most common words based on our integer variable (43)
9. Printing the list with the counts associated with their instances (top 50)(line 45)

## Part Three - Python Fundamentals
### Computational Mindset
- As literate programmers, your approach should be changed to problem solvong, and you need to rethink how you want the computer to answer your questions in its binary methods
- Computers only work in 1s and 0s
[text flow analysis chart of annotating a source](3.3-slide.png)
