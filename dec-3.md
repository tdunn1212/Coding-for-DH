# Dec. 4 Notes (Module 5)
## Part One: Functions
- Perform blocks of reusable code meant to perform specific tasks
- Can be called at any time
- Built in functions are print() and type()
- type `def name(variable1,variable2):`
```
def calculate_length_of_time(start_year, end_year):
length_of_time = int(end_year) –
int(start_year)
return length_of_time
```
- To use this function, you would call it: calculate_length_of_time(“1899”, “1902”)
- Functions are useful for when there's something you think you'll be repeating multiple times in your code to minimize repitition 
- **Calling from a list of lists:** function = variable [higher list position][lower list position]
- isdigit(): determines if a string value is numerical
- isalpha(): determines if a string value is alphabetical
- Example
```
# find age of each person from records
life_records = [["Cindy Salter", "Born: 1903", "Died: 1933"], 
                ["Glynis Graves", "Born: 1911", "Died: 1989"], 
                ["Noel Boardman", "Born: 1908", "Died: 1972"]]

def find_age(record):
    born = '' #these variables have empty values so we can declare them before the for loop to use it outside of them 
    death = ''# this is like declaring an empty list to use later
    for word in record[1].split():
        if word.isdigit():
            born = int(word)

    for word in record[2].split():
        if word.isdigit():
            death = int(word)

    age = record[0] + "'s age: " + str(death - born)
    return age

print(find_age(life_records[0])) # declares that life record 0 is the record variable
print(find_age(life_records[1]))
print(find_age(life_records[2]))
```
## Part Two: Libraries/Packages
### NLTK
- *Collections of large pre-written functions that allow you to install them in your Python environment and import their functions into your code*
- Pre-written code is like using prepared meal kits
- We "wrangle" or prepare for analog text analysis by printing materials, formatting them, making sure there's no immediate errors, and gathering your tools
- **Using Libraries is preferable to making your own functions, since it removes the complications of creating your own functions**
- **The Natural Language Toolkit** is is an all-encompassing library to support work in natural language processing (NLP), a multidisciplinary field which deals with the interactions between "natural" human language and computers
  - the original code lists 20 most common stopwords and you can add stop words
  - it also allows for tokenizing,  splitting up a larger body of text into smaller lines or words
  - Here's the link to their documentation: [click here](https://www.nltk.org/)
  - NLTK uses Penn Treebank Part of Speech tagging, found [here](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html)
- Using pre-written code/libraries is especially useful for larger text-analysis, to shorten your code substantially and remove areas of complication
- We can tokenize strings and text files into words and sentences, break them down into Parts of Speech (POS), and remove stopwords from these text files
Example code: 
- now remember that huge block of stopwords manually typed out in the sample block of code from the first lesson? That comes built in to NLTK as you may have guessed from the earlier import statment
- we can assign the NLTK stopwords to a variable like so:
```
stop_words = stopwords.words('english')

(and then remove the stopwords from out text using a loop to check if each word in the transcript and only keep the words that are NOT in out stopword list)
filtered_transcript_words = []
for word in transcript_words:
    if word not in stop_words:
        filtered_transcript_words.append(word)
```
Finally, we can simply find word frequeny with NLTK's frequnecy distribution function:
```
from nltk import FreqDist

transcript_fdist = FreqDist(filtered_transcript_words)
transcript_fdist.most_common(10)

```
- This would create a frequency distribution list that is topped by punctuation, so we can extend our stopwords to fix this!
```
from string import punctuation
punctuation = list(punctuation)

# and luckily, you can modify your stopwords and punctuation lists like any other list!
# let's add "n't", "'s", and "would"
# to add multiple elements to a list at once, we use extend() rather that append()
stop_words.extend(["n't", "'s", 'would'])
```
**Here's the final code that gives you frequency distribution:**
```
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords

from string import punctuation
punctuation = list(punctuation)

nltk.download('punkt_tab')
nltk.download('stopwords')

transcript = open('Bette-Smith-Transcript.txt', encoding="utf-8").read().lower()

transcript_words = word_tokenize(transcript)

stop_words = stopwords.words('english')
stop_words.extend(["n't", "'s", 'would'])

filtered_transcript_words = []
for word in transcript_words:
    if word not in stop_words and word not in punctuation:
        filtered_transcript_words.append(word)

transcript_fdist = FreqDist(filtered_transcript_words)
transcript_fdist.most_common(10)
```
- For lit reviews, writing up lit reviews and having codes and reproducibility is super important- talk to Martha about this!

##### Practice Activity with Hamlet
```
import nltk

from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords

from string import punctuation
punctuation = list(punctuation)

nltk.download('punkt_tab')
nltk.download('stopwords')

transcript = open('hamlet.txt',encoding="utf-8").read().lower()

transcript_words = word_tokenize(transcript)

stop_words = stopwords.words('english')
stop_words.extend(["n't", "'s",'footnote','_ham._','--',"'d",'_i.e._','shall','project','thy','come','thou','may','r.',"_hor._",'_king._',"'ll",'_pol._','let','would','upon','must','c.','make',"'t",'gutenberg™','go',"well","_and_",'us'])
# had to add 28 stop words

filtered_transcript_words = []
for word in transcript_words:
    if word not in stop_words and word not in punctuation:
        filtered_transcript_words.append(word)

transcript_fdist = FreqDist(filtered_transcript_words)
transcript_fdist.most_common(10)

# from nltk.text import Text

# text_list = Text(transcript_words)
# text_list.concordance("king", lines=82)
```
Provides results:
('lord', 157),
 ('hamlet', 127),
 ('king', 82),
 ('good', 78),
 ('time', 65),
 ('horatio', 56),
 ('father', 56),
 ('work', 56),
 ('speak', 55),
 ('queen', 54)
### Pandas
- **Pandas is a library with prewritten code for tabular data analysis. Pandas is a Python package for exploring, cleaning, and processing tabular data or dataframes (as data tables are defined in Python)**
- Pandas works in `dataframe` format, which is the Python version of a spreadsheet, to perform data analysis and manipulation
  - Like a spreadsheet, each column can be of a different type, and using Pandas means we can quickly perform a number of operations on our `dataframe` to prepare our data for use in analysis.    
- Pandas simplifies code for data that is in tabular format
  - this can be any data type
  - we will use strings
- Here are helpful Pandas resources:
  - [Pandas in 10 minutes](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)
  - [Getting started in Pandas](https://pandas.pydata.org/docs/getting_started/index.html)
- You can turn individual columns into list variables by calling them as such: `witches_residence = list(witches_df['res_county'])`
- We can update column values and filter out rows that have no data
- using `witches_df["occupation"].value_counts()` with our example, you can count particular values of certain categories based on your data, this would get us the frequency of occupations
- `.describe` gets you the numerical data about numerical columns in your data
- The `.fillna("")` function replaces all blank cells with text of your choice

**Important Example for Final Case Study:**
turning the notes column into a list and back into a string that has these in a list
```
historian_notes=list(witches_df['notes'])

all_notes=""

for note in historian_notes:
    if note != 'unknown':
        all_notes += note + '\n'

print(type(all_notes))
print(all_notes)
```