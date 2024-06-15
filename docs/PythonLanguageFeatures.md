While you do not need to know everything about Python syntax, you should know enough to recognize the particular language features that generated code is using.

## Modules
One of the most important facets of Python is the ecosystem of modules that people have created to solve a diverse array of problems. You can import these modules into your code so that you don’t have to code your own solution. Python’s standard library has many modules for working with the most common types of problems. Other modules need to be downloaded and installed separately. If you have ArcGIS Pro installed, you already have Python environment with about 200 additional modules installed. 

You can import all the functionality of a module with a simple import statement, which will look something like:

``` py 
import csv
```

You can also import just a part of a module’s functionality by specifying those parts, which will look something like:

``` py
from arcgis import features
```

You should be able to recognize what it means when the model produces code that imports a module. Because the capabilities of a model cannot be used unless the module is imported, you will also need to recognize when the model has created code that makes use of a module, but has not also written the appropriate import statement.

## Data types
Different types of values have different capabilities. For example, you can’t multiply a piece of text by another piece of text. You should recognize the data types created by the model. The table below shows the most common general Python data types.

| Data type  | Description                                                                                                           | Examples                     |
| ---------- | --------------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| Integer    | Whole numbers                                                                                                         | `80`, `-2`                   |
| Float      | Any numeric value                                                                                                     | `9.84`, `-1.0`               |
| Boolean    | Logical values                                                                                                        | `True`, `False`              |
| String     | A set of characters, generally representing text values. Enclosed in `"` or `'` quotes.                               | `"string"`, `'8'`, `"False"` |
| List       | Mutable ordered sequence of values. Enclosed in `[]` brackets                                                         | `[1, 2, 3, 4, 5, 6]`         |
| Tuple      | Immutable ordered sequence of values. Enclosed in `()` parentheses.                                                   | `(1, 2, 3, 4, 5, 6)`         |
| Dictionary | Collection of key: value pairs. Enclosed in `{}` braces. Keys are usually strings or numbers. Values can be anything. | `{"MN": 1, "WI": 2}`         |

Lists, tuples, and dictionaries are containers for other values. Those values could be any other types, even other lists, tuples, or dictionaries. You can easily have a list of dictionaries, where each value in each dictionary is itself another list of dictionaries.

## Variables
Some values, like a long list or heavily nested dictionary, are very complex and hard to work with directly. It can be convenient to give values a name and refer to that value by its name instead. These variable names can also imbue a value with meaning for anyone reading the code. A good name can help us understand better what the code is doing. Values are assigned to variable names using the assignment operator (=). For example:

``` py linenums="1"
capital = "Saint Paul"
population = 5717000
is_wisconsin = False
```

## Blocks
A block is a chunk of connected code that performs a task. You can recognize a block because the first line will end with a colon (:) and the rest of the block will be indented one level relative to the first line. It is possible to have blocks inside of blocks.

### Conditional blocks 
Allow you to deal with branching logic in your code. Conditional statements check the truth value of a statement, and if it is true, execute the code in the rest of the block. You can recognize a conditional by the use of the `if`, `elif` (else if) and `else` keywords. For example:

``` py linenums="1"
if capital == "Saint Paul":
    state = "Minnesota"
elif capital == "Madison":
    state = "Wisconsin"
else: 
    state = "Unknown"
```

This code snippet checks the value of `capital` against different possibilities. It first checks to see if the value is equal to `"Saint Paul"`. If so, it sets the value of `state` to `"Minnesota"`. If not, it checks to see if the value is equal to `"Madison"`. If so, it sets the value of `state` to `"Wisconsin"`. If `capital` is any other value, it sets the value of `state` to `"Unknown"`.

### For loops 
Allow for repeated code execution. You can recognize a for loop by the use of the `for` and `in` keywords. For example: 

``` py linenums="1"
seq = (1, 2, 3, 4, 5, 6)
big_seq = []
for num in seq:
    if num > 4:
        big_seq.append(num)
```

This code snippet starts with a tuple `seq` and an empty list `big_seq`. It looks at every value inside `seq` in order. If the value is bigger than 4, it appends that value to `big_seq`. After running this code, the value of `big_seq` will be `[5, 6]`. 

### Functions
Encapsulate some process so that the process can easily be repeated without having to write the code to perform that process again. Functions must be defined before they can be used. You can recognize a function definition by the use of the `def` keyword. A function will typically produce some value, specified by the `return` keyword. For example:

``` py linenums="1"
def dist(x1, y1, x2, y2):
    a_sq = (x2 - x1)**2
    b_sq = (y2 - y1)**2
    return (a_sq + b_sq)**0.5
```

This code snippet creates a function that calculates the Euclidean distance between two points, given their x,y coordinates. It uses to Pythagorean formula: first it calculates the square of the difference between the two x-coordinates (the `a_sq` value), then it calculates the square of the difference between the two y-coordinates (the `b_sq` value). Then it returns the square root of the sum of those squared differences.

After a function has been defined, it must be called in order to execute it. You can recognize a function is being called by the parentheses after its name. There may or may not be any values inside the parentheses. For example:

``` py
dist(0, 0, 1, 1)
```

This code snippet calls the `dist` function to find the distance between the point at coordinates 0,0 and the point at coordinates 1,1. It will return a value of approximately 1.41.

## Files
Sometimes the data we want to work with is stored outside the script, in files. You will need to open those files in order to work with the data inside them. You will recognize code that opens a file by the use of the `open` function, which specifies the file’s path and a mode (`'r'` for read, `'w'` for overwrite, `'a'` for append). As a best practice, opening files should be done in a context manager block, which you can recognize by the use of the `with` and `as` keywords. For example:

``` py linenums="1"
text_file = r'C:\temp\text.txt'
with open(text_file, 'r') as f:
    for line in f:
        print(line)
```

This code snippet will open the file located at C:\temp\text.txt and open it. The open file is stored in the `f` variable. It loops through every line in the file and prints out that line.

## Exercise: Identify programming features
1.	Navigate to the downloaded materials for this workshop
2.	Copy the file path for feature_quiz.py
3.	Open a command line program that can run Python scripts. If you have ArcGIS Pro installed, it will probably be easiest to use a program called Python Command Prompt that you can search for from the Start menu.
4.	At the command prompt, type python followed by the file path you copied. You may need to put quotes around the path. Ex: python "C:\Users\myuser\dave\feature_quiz.py"
5.	Answer the questions about Python features until you either feel confident that you can recognize all the features or you get bored
6.	Open feature_quiz.py in an editor of your choice (right-clicking on the file should present you with some opens to open it).
7.	Examine the code in the file. Which features do you recognize? Which features do you not recognize?

## Have the model summarize code features
If you have access to an LLM interface, like Copilot or ChatGPT, you can have the model summarize a chunk of code that uses Python features you do not recognize. LLMs tend to be much better at summarizing content than they are at generating it themselves, and the summaries are typically reliable. You can have the model summarize the code it generated for you, or code snippets you have found elsewhere.


