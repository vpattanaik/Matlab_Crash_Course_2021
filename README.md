# Get Started with MATLAB

**MATLAB** (viz. "matrix laboratory") is a programming language and numeric computing environment. The MATLAB language is a matrix-based language that allows matrix manipulations, plotting of functions and data, implementation of algorithms, creation of user interfaces, and interfacing with programs written in other languages.

## Matlab UI

![MATLAB Desktop](/images/desktop.png)

The desktop includes these panels *(see figure)*:

- **Current Folder** *(Left)* — Access the files in the current folder.
- **Command Window** *(Center)* — Enter commands at the command line, indicated by the prompt (>>).
- **Workspace** *(Right)* — Explore variables that have been created or imported from files.

To begin using MATLAB, simply type the code (example: `A = 1`) in the **Command Window** and hit ENTER. To run multiple lines of code sequentially, one can write the codes into a *script* (*.m) file.

To create a new script, goto **HOME** -> Click **New Script**. A file named 'Untitled' should show up in the **Editor** panel. To save the file in the current folder, goto **EDITOR** -> Click **Save**. Type in a *File name* and click *Save*. The *m*-file should now be visible in the **Current Folder** panel.

Now type `A = 1` in the *m*-file inside the **Editor** panel, go to **EDITOR** -> Click **Save**. Doing so would save the file, now to run the *m*-file, goto **EDITOR** -> Click **Run**. The results should be visible in the **Command Window**, and the variables from the *m*-file should be visible in the **Workspace** panel (see screenshot).

![MATLAB Illustration](/images/desktop_illustration.png)

### Useful Shortcuts
 - **Create** new script [`Ctrl + N`]
 - **Save** script [`Ctrl + S`]
 - **Run** script [`F5`]
 - **Abort** running script [`Ctrl + C`]
 - **Comment/Uncomment** text [`Ctrl + R`/`Ctrl + T`]

### Useful Commands
 - **Clear** the Command Window [`clc`]
 - **Remove items** from workspace, and free up system memory [`clear all`]
 - **Close** one or more figures [`close all`]
 - **Help** for functions in **Command Window** [`help`]

### Getting Help
Typing `help *function name*` in the **Command Window** displays the help text for the functionality specified by name, such as a function, method, class, toolbox, or variable.

```matlab
help delete
```

*Output:*
```matlab
delete Delete file or graphics object.
     delete file_name deletes the named file from disk. Wildcards
     may be used. For example, delete *.p deletes all P-files from the
     current directory. 
     ...
```

Another method for getting `help` is to *right-click* on the command in **Command Window** and click **Help on Selection**. Or simply click on the command code and press `F1`. Alternatively, one can search for functions by using the **Search Documentation**. Simply type what you are searching for and hit ENTER.

## Initializing Variables

To initialize a variable, simply type the statement in the **Command Window**,

```matlab
a = 1
```

MATLAB will add the variable *a* to the workspace and display the result in the Command Window.

*Output:*
```matlab
a = 

     1
```

When you do not specify an output variable, MATLAB uses the variable *ans* (short for answer) to store the results of your calculation.

```matlab
sin(a)
```

*Output:*
```matlab
ans =

    0.8415
```

If you end a statement with a ; *(semicolon)*, MATLAB will performs the computation, but suppress the display of output in the **Command Window**.

```matlab
b = (sin(a)) ^ 2;
```

To see the value of *b* in **Command Window**, type *b*.

*Output:*
```matlab
b =

    0.7081
```

To recall previous commands pressing the ↑ (up-arrow) and ↓(down-arrow) keys.

### Data Types

Here are some useful data types supported in MATLAB.

| Type | Description | Specifier |
|------|-------------|----------------------|
| `char` | Character array | `%c` |
| `double` | Double-precision floating point | `%f` |
| `int8`, `int16`, `int32`, `int64` | Signed integer | `%d` |

MATLAB does not require the user to specify the data type of a variable.

Examples:

-    ```matlab
     chr = 'a';
     whos chr
     ```

     *Output:*
     ```matlab
     Name      Size            Bytes  Class    Attributes

     chr       1x1                 2  char  
     ```

-    ```matlab
     str = 'Hello, world';
     whos str
     ```
     *Output:*
     ```matlab
     Name      Size            Bytes  Class    Attributes

     str       1x12               24  char  
     ```

`whos` displays information about specific variables in the current **Workspace**.

## Adding Comments to Script
To add comments to MATLAB code, use the *%* (percent) symbol. Comment lines can appear anywhere in a program file, also at the end of a line of code. Like so,

```matlab
% Add up all the vector elements.
y = sum(x) % Use the sum function.
```

To comment out multiple lines of code, use the block comment operators, *%{* and *%}*. The *%{* and *%}* (percent symbol with curly braces) operators must appear alone on the lines that immediately precede and follow the block of help text. Do not include any other text on these lines.

```matlab
a = magic(3);
%{
sum(a)
diag(a)
sum(diag(a))
%}
sum(diag(fliplr(a)))
```

To break down script-code into chunks or *Code Sections*, use *%%* (two percent signs) at the start of the line where you want to begin the new code section.

Type the code below in the *m*-file,

```matlab
%% Calculate and Plot Sine Wave
% Define the range for x.
% Calculate and plot y = sin(x).
x = 0:1:6*pi;
y = sin(x);
plot(x, y)

%% Modify Plot Properties
title('Sine Wave')
xlabel('x')
ylabel('sin(x)')
fig = gcf;
fig.MenuBar = 'none';
```

The code has two sections, like so.

![Code Sections](/images/code_sections.png)

## Matrices and Arrays

MATLAB is designed to operate primarily on whole matrices and arrays. All MATLAB variables are multidimensional arrays, no matter what type of data.

```matlab
a = [1 2 3 4]
```

*Output:*
```matlab
a =

     1     2     3     4
```

An row vector is called an *array*, while a two-dimensional *array* is called a *matrix*. To create a matrix that has multiple rows, separate the rows with *;* (semicolons).

```matlab
a = [1 2 3; 4 5 6; 7 8 10]
```

*Output:*
```matlab
a =

     1     2     3
     4     5     6
     7     8    10
```

To create arrays with sequential numbers use *:* (colon), to indicate range.

```matlab
b = [1:5]
```

*Output:*
```matlab
b =

     1     2     3     4     5
```

To create matrices one can also use functions, like `ones`, `zeros`, or `rand`.

-    ```matlab
     z = zeros(5, 1)
     ```

     *Output:*
     ```matlab
     z =

          0
          0
          0
          0
          0
     ```

-    ```matlab
     o = ones(1, 5)
     ```

     *Output:*
     ```matlab
     o =

          1     1     1     1     1
     ```

-    ```matlab
     r = rand(2, 3)
     ```

     *Output:*
     ```matlab
     r =

     0.8147    0.1270    0.6324
     0.9058    0.9134    0.0975
     ```

`2` in the previous example indicates the number of `rows`, while `3` indicates the number of `columns`.

### Array Operations

All values in an array can be processed using a single arithmetic operator or function.

```matlab
a + 10
```

*Output:*
```matlab
ans =

    11    12    13
    14    15    16
    17    18    20
```

```matlab
a * 2
```

*Output:*
```matlab
ans =

     2     4     6
     8    10    12
    14    16    20
```

To transpose a array, use a *'* (single quote).

```matlab
a'
```

*Output:*
```matlab
ans =

     1     4     7
     2     5     8
     3     6    10
```

To apply an operator element-wise to the array, use *.* (dot) right before the operator.

```matlab
a .^ 2
```

*Output:*
```matlab
ans =

     1     4     9
    16    25    36
    49    64   100
```

### Matrix multiplication vs. Element-wise multiplication

-    ```matlab
     a * a
     ```

     *Output:*
     ```matlab
     ans =

     30    36    45
     66    81   102
     109   134   169
     ```

-    ```matlab
     a .* a
     ```

     *Output:*
     ```matlab
     ans =

          1     4     9
     16    25    36
     49    64   100
     ```

### Concatenating Arrays

Arrays can be joined together to make larger ones.

```matlab
A = [a, a]
```

*Output:*
```matlab
A =

     1     2     3     1     2     3
     4     5     6     4     5     6
     7     8    10     7     8    10
```

Using *comma* concatenates the second array after the last column of the first array, whereas *semicolon* does the same after the last row.

```matlab
A = [a; a]
```

*Output:*
```matlab
A =

     1     2     3
     4     5     6
     7     8    10
     1     2     3
     4     5     6
     7     8    10
```

### Array Indexing

```matlab
A = magic(3)
```

`magic(n)` returns an n-by-n matrix constructed from the integers 1 through n^2 with equal row and column sums.

*Output:*
```matlab
A =

     8     1     6
     3     5     7
     4     9     2
```

There are two ways to refer to a particular element in an array. First, is to specify row and column subscripts.

```matlab
A(2, 3)
```

*Output:*
```matlab
ans =

     7
```

Second, is to use a single subscript that traverses down each column. This is also called *linear indexing*.

```matlab
A(8)
```

*Output:*
```matlab
ans =

     7
```

If one tries to refer to elements outside an array on the right side of an assignment statement (like so, `test = A(4,5)`), MATLAB throws the error `Index exceeds matrix dimensions`. However, on the left side of an assignment statement, one can specify elements outside the current dimensions. *The size of the array increases to accommodate the newcomers.*

```matlab
A(4, 5) = 17
```

*Output:*
```matlab
A =

     8     1     6     0     0
     3     5     7     0     0
     4     9     2     0     0
     0     0     0     0    17
```

To refer to multiple elements of an array, use the colon operator, which allows you to specify a range of the form `start:end`.

```matlab
A(1:3, 2)
```

*Output:*
```matlab
ans =

     1
     5
     9
```

The colon alone, without start or end values, specifies all of the elements in that dimension.

```matlab
A(3, :)
```

*Output:*
```matlab
ans =

     4     9     2     0     0
```

The colon operator also allows you to create an equally spaced vector of values using the more general form `start:step:end`.

```matlab
B = 0:10:100
```

*Output:*
```matlab
B =

     0    10    20    30    40    50    60    70    80    90   100
```

## Plots

To create two-dimensional line plots, use the `plot` function.

-    ```matlab
     x = 0:pi/100:2*pi;
     y = sin(x);

     whos x;
     ```

     *Output:*
     ```matlab
     Name      Size             Bytes  Class     Attributes

     x         1x201             1608  double
     ```

-    ```matlab
     whos y;
     ```

     *Output:*
     ```matlab
     Name      Size             Bytes  Class     Attributes

     y         1x201             1608  double
     ```

     ```matlab
     plot(x, y)
     ```

![Simple Sine Plot](/images/simple_plot.png)

Add labels to plots like so,

```matlab
xlabel('x')
ylabel('sin(x)')
title('Plot of the Sine Function')
```

![Labelled Sine Plot](/images/labelled_plot.png)

To draw bar plots, use the `bar` function.

```matlab
bar(x(25:75), y(25:75))
```

Note that in the above example the plotted vectors in range 25:75 rather than 1:201.

![Sine Bar Plot](/images/sine_barplot.png)

To create a bar graph with one bar for each element in *y*, use `bar(y)`.

```matlab
y = [75 91 105 123.5 131 150 179 203 226 249 281.5];
bar(y)
```

![Single Element Bar Plot](/images/one_element_bar.png)

### Plotting Multiple Plots in One Window

By default, MATLAB clears the figure each time a plotting function is called. To add plots to an existing figure, use `hold on`. Use `hold off` to close all plots from appearing in the current figure window.

```matlab
x = 0:pi/100:2*pi;
y = sin(x);
plot(x, y)
hold on
y2 = cos(x);
plot(x, y2, ':m')
legend('sin', 'cos')
hold off
```

`:m` in the third-last line indicates that magenta coloured, dotted line.

![Multiple Plot in Figure](/images/multi_plot.png)

Line styles and colors can be indicated using these.

| Line Styles |  Colors |
|-------------|---------|
| Solid line `-`, Dashed line `--`, Dotted line `:`, Dash-dot line `-.` | yellow `y`, magenta `m`, cyan `c`, red `r`, green `g`, blue `b`, white `w`, black `k` |

## Conditional Statements

Conditional statements enable users to select at run time which block of code to execute. The simplest conditional statement is an `if` statement.

```matlab
a = randi([2, 100], 1);
```

`randi([imin, imax], n)` returns an array of size `n` containing integers between [imin, imax]. Alternatively, `randi(imax, n)` returns an `n-by-n` matrix of integers between the interval `[1, imax]`.

The code below checks if `a` is even and displays `a is even`.

```matlab
if (mod(a, 2) == 0)
     disp('a is even')
end
```

`mod(a,m)` returns the remainder after division of `a` by `m`, i.e., `a` is the dividend and `m` is the divisor. And, `disp(X)` displays the value of variable X without printing the variable name.

This code prints if `a` is even or odd number.

```matlab
if (mod(a, 2) == 0)
     disp('a is even')
else
     disp('a is odd')
end
```

`if` statements can include alternate choices, using the optional keywords `elseif` or `else`.

The code below prints if `a` is *small*, *medium* or *large*.

```matlab
if a < 30
     disp('small')
elseif a < 80
     disp('medium')
else
     disp('large')
end
```

**Learn about the `switch` conditional statement [here](https://se.mathworks.com/help/matlab/ref/switch.html).**

## Loop Control Statements

To execute a block of code repeatedly, use the `for` loop statement.

```matlab
for n = 1:5
     disp(n)
end
```

*Output:*
```matlab
     1

     2

     3

     4

     5
```

To nest multiple `for` loops, use the `end` keyword.

```matlab
a = zeros(2, 3);
for r = 1:2
     for c = 1:3
          a(r, c) = (10 * r) + c;
     end
end
a
```

*Output:*
```matlab
a =

    11    12    13
    21    22    23
```

**Learn about the `while` loop [here](https://se.mathworks.com/help/matlab/ref/while.html).**

*To programmatically exit a loop use the `break` statement, and to skip to the next iteration of a loop use the `continue` statement.*

To display variables and string together, add the *+* (plus) symbol, like so.

```matlab
disp (2 + " * " + 1 + " = " + 2)
```

*Output:*
```matlab
2 * 1 = 2
```

## Symbolic Functions

Symbolic functions represent math functions and can be for differentiation, integration, solving ODEs, and other math operations. To create symbolic functions use `syms` like so,

```matlab
syms f(x, y) % Creates symbolic function 'f' with variables 'x' and 'y'
f(x, y) = x ^ 2 * y % Assigns a mathematical expression to 'f'
f(3, 2) % Finds the value of 'f' at (3,2)
```

<img src="https://render.githubusercontent.com/render/math?math=f(x,%20y)%20=%20x%20^%202%20*%20y&mode=inline">

*Output:*
```matlab
f(x, y) =
 
x^2*y
 
 
ans =
 
18
```

### Differentiate Symbolic Expressions

Expressions with Individual variables can be expressed like so,

```matlab
syms x  % Creates symbolic function 'x'
f = sin(x) ^ 2 % Assigns a mathematical expression to 'f'
diff(f) % Differentiates the symbolic expression 'f'
```

<img src="https://render.githubusercontent.com/render/math?math=f%20=%20sin(x)%20^%202&mode=inline">
<br/>
<img src="https://render.githubusercontent.com/render/math?math=ans%20=%202%20*%20cos(x)%20*%20sin(x)&mode=inline">

```matlab
syms x y % Creates symbolic functions 'x' and 'y'
f = (x) ^ 2 * y % Assigns a mathematical expression to 'f'
fx = diff(f, x) % Assigns a mathematical expression to 'f'
fy = diff(f, y) % Differentiates the symbolic expression i.e., 'df/dy'
```

<img src="https://render.githubusercontent.com/render/math?math=f%20=%20x%20^%202%20*%20y&mode=inline">
<br/>
<img src="https://render.githubusercontent.com/render/math?math=fx%20=%202%20*%20x%20*%20y&mode=inline">
<br/>
<img src="https://render.githubusercontent.com/render/math?math=fy%20=%20x%20^%202&mode=inline">

### Integrate Symbolic Expressions

```matlab
syms x % Creates symbolic functions 'x'
f = sin(x) ^ 2 % Assigns a mathematical expression to 'f'
int(f) % Integrates the symbolic expression 'f' with respect to 'x'
```

<img src="https://render.githubusercontent.com/render/math?math=f%20=%20sin(x)%20^%202&mode=inline">
<br/>
<img src="https://render.githubusercontent.com/render/math?math=ans%20=%20x/2%20-%20sin(2*x)/4&mode=inline">

```matlab
syms x y n % Creates symbolic functions 'x', 'y' and 'n'
f = x^n + y^n % Assigns a mathematical expression to 'f'
int(f, 1, 10) % Calculates definite integral
```

<img src="https://render.githubusercontent.com/render/math?math=f%20=%20x^n%20+%20y^n&mode=inline">
<br/>
<img src="https://render.githubusercontent.com/render/math?math=ans%20%3D%20%5Cleft%5C%7B%5Cbegin%7Barray%7D%7Bcl%7D%20%5Clog%20(10)%2B%5Cfrac%7B9%7D%7By%7D%20%26%20%5Ctext%7B%5C%20if%5C%20%5C%20%7Dn%3D-1%5C%5C%20%5Cfrac%7B10%5C%2C%7B10%7D%5En-1%7D%7Bn%2B1%7D%2B9%5C%2Cy%5En%20%26%20%5Ctext%7B%5C%20if%5C%20%5C%20%7Dn%5Cneq%20-1%20%5Cend%7Barray%7D%5Cright.%0A">

### Solve Equations

You can solve different types of symbolic equations (like: equations with one or more symbolic variables, systems of algebraic equations, etc.). **For detailed information see [Equation Solving](https://se.mathworks.com/help/symbolic/equation-solving.html).**

```matlab
syms x % Creates symbolic functions 'x'
solve(x^3 - 6*x^2 == 6 - 11*x) % Solves equations and systems
```

<img src="https://render.githubusercontent.com/render/math?math=x^3%20-%206*x^2%20=%206%20-%2011*x&mode=inline">

Returns values of `x` to be `(1, 2, 3)`.

You also can solve systems of equations, like so,

```matlab
syms x y z % Creates symbolic functions 'x', 'y' and 'z'
[x, y, z] = solve(z == 4*x, x == y, z == x^2 + y^2) % Solves equations and systems
```

<img src="https://render.githubusercontent.com/render/math?math=z%20=%204*x&mode=inline">
<br/>
<img src="https://render.githubusercontent.com/render/math?math=x%20=%20y&mode=inline">
<br/>
<img src="https://render.githubusercontent.com/render/math?math=z%20=%20x^2%20%2B%20y^2&mode=inline">

The returns possible values of `(x, y, z)` to be `(0, 0, 0)` and `(2, 2, 8)`.

### Simplify Symbolic Expressions

```matlab
syms x % Creates symbolic functions 'x'
f = (x ^2- 1)*(x^4 + x^3 + x^2 + x + 1)*(x^4 - x^3 + x^2 - x + 1); % Assigns a mathematical expression to 'f'
```

<img src="https://render.githubusercontent.com/render/math?math=f%20%3D%20%7B%5Cleft(x%5E2%20-1%5Cright)%7D%5C%2C%7B%5Cleft(x%5E4%20-x%5E3%20%2Bx%5E2%20-x%2B1%5Cright)%7D%5C%2C%7B%5Cleft(x%5E4%20%2Bx%5E3%20%2Bx%5E2%20%2Bx%2B1%5Cright)%7D">

You can simplify this answer by entering,

```matlab
simplify(f) % Simplifies representation of uncertain objects
```

<img src="https://render.githubusercontent.com/render/math?math=f%20=%20x^{10}%20-%201&mode=inline">

### Substitutions in Symbolic Expressions

```matlab
syms x y % Creates symbolic functions 'x' and 'y'
f = x^2*y + 5*x*sqrt(y) % Assigns a mathematical expression to 'f'
```

<img src="https://render.githubusercontent.com/render/math?math=f%20=%20x^2%20\,y%2B5\,x\,\sqrt{y}&mode=inline">

To substitute `x` with `3` enter command,

```matlab
subs(f, x, 3) % Substitutes symbolic 'x' in function 'f'
```

<img src="https://render.githubusercontent.com/render/math?math=ans%20=%209\,y%2B15\,\sqrt{y}&mode=inline">

**Learn more about Symbolic Computations [here](https://se.mathworks.com/help/symbolic/performing-symbolic-computations.html).**

## Functional Programming

*Scripts* and *functions* allow to reuse sequences of commands by storing them in program files. Functions provide more flexibility, primarily because they can pass input values and return output values. For example, the function named `fact` computes the factorial of a number (`n`) and returns the result (`f`).

```matlab
x = 5;
y = fact(5)

function f = fact(n)
     f = prod(1 : n);
end
```

*Output:*
```matlab
y =

   120
```

If your function accepts any inputs, enclose their names in parentheses after the function name. And, separate inputs with commas. Like so,
`function y = myFunction(one, two, three)`

If your function returns more than one output, enclose the output names in square brackets. Like so,
`function [one, two, three] = myFunction(x)`

***Valid function*** and ***variable names*** **must start with a letter, and can contain letters, digits, or underscores**.

:exclamation: Function definitions in a script must appear at the end of the file.
In case you see the above error, simply *move the function definition to the very end of the script*.

## Reading-Writing Files

To load data from file, use the `importdata` function.

```matlab
A = importdata('ngc6543a.jpg');
image(A)
```

The output `A` is 3D matrix of `uint8` class and holds the RGB values of the image `ngc6543a.jpg`.

![JPG file ngc6543a](/images/imported_image.png)

### Audio Data Files

The `audioinfo` gets the information about the audio file.

```matlab
filename = 'data_files/handel.wav';
info = audioinfo(filename)
```

The `audioread` function supports WAVE, OGG, FLAC, AU, MP3, and MPEG-4 AAC files.

```matlab
[y, Fs] = audioread(filename);
```

Play the audio, using:

```matlab
sound(y, Fs)
```

To create a vector `t` the same length as `y` (which represents elapsed time).

```matlab
t = 0 : seconds(1/Fs) : seconds(info.Duration);
t = t(1 : end-1);
```

And plot the audio data as a function of time, like so.

```matlab
plot(t, y)
xlabel('Time')
ylabel('Audio Signal')
```

![Audio Data Plot](/images/imported_audio.png)

### Textual Data Files

To import files, with specific space delimiter and the single column header, do this.

```matlab
filename = 'data_files/myfile01.txt';
delimiterIn = ' ';
headerlinesIn = 1;
A = importdata(filename, delimiterIn, headerlinesIn);
```

Here's what the `myfile01.txt` actually looks like.

*Output:*
```matlab
Day1  Day2  Day3  Day4  Day5  Day6  Day7
95.01 76.21 61.54 40.57  5.79 20.28  1.53
23.11 45.65 79.19 93.55 35.29 19.87 74.68
60.68  1.85 92.18 91.69 81.32 60.38 44.51
48.60 82.14 73.82 41.03  0.99 27.22 93.18
89.13 44.47 17.63 89.36 13.89 19.88 46.60
```

View columns 3 and 5, using:

```matlab
for k = [3, 5]
     disp(A.colheaders{1, k})
     disp(A.data( :, k ))
     disp(' ')
end
```

*Output:*
```matlab
Day3
   61.5400
   79.1900
   92.1800
   73.8200
   17.6300

Day5
    5.7900
   35.2900
   81.3200
    0.9900
   13.8900
```

To export *object data* to an Excel file, use `export(ps, filename, sheet)`. Here, `ps` is the parameter set to export, `filename` is the name of the file, and `sheet` is the name of Excel workbook sheet.

**More details on `importdata` can be found [here](https://se.mathworks.com/help/matlab/ref/importdata.html?searchHighlight=colheaders&s_tid=srchtitle).**

### CSV Data Files

Comma-separated value (CSV) files can be read through `csvread`. However, MATLAB recommends `readmatrix` instead.

`readmatrix(filename)` creates an array by reading column-oriented data from a file. Compatible file formats include delimited text file types (`.txt`, `.dat`, or `.csv`) and spreadsheet file types (`.xls`, `.xlsb`, `.xlsm`, `.xlsx`, `.xltm`, `.xltx`, or `.ods`)

Try `M = readmatrix('basic_matrix.txt')` or  `M = readmatrix('basic_matrix.xls')`.

*Output:*
```matlab
M =

     6     8     3     1
     5     4     7     3
     1     6     7    10
     4     2     8     2
     2     7     5     9
```

### Import Mixed Data from Text File

The sample file `bigfile.txt` contains commented lines beginning with *##*. The data is arranged in five columns: The first column contains text indicating timestamps. The second, third, and fourth columns contain numeric data indicating temperature, humidity and wind speed. The last column contains descriptive text.

```matlab
type('bigfile.txt')
```

*Output:*
```matlab
## A	ID = 02476
## YKZ Timestamp Temp Humidity Wind Weather
06-Sep-2013 01:00:00	6.6	89	4	clear
06-Sep-2013 05:00:00	5.9	95	1	clear
06-Sep-2013 09:00:00	15.6	51	5	mainly clear
06-Sep-2013 13:00:00	19.6	37	10	mainly clear
06-Sep-2013 17:00:00	22.4	41	9	mostly cloudy
06-Sep-2013 21:00:00	17.3	67	7	mainly clear
## B	ID = 02477
## YVR Timestamp Temp Humidity Wind Weather
09-Sep-2013 01:00:00	15.2	91	8	clear
09-Sep-2013 05:00:00	19.1	94	7	n/a
09-Sep-2013 09:00:00	18.5	94	4	fog
09-Sep-2013 13:00:00	20.1	81	15	mainly clear
09-Sep-2013 17:00:00	20.1	77	17	n/a
09-Sep-2013 18:00:00	20.0	75	17	n/a
09-Sep-2013 21:00:00	16.8	90	25	mainly clear
## C	ID = 02478
## YYZ Timestamp Temp Humidity Wind Weather
```

### Import Data as Table

To import the data as a table, use `readtable` with import options. The `DataLines` property selects a specify location of the data (*in this case 3 through 8*).

```matlab
opts = detectImportOptions('bigfile.txt');
opts.DataLines = [3 8];
opts.VariableNames = {'Timestamp', 'Temp', ...
                    'Humidity', 'Wind', 'Weather'};
T_first = readtable('bigfile.txt', opts)
```

*Output:*
```matlab
T_first =

  6×5 table

         Timestamp          Temp    Humidity    Wind         Weather     
    ____________________    ____    ________    ____    _________________

    06-Sep-2013 01:00:00     6.6       89         4     {'clear'        }
    06-Sep-2013 05:00:00     5.9       95         1     {'clear'        }
    06-Sep-2013 09:00:00    15.6       51         5     {'mainly clear' }
    06-Sep-2013 13:00:00    19.6       37        10     {'mainly clear' }
    06-Sep-2013 17:00:00    22.4       41         9     {'mostly cloudy'}
    06-Sep-2013 21:00:00    17.3       67         7     {'mainly clear' }
```

### Import Data as Cell Array

```matlab
opts = detectImportOptions('bigfile.txt');
opts.DataLines = [3 8];
C = readcell('bigfile.txt', opts)
```

*Output:*
```matlab
C =

  6×5 cell array

    {[06-Sep-2013 01:00:00]}    {[ 6.6000]}    {[89]}    {[ 4]}    {'clear'        }
    {[06-Sep-2013 05:00:00]}    {[ 5.9000]}    {[95]}    {[ 1]}    {'clear'        }
    {[06-Sep-2013 09:00:00]}    {[15.6000]}    {[51]}    {[ 5]}    {'mainly clear' }
    {[06-Sep-2013 13:00:00]}    {[19.6000]}    {[37]}    {[10]}    {'mainly clear' }
    {[06-Sep-2013 17:00:00]}    {[22.4000]}    {[41]}    {[ 9]}    {'mostly cloudy'}
    {[06-Sep-2013 21:00:00]}    {[17.3000]}    {[67]}    {[ 7]}    {'mainly clear' }
```

Imports can also be done using the `textscan` function. Just specify the size of block using `N` and the format of the data fields using `formatSpec` (the *format specifier* function).

```matlab
N = 6;
formatSpec = '%D %f %f %f %s';
fileID = fopen('bigfile.txt');
```

`%D` indicates the date and time variables, `%f` indicates double-precision floating point values , and `%s` indicates strings.

To read the first block and display the contents of the variable `Humidity` (*column 2*), try:

```matlab
C_first = textscan(fileID, formatSpec, N, 'CommentStyle', '##', 'Delimiter', '\t')
C_first{2}
```

*Output:*
```matlab
C_first =

  1×5 cell array

    {6×1 datetime}    {6×1 double}    {6×1 double}    {6×1 double}    {6×1 cell}


ans =

   15.2000
   19.1000
   18.5000
   20.1000
   20.1000
   20.0000
```

---

## Useful Examples

### Importing TXT Data and Extracting Tabular Data

```matlab
%% Clearing previous session
clc % Clears Command Window
clear % Remove all variables from workspace
close all % Closes all figures

%% Initializing import file name
filename = '06102017.txt'; % File path

%% Importing lines 11-13 from text file
para = detectImportOptions(filename); % Creates import options based on file content
para.DataLines = [11 13]; % Selects lines 11-13
p_data = readcell(filename, para); % Reads cell array from file
disp('MIDAS SVP 500 Parameters:'); % Displays value in Command Window
fprintf(1, '%s\n', p_data{:}); % Displays call data to Command Window 

%% Importing lines 32-130 from text file
ipts = detectImportOptions(filename); % Creates import options based on file content
ipts.DataLines = [32 130]; % Selects lines 32-130
ipts.VariableNames = {'Date_Time', 'Sound_Velocity', ...
    'Pressure', 'Temperature'}; % Creates column names
T_first = readtable(filename, ipts); % Creates table from file
data_count = height(T_first); % Counts number of table rows

%% Plotting data
figure % Creates new figure
plot(1:data_count, T_first.Pressure)
hold on % Retain current plot when adding new plots
plot(1:data_count, T_first.Temperature)
legend('Pressure','Temperature') % Adds legend to figure
legend('Location','southeast') % Moves lend to specific location with respect to axes
title('Variation of Water Temperature with Depth') % Adds title to figure
set(gca, 'Ydir', 'reverse') % Reverse the orientation of Y-Axis
hold off % Stops retaining current plot
```

*The above code plots a different output. Can you fix the code to get the output below?*

![Pressure vs. Temperature](/images/pressure_v_temp.png)

<details>
<summary>Here's the correct code...</summary>
<p>

```matlab
%% Clearing previous session
clc % Clears Command Window
clear % Remove all variables from workspace
close all % Closes all figures

%% Initializing import file name
filename = 'data_files/06102017.txt'; % File path

%% Importing lines 11-13 from text file
para = detectImportOptions(filename); % Creates import options based on file content
para.DataLines = [11 13]; % Selects lines 11-13
p_data = readcell(filename, para); % Reads cell array from file

disp('MIDAS SVP 500 Parameters:'); % Displays value in Command Window
fprintf(1, '%s\n', p_data{:}); % Displays call data to Command Window 

%% Importing lines 32-130 from text file
ipts = detectImportOptions(filename); % Creates import options based on file content
ipts.DataLines = [32 130]; % Selects lines 32-130
ipts.VariableNames = {'Date_Time', 'Sound_Velocity', ...
    'Pressure', 'Temperature'}; % Creates column names
T_first = readtable(filename, ipts); % Creates table from file
data_count = height(T_first); % Counts number of table rows

%% Plotting data
figure % Creates new figure
line(1:data_count, T_first.Pressure, 'Color', 'b') % Creates primitive line plot
ylabel('Pressure'); % Sets Y-Axis label text
hold on % Retain current plot when adding new plots

ax1 = gca; % Selects current axes
ax1.YColor = 'b'; % Sets Y-Axis color
ax1_pos = ax1.Position; % Selects position of first axes
ax2 = axes('Position', ax1_pos, ... % Sets position properties
    'XAxisLocation', 'top', ...
    'YAxisLocation', 'right', ...
    'Color','none');
set(ax1, 'xticklabel', []) % Removes X-Tick labels for first plot
set(ax2, 'xticklabel', []) % Removes X-Tick labels for second plot

line(1:data_count, T_first.Temperature, 'Color', 'r') % Creates primitive line plot
ylabel('Temperature'); % Sets Y-Axis label text
ax2.YColor = 'r'; % Sets Y-Axis color
set(get(ax2,'ylabel'),'rotation',-90,'VerticalAlignment','bottom') % Set graphics object properties
title('Variation of Water Temperature with Depth') % Adds title to figure
set(ax1, 'Ydir', 'reverse') % Reverse the orientation of Y-Axis
hold off % Stops retaining current plot
```

</p>
</details>

### Importing XYZ Data and Visualizing it Using Different Plot Types

The following example visualizes the topography of seabed data.

```matlab
%% Clearing previous session
clc % Clears Command Window
clear % Remove all variables from workspace
close all % Closes all figures

%% Importing XYZ data
xyzData = importdata('data_files\hm_ac.xyz'); % Loads data from file
X = xyzData(:, 1); % X-Axis data
Y = xyzData(:, 2); % Y-Axis data
Z = xyzData(:, 3); % Z-Axis data

%% Plot Type 1 - Scatter Plot
figure % Creates new figure window
scatter3(X, Y, Z, 'MarkerFaceColor', [0 .75 .75]) % 3D Scatter Plot
view([90 45]) % Changes Plot View

%% converting XYZ data into surface
tri = delaunay(X, Y); % 2-D Delaunay triangulation from points in vectors X and Y

%% Plot Type 2 - Surface Plot
figure % Creates new figure window
trisurf(tri, X, Y, Z); % Plots 3-D triangular surface
shading interp % Color shades surface using interpolating
view([90 45]) % Changes Plot View

%% Another method for converting XYZ data into surface
% Creates 2-D or 3-D Delaunay Triangulation from set of points
dt = delaunayTriangulation(X, Y);
tri = dt.ConnectivityList;
xi = dt.Points(:, 1);
yi = dt.Points(:, 2);

% Perform interpolation on 2-D or 3-D data set of scattered data
F = scatteredInterpolant(X, Y, Z);
zi = F(xi, yi);

%% Plot Type 3 - 2D view of Scatter Plot
figure
% Plots 3-D triangular surface using vectors X, Y, and Z, and triangle connectivity matrix T
trisurf(tri, xi, yi, zi)
shading interp % Sets color shading properties
view([90 90]) % Changes Plot View
```

![XYZ Plot 1](/images/xyz_1_plot_1.png)
![XYZ Plot 2](/images/xyz_1_plot_2.png)
![XYZ Plot 3](/images/xyz_1_plot_3.png)

And, the following example visualizes a submarine lying on the seabed data (*using other plot types*).

```matlab
%% Clearing previous session
clc % Clears Command Window
clear % Remove all variables from workspace
close all % Closes all figures

%% Importing XYZ data
xyzData = importdata('data_files\talllaht_6.xyz');
X = xyzData(:, 1); % X-Axis data
Y = xyzData(:, 2); % Y-Axis data
Z = xyzData(:, 3); % Z-Axis data

%% Another method for converting XYZ data into surface
% Creates 2-D or 3-D Delaunay Triangulation from set of points
dt = delaunayTriangulation(X, Y);
tri = dt.ConnectivityList;
xi = dt.Points(:, 1);
yi = dt.Points(:, 2);

% Perform interpolation on 2-D or 3-D data set of scattered data
F = scatteredInterpolant(X, Y, Z);
zi = F(xi, yi);

%% Plot Type 1 - 2D view of Scatter Plot
figure
% Plots 3-D triangular surface using vectors X, Y, and Z, and triangle connectivity matrix T
trisurf(tri, xi, yi, zi)
shading interp % Sets color shading properties
view([270 90]) % Changes Plot View

%% Reducing data resolution (i.e., cell size)
min_long = min(X); % Finds min values
min_lat = min(Y); % Finds min values
max_long = max(X); % Finds max values
max_lat = max(Y); % Finds max values
proj_long = linspace(min_long, max_long, 1000); % Generates linearly spaced vectors
proj_lat = linspace(min_lat, max_lat, 1000); % Generates linearly spaced vectors
%Interpolates between assigned values to refine the grid
[PROJ_LONG, PROJ_LAT] = ndgrid(proj_long, proj_lat); % Creates rectangular grid in N-D space
PROJ_Z = F(PROJ_LONG, PROJ_LAT);

%% Plot Type 2 - Filled Contour Plot
figure
% Plots Filled 2-D Contour Plots
contourf(PROJ_LONG, PROJ_LAT, PROJ_Z); % Fills data into 2-D contour plot
camroll(90) % Rotates camera about view axis

%% Plot Type 3 - Simple Contour Plot with data
contour(PROJ_LONG, PROJ_LAT, PROJ_Z, 'ShowText', 'on') % Creates contour plot of matrix
camroll(90) % Rotates camera about view axis
grid on % Displays axes grid lines
colorbar % Shows color scale using a colorbar
```

![XYZ Plot 1](/images/xyz_2_plot_1.png)
![XYZ Plot 2](/images/xyz_2_plot_2.png)
![XYZ Plot 3](/images/xyz_2_plot_3.png)

### Plotting Longitudes - Latitudes on Maps

The following example visualizes locations in Tallinn, Estonia.

```matlab
%% Clearing previous session
clc % Clears Command Window
clear % Remove all variables from workspace
close all % Closes all figures

%% Importing CSV file
csv_file = 'data_files\baltic_locations.csv'; % CSV file path
csv_data = readtable(csv_file); % Creates table from CSV file

%% Selecting specific columns from MATLAB table
% Extracting three columns from 'csv_data' into 'slctd_clmns'
slctd_clmns.NAME = csv_data.A1_NAME;
slctd_clmns.LONGITUDE = csv_data.X_COORDINATE;
slctd_clmns.LATITUDE = csv_data.Y_COORDINATE;

slctd_clmns = struct2table(slctd_clmns) % Converts structure array to table

%% Extracting rows with NAME == 'Harju maakond'
po_in_harju = slctd_clmns(strcmpi(slctd_clmns.NAME, 'Harju maakond'), :);

%% Bounding Box retrieved from https://boundingbox.klokantech.com/
lat_harju_N = 59.591577
lon_harju_E = 24.550170

lat_harju_S = 59.351808
lon_harju_W = 24.926283

geoplot(po_in_harju.LATITUDE, po_in_harju.LONGITUDE, 'r*') % Plots geographic coordinates
geolimits([lat_harju_S lat_harju_N],[lon_harju_E lon_harju_W]) % Sets geographic limits
geobasemap streets % Sets basemap style
```

![Geographic Plot](/images/geo_plot.png)

Other geographic basemaps avaiable in MATLAB can be found [here](https://se.mathworks.com/help/matlab/ref/geobasemap.html).

---

**Now, try these out yourself:**
- Initialize temperature in Fahrenheit and convert it to Celsius.
- Convert value in radians to degree.
- Calculate the value *tan of pi*, but prevent the output from being displayed.
- Generate the first 20 Fibonacci numbers using loop and then display the vector as bar plot.
- Print the table of a random number (*between 5 and 15*), using loops. Like `13 * 1 = 13` [...] `13 * 10 = 130`.

**Encode these [word problems](https://themathpage.com/Alg/word-problems.htm):**
- Jane spent $42 for shoes.  This was $14 less than twice what she spent for a blouse.  How much was the blouse?
- There are b boys in the class.  This is three more than four times the number of girls.  How many girls are in the class?
- The sum of two numbers is 84, and one of them is 12 more than the other.  What are the two numbers?
- The sum of two consecutive numbers is 37.  What are they?
- One number is 10 more than another.  The sum of twice the smaller plus three times the larger, is 55.  What are the two numbers?
- Divide $80 among three people so that the second will have twice as much as the first, and the third will have $5 less than the second.
- The sum of two consecutive odd numbers is 52.  What are the two odd numbers?
- Julie has $50, which is eight dollars more than twice what John has.  How much has John?
- Carlotta spent $35 at the market.  This was seven dollars less than three times what she spent at the bookstore; how much did she spend there?
- There are b black marbles.  This is four more than twice the number of red marbles.  How many red marbles are there?
- Janet spent $100 on books.  This was k dollars less than five times what she spent on lunch.  How much did she spend on lunch?
- The sum of two numbers is 99, and one of them is 17 more than the other.  What are the two numbers?
- A class of 50 students is divided into two groups; one group has eight less than the other; how many are in each group?
- The sum of two numbers is 72, and one of them is five times the other; what are the two numbers?
- The sum of three consecutive numbers is 87; what are they?
- A group of 266 persons consists of men, women, and children.  There are four times as many men as children, and twice as many women as children.  How many of each are there?
- Divide $79 among three people so that the second will have three times more than the first, and the third will have two dollars more than the second.
- Divide $15.20 among three people so that the second will have one dollar more than the first, and the third will have $2.70 more than the second.
- Two consecutive odd numbers are such that three times the first is 5 more than twice the second.  What are those two odd numbers?

**Try to encode the following equations:**

- Initial Velocity

     <img src="https://render.githubusercontent.com/render/math?math=\text{u}_\text{x}%20=%20\text{u}%20\cdot%20\cos\theta&mode=inline">
     <br/>
     <img src="https://render.githubusercontent.com/render/math?math=\text{u}_\text{y}%20=%20\text{u}%20\cdot%20\sin\theta&mode=inline">

- Time of Flight

     <img src="https://render.githubusercontent.com/render/math?math=\text{T}=\frac{2%20\cdot%20\text{u}_\text{y}}{\text{g}}&mode=inline">

- Velocity

     <img src="https://render.githubusercontent.com/render/math?math=\text{u}_\text{x}%20=%20\text{u}%20\cdot%20\cos{\theta}&mode=inline">
     <br/>
     <img src="https://render.githubusercontent.com/render/math?math=\text{u}_\text{y}%20=%20\text{u}%20\cdot%20\sin%20{\theta}%20-%20\text{g}%20\cdot%20\text{t}&mode=inline">

- Pythagorean Theorem

     <img src="https://render.githubusercontent.com/render/math?math=\text{u}=\sqrt{\text{u}_\text{x}^2+\text{u}_\text{y}^2}&mode=inline">

- Displacement

     <img src="https://render.githubusercontent.com/render/math?math=\text{x}=\text{u}%20\cdot%20\text{t}%20\cdot%20\cos\theta&mode=inline">
     <br/>
     <img src="https://render.githubusercontent.com/render/math?math=\text{y}=\text{u}%20\cdot%20\text{t}%20\cdot%20\sin\theta-\frac1%202\text{gt}^2&mode=inline">
     <br/>
     <img src="https://render.githubusercontent.com/render/math?math=\Delta%20\text{r}=\sqrt{\text{x}^2%2B\text{y}^2}&mode=inline">

- Parabolic Trajectory

     <img src="https://render.githubusercontent.com/render/math?math=\text{y}=\tan\theta%20\cdot%20\text{x}-\frac{\text{g}}{2%20\cdot%20\text{u}^2%20\cdot%20\cos^2\theta}%20\cdot%20\text{x}^2&mode=inline">

- Maximum Height

     <img src="https://render.githubusercontent.com/render/math?math=\text{h}=\frac{\text{u}^2%20\cdot%20\sin^2\theta}{2\cdot%20\text{g}}&mode=inline">
     <br/>
     <img src="https://render.githubusercontent.com/render/math?math=\text{t}_\text{h}=\frac{\text{u}%20\cdot%20\sin\theta}{\text{g}}&mode=inline">

     *where <img src="https://render.githubusercontent.com/render/math?math=\text{t}_\text{h}&mode=inline"> stands for the time it takes to reach maximum height.*

- Range

     <img src="https://render.githubusercontent.com/render/math?math=\text{R}=\frac{\text{u}^2%20\cdot%20\sin2\theta}{\text{g}}&mode=inline">

     <br/><br/>

- Sound velocity in water - [Del Grosso and Mader (1972)](https://www.sciencedirect.com/science/article/abs/pii/S030156299800091X)

     ![equation](https://latex.codecogs.com/gif.latex?c%20%3D%20a_%7B0%7D%20&plus;%20a_%7B1%7D%20%5Ccdot%20T%20&plus;%20a_%7B2%7D%20%5Ccdot%20T%5E%7B2%7D%20&plus;%20a_%7B3%7D%20%5Ccdot%20T%5E%7B3%7D%20&plus;%20a_%7B4%7D%20%5Ccdot%20T%5E%7B4%7D%20&plus;%20a_%7B5%7D%20%5Ccdot%20T%5E%7B5%7D)

     *c = sound velocity [m s<sup>-1</sup>]*

     *T = Temperature*

     *a<sub>0</sub> ... a<sub>5</sub> = Coefficients*

     *List of coefficients (a<sub>0</sub> ... a<sub>5</sub>) from literature*

     | Reference | a<sub>0</sub> | a<sub>1</sub> | 10<sup>2</sup> . a<sub>2</sub> | 10<sup>4</sup> . a<sub>3</sub> | 10<sup>6</sup> . a<sub>4</sub> | 10<sup>9</sup> . a<sub>5</sub> | Max error (m s<sup>-1</sup>) | Temp. range (C) |
     |---|---|---|---|---|---|---|---|---|
     | Del Grosso and Mader (1972) | 1402.388 | 5.03711 | 25.80852 | 3.3420 | 21.4780 | 3.146 | 0.002 | 0–100 |
     | Wilson (1959) | 1403.013 | 5.02476 | 25.69215 | 2.8874 | 20.8249 | 0. | 0.01 | 0–100 |
     | Greenspan and Tschiegg (1959) | 1402.736 | 5.03358 | 25.79506 | 3.3164 | 21.4526 | 3.045 | 0.01 | 0–100 |
     | AIUM (1995) | 1403.0 | 5.0 | 26.0 | 3.0 | 0. | 0. | 2.7 | 0–50 |

     **Simplified Equation:**

     ![equation](https://latex.codecogs.com/gif.latex?c%20%3D%201404.3&plus;4.7T-0.04T%5E2)

- [Mackenzie Equation (1981)](http://resource.npl.co.uk/acoustics/techguides/soundseawater/refs.html#7)

     ![equation](https://latex.codecogs.com/gif.latex?c%28D%2CS%2CT%29%20%3D%20%5Ctextsuperscript%7B%7E%7D%201448.96%20&plus;%204.591T%20-%205.304%20*%2010%5Ctextsuperscript%7B-2%7DT%5Ctextsuperscript%7B2%7D%20&plus;%202.374%20*%2010%5Ctextsuperscript%7B-4%7DT%5Ctextsuperscript%7B3%7D%20&plus;%201.340%20%28S-35%29%20&plus;%201.630%20*%2010%5Ctextsuperscript%7B-2%7DD%20&plus;%201.675%20*%2010%5Ctextsuperscript%7B-7%7DD%5Ctextsuperscript%7B2%7D%20-%201.025%20*%2010%5Ctextsuperscript%7B-2%7DT%28S%20-%2035%29%20-%207.139%20*%2010%5Ctextsuperscript%7B-13%7DTD%5Ctextsuperscript%7B3%7D)

     *T = temperature in degrees Celsius*

     *S = salinity in parts per thousand*

     *D = depth in metres*

     *Range of validity: temperature 2 to 30 °C, salinity 25 to 40 parts per thousand, depth 0 to 8000 m*

- [Coppens Equation (1981)](http://resource.npl.co.uk/acoustics/techguides/soundseawater/refs.html#2)

     ![equation](https://latex.codecogs.com/gif.latex?c%28D%2CS%2Ct%29%20%3D%20%5Ctextsuperscript%7B%7E%7D%20c%280%2CS%2Ct%29%20&plus;%20%2816.23%20&plus;%200.253t%29D%20&plus;%20%280.213-0.1t%29D%5Ctextsuperscript%7B2%7D%20&plus;%20%7B%5B%7D0.016%20&plus;%200.0002%28S-35%29%7B%5D%7D%28S%20-%2035%29tD)

     ![equation](https://latex.codecogs.com/gif.latex?c%280%2CS%2Ct%29%20%3D%20%5Ctextsuperscript%7B%7E%7D%201449.05%20&plus;%2045.7t%20-%205.21t%5Ctextsuperscript%7B2%7D%20&plus;%200.23t%5Ctextsuperscript%7B3%7D%20&plus;%20%281.333%20-%200.126t%20&plus;%200.009t%5Ctextsuperscript%7B2%7D%29%28S%20-%2035%29)

     *t = T/10 where T = temperature in degrees Celsius*

     *S = salinity in parts per thousand*

     *D = depth in kilometres*

     *Range of validity: temperature 0 to 35 °C, salinity 0 to 45 parts per thousand, depth 0 to 4000 m*

- Conversion of pressure into depth - [Leroy and Parthiot (1998)](http://resource.npl.co.uk/acoustics/techguides/soundseawater/refs.html#6)

     ![equation](https://latex.codecogs.com/gif.latex?Z%5Ctextsubscript%7BS%7D%28P%2CQ%29%20%3D%20%5Ctextsuperscript%7B%7E%7D%209.72659%20*%2010%5Ctextsuperscript%7B2%7DP%20-%202.2512%20*%2010%5Ctextsuperscript%7B-1%7D%20P%5Ctextsuperscript%7B2%7D%20&plus;%202.279%20*%2010%5Ctextsuperscript%7B-4%7D%20P%5Ctextsuperscript%7B3%7D%20-%201.82%20*%2010%5Ctextsuperscript%7B-7%7D%20P%5Ctextsuperscript%7B4%7D%20g%28Q%29%20&plus;%201.092%20*%2010%5Ctextsuperscript%7B-4%7D%20P)

     *Where g(Q), the international formula for gravity, is given by:*

     ![equation](https://latex.codecogs.com/gif.latex?g%28Q%29%20%3D%20%5Ctextsuperscript%7B%7E%7D%209.780318%20%281%20&plus;%205.2788%20*%2010%5Ctextsuperscript%7B-3%7D%20sin%5Ctextsuperscript%7B2%7DQ%20&plus;%202.36%20*%2010%5Ctextsuperscript%7B-5%7D%20sin%5Ctextsuperscript%7B4%7D%20Q%29)

     *Z = depth in metres*

     *P = pressure in MPa (relative to atmospheric pressure)*

     *Q = latitude*

- Conversion of depth into pressure - [Leroy and Parthiot (1998)](http://resource.npl.co.uk/acoustics/techguides/soundseawater/refs.html#6)

     ![equation](https://latex.codecogs.com/gif.latex?P%28Z%2CQ%29%20%3D%20h%28Z%2CQ%29%20-%20Th%5Ctextsubscript%7B0%7DZ)

     ![equation](https://latex.codecogs.com/gif.latex?h%28Z%2CQ%29%20%3D%20h%28Z%2C45%29%20*%20k%28Z%2CQ%29)

     ![equation](https://latex.codecogs.com/gif.latex?h%28Z%2C45%29%20%3D%20%5Ctextsuperscript%7B%7E%7D%201.00818%20*%2010%5Ctextsuperscript%7B-2%7D%20Z%20&plus;%202.465%20*%2010%5Ctextsuperscript%7B-8%7DZ%5Ctextsuperscript%7B2%7D%20-%201.25%20*%2010%5Ctextsuperscript%7B-13%7DZ%5Ctextsuperscript%7B3%7D%20&plus;%202.8%20*%2010%5Ctextsuperscript%7B-19%7DZ%5Ctextsuperscript%7B4%7D)

     ![equation](https://latex.codecogs.com/gif.latex?k%28Z%2CQ%29%20%3D%20%5Ctextsuperscript%7B%7E%7D%20%28g%28Q%29%20-%202%20*%2010%5Ctextsuperscript%7B-5%7DZ%29%5Ctextbf%7B/%7D%289.80612%20-%202%20*%2010%5Ctextsuperscript%7B-5%7DZ%29)

     ![equation](https://latex.codecogs.com/gif.latex?g%28Q%29%20%3D%20%5Ctextsuperscript%7B%7E%7D%209.7803%281%20&plus;%205.3%20*%2010%5Ctextsuperscript%7B-3%7D%20sin%5Ctextsuperscript%7B2%7DQ%29)

     ![equation](https://latex.codecogs.com/gif.latex?Th%5Ctextsubscript%7B0%7DZ%20%3D%201.0%20*%2010%5Ctextsuperscript%7B-2%7D%20Z/%28Z&plus;100%29%20&plus;%206.2%20*%2010%5Ctextsuperscript%7B-6%7D%20Z)

     *Z = depth in metres*

     *h = pressure in MPa (relative to atmospheric pressure)*

     *Q = latitude*

     *In the above equation, P (=h(Z,Q)) would apply to the oceanographers' standard ocean, defined as an ideal medium with a temperature of 0 °C and salinity of 35 parts per thousand.*

Also, try out these **MATLAB Examples**:

- [GPS receiver simulation model](https://se.mathworks.com/help/nav/ref/gpssensor-system-object.html). Run this `openExample('shared_positioning/GenerateGPSPositionMeasurementsFromStationaryInputExample')` in the **Command Window**.

- [Underwater Target Detection with an Active Sonar System](https://se.mathworks.com/help/phased/ug/underwater-target-detection-with-an-active-sonar-system.html). Run this `openExample('phased/ActiveSonarExample')` in the **Command Window**.

## Sources
1. "Introduction to MATLAB Programming" Courseware [https://se.mathworks.com/academia/highschool/courseware/introduction-to-matlab.html]
2. Get Started with MATLAB [https://se.mathworks.com/help/matlab/getting-started-with-matlab.html]
