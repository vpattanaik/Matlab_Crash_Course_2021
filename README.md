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

### Adding Comments to Script
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
plot(x,y)

%% Modify Plot Properties
title('Sine Wave')
xlabel('x')
ylabel('sin(x)')
fig = gcf;
fig.MenuBar = 'none';
```

The code has two sections, like so.

![Code Sections](/images/code_sections.png)

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
b = (sin(a))^2;
```

To see the value of *b* in **Command Window**, type *b*.

*Output:*
```matlab
b =

    0.7081
```

To recall previous commands pressing the ↑ (up-arrow) and ↓(down-arrow) keys.

## Data Types

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
a+10
```

*Output:*
```matlab
ans =

    11    12    13
    14    15    16
    17    18    20
```

```matlab
a*2
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
a.^2
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
     a*a
     ```

     *Output:*
     ```matlab
     ans =

     30    36    45
     66    81   102
     109   134   169
     ```

-    ```matlab
     a.*a
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

## Array Indexing

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
plot(x,y2, ':m')
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

## Functions

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

## Reading-Writing Files

To load data from file, use the `importdata` function.

```matlab
A = importdata('ngc6543a.jpg');
image(A)
```

The output `A` is 3D matrix of `uint8` class and holds the RGB values of the image `ngc6543a.jpg`.

![JPG file ngc6543a](/images/imported_image.png)

### Textual Data Files

To import files, with specific space delimiter and the single column header, do this.

```matlab
filename = 'data_files/myfile01.txt';
delimiterIn = ' ';
headerlinesIn = 1;
A = importdata(filename, delimiterIn, headerlinesIn);
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

To export *object data* to an Excel file, use `export(ps, filename, sheet)`. Here, `ps` is the parameter set to export, `filename` is the name of the file, and `sheet` is the name of Excel workbook sheet.

**More details on `importdata` can be found [here](https://se.mathworks.com/help/matlab/ref/importdata.html?searchHighlight=colheaders&s_tid=srchtitle).**

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

### Importing XYZ Data and Using Different Plot Types

```matlab
%% Importing XYZ data and Displaying as Scatter Plot
xyzData = importdata('data_files\hm_ac.xyz');
X = xyzData(:, 1); % X-Axis data
Y = xyzData(:, 2); % Y-Axis data
Z = xyzData(:, 3); % Z-Axis data
figure % Creates new figure window
scatter3(X, Y, Z, 'MarkerFaceColor', [0 .75 .75]) % 3D Scatter Plot
view([90 45]) % Changes Plot View

%% Plot Type 2
tri = delaunay(X, Y); % 2-D Delaunay triangulation from points in vectors X and Y
figure % Creates new figure window
trisurf(tri, X, Y, Z); % Plots 3-D triangular surface
shading interp % Color shades surface using interpolating
view([90 45]) % Changes Plot View

%% Plot Type 3
min_long = min(X); % Finding min/max values
min_lat = min(Y);
max_long = max(X);
max_lat = max(Y);
proj_long = linspace(min_long, max_long, 100); % Generates linearly spaced vectors
proj_lat = linspace(min_lat, max_lat, 100);
%Interpolates between assigned values to refine the grid
[PROJ_LONG, PROJ_LAT] = ndgrid(proj_long, proj_lat);

% Perform interpolation on 2-D or 3-D data set of scattered data
F = scatteredInterpolant(X, Y, Z);
PROJ_Z = F(PROJ_LONG, PROJ_LAT);

figure
% Represents data as a Surface
surf(PROJ_LONG, PROJ_LAT, PROJ_Z, 'edgecolor', 'none');

figure
% Plots Filled 2-D Contour Plots
contourf(PROJ_LONG, PROJ_LAT, PROJ_Z);

%% Plot Type 4
% Creates 2-D or 3-D Delaunay Triangulation from set of points
dt = delaunayTriangulation(X, Y);
tri = dt.ConnectivityList;
xi = dt.Points(:, 1);
yi = dt.Points(:, 2);
zi = F(xi, yi) ;

figure
% Plots 3-D triangular surface using vectors X, Y, and Z, and triangle connectivity matrix T
trisurf(tri, xi, yi, zi) 
view(2)
shading interp
```

![XYZ Plot 1](/images/xyz_plot_1.png)
![XYZ Plot 2](/images/xyz_plot_2.png)
![XYZ Plot 3](/images/xyz_plot_3.png)
![XYZ Plot 4](/images/xyz_plot_4.png)
![XYZ Plot 5](/images/xyz_plot_5.png)

---

**Here's another [example](https://se.mathworks.com/matlabcentral/answers/491600-how-do-i-create-a-3-dimensional-response-surface-plot-from-x-y-z-points) illustrating previously discussed functions:**

```matlab
X = [288 318 127 132 264 200 268];
Y = [2.79 4.64 2.31 7.16 2.31 2.60 3.06];
Z = [7.55 14.28 8.31 17.27 4.32 6.74 15.12];

%% Apply cubic interpolation 
[xGrid,yGrid] = meshgrid(linspace(min(X), max(X)), linspace(min(Y), max(Y)));
zGrid = griddata(X(:), Y(:), Z(:), xGrid(:), yGrid(:), 'cubic');
zGrid = reshape(zGrid, size(xGrid));

%% Visualize the result
figure
contour(xGrid, yGrid, zGrid, 'ShowText', 'on')
hold on
scatter(X, Y, 'ro')
grid on
colorbar
```

![Surface Plot](/images/surface_plot_example.png)

**Now, try these out yourself:**
- Initialize temperature in Fahrenheit and convert it to Celsius.
- Convert value in radians to degree.
- Calculate the value *tan of pi*, but prevent the output from being displayed.
- Generate the first 20 Fibonacci numbers using loop and then display the vector as bar plot.
- Print the table of a random number (*between 5 and 15*), using loops. Like `13 * 1 = 13` [...] `13 * 10 = 130`.

**Also, try and encode these (word problems)[https://themathpage.com/Alg/word-problems.htm]:**
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

Also, try out **MATLAB's [GPS receiver simulation model](https://se.mathworks.com/help/nav/ref/gpssensor-system-object.html).**
Or, run this `openExample('shared_positioning/GenerateGPSPositionMeasurementsFromStationaryInputExample')` in the **Command Window**.

Also, try out **MATLAB's [Underwater Target Detection with an Active Sonar System](https://se.mathworks.com/help/phased/ug/underwater-target-detection-with-an-active-sonar-system.html).**
Or, run this `openExample('phased/ActiveSonarExample')` in the **Command Window**.

## Sources
1. "Introduction to MATLAB Programming" Courseware [https://se.mathworks.com/academia/highschool/courseware/introduction-to-matlab.html]
2. Get Started with MATLAB [https://se.mathworks.com/help/matlab/getting-started-with-matlab.html]
