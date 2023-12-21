# 留学生日常作业/课程设计/代码辅导/CS/DS/商科，仅为漂洋过海的你❥
标签：Computer Science、Data Science、Business Administration，留学生编程作业代写&&辅导

## 个人介绍:
本人是一名资深码农，酷爱投资。

为您提供 CS , DS , 商科 编程作业代写

<img src="design2023866.jpg"  width="200" />

2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 1/15
Project 3
Due Dates
Project Quiz (https://canvas.umn.edu/courses/391252/quizzes/814187) : 11:59pm, October 27
2023, Canvas
Project Code: 11:59pm, November 6, 2023, Gradescope
8.75% of Course Grade
Projects are individual work: No collaboration with other students is allowed.
Starter Code: proj3-code.zip (https://csci2021-fa23.s3.amazonaws.com/proj3-code.zip)
How to Succeed on This Project
1. Read the entirety of this spec in detail. It contains a lot of information that will make the project
go more smoothly if you take the time to understand it before starting your project. Assembly
programming is particularly dependent on small details. This document contains a number
of helpful pointers that will save you pain further down the line.
2. Know the purpose of each file in the starter code. You will only need to modify two files to
complete the project, but you should read this specification to understand why the other files are
present. In particular, understand which files you are not allowed to modify to avoid
autograder issues.
3. Know how to run your code independently of the Makefiles we provide. As with the last
project, the test results alone are not enough to tell you what is going wrong with your code,
perhaps even more so now that we are working directly with assembly. You will need to be able to
test your code and inspect it with gdb to figure out precisely where it may be producing
undesirable results.
4. Expect to get stuck, and exercise patience and persistence. This project has both an
assembly coding element and a puzzle solving element. Assembly code can be very error-prone
and will require time and careful thinking to do correctly. Part 2 of the project involves solving a
series of puzzles in an assembly program and will also require time and thinking to solve. We are
happy to help in office hours but will not give out direct solutions.
5. Start early. Give yourself time to get stuck, discover insights and solutions to something that
initially seems challenging, and overcome obstacles. It can be hard to think methodically about
assembly code or creatively about puzzle solutions when faced with the pressure of an imminent
deadline.
6. If you have questions, your best option is to ask in a public Piazza post. This gets your question
in front of as many people as quickly as possible and also lets others benefit by seeing the
answer to your question.
7. Familiarize yourself with the late submission policy detailed in the syllabus so that you are not
caught off-guard. No submissions are accepted more than 48 hours after the deadline.
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 2/15
Project extensions are not granted except in the case of a documented and acute
emergency.
8. The two parts of this project are independent, so you should feel free to switch between them. If
you get stuck in Part 1, try making some progress on Part 2, and vice versa.
Introduction
In Project 3, we essentially move one “level down” from Project 2, transitioning from C to assembly.
In Part 1, you will implement solutions to the same bitwise puzzle problems seen in Project 2, this
time in assembly.
In Part 2, you will be given another puzzle program to reverse engineer via gdb . However, you
will no longer have access to the C source code for this program. Rather, you will be working
directly with a binary program and stepping through its instructions.
Working with assembly will get you much more acquainted with the low-level details of x86 and also
give you a greater appreciation for the features of “high-level” languages like C.
Grading Criteria
Credit for this assignment will be awarded based on the following categories:
Project Quiz (10%): A quiz (https://canvas.umn.edu/courses/391252/quizzes/814187) on this
assignment specification and the project starter code has been posted to Canvas. Complete the
quiz by the due date. The quiz is to be completed individually but multiple attempts are allowed.
Automated Testing of Bitwise Puzzle Solutions (35%): The starter code features the btest
and cc_check programs to check the correctness of each of your puzzle solutions. We will use
the same programs to evaluate your puzzle solutions in the autograder.
Manual Inspection of Bitwise Puzzle Solutions (20%): We will inspect your assembly code
solutions to the bitwise puzzles to evaluate coding style. This includes aspects like consistent
indentation and comments. Because assembly code is even less self-explanatory than C code,
comments become particularly important in this venue. Make sure to thoroughly comment your
code.
Score on “Binary Bomb” Problem (35%): We will be running a grading server to track your
progress through the phases of the “Binary Bomb” puzzle program that comprises Part 2 of the
project. This server will track and adjust your score as you make progress on the puzzle, and we
will use its logs to assign you a score based on your progress at the time of the project deadline.
Starter Code
Download the zip file linked at the top of this page to obtain a portion of the start code for this project.
This zip contains the starter code for Part 1. You will need to follow the special instructions
below to obtain your “Binary Bomb” for Part 2.
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 3/15
File Purpose Notes
Makefile Submit Use to run make zip before submission
bitwise/Makefile Build and Test
Build file to compile code and run test
cases for Part 1
bitwise/bits.s Edit
Your solutions to the bitwise puzzle
problems for Part 1. We have defined an
assembly function for each problem, and
you will need to fill in each function’s body
with your solution.
bitwise/btest.c Testing Testing code for bitwise puzzle problems
bitwise/bits_test.h Testing Testing code for bitwise puzzle problems
bitwise/bits_test.c Testing Testing code for bitwise puzzle problems
bitwise/btest_server.c Testing Testing code for bitwise puzzle problems
bitwise/bits_impl.h Testing Testing code for bitwise puzzle problems
bitwise/dl_protocol.h Testing Testing code for bitwise puzzle problems
bitwise/sema.c Testing Testing code for bitwise puzzle problems
bitwise/sema.h Testing Testing code for bitwise puzzle problems
bitwise/cc_check Testing Testing code for bitwise puzzle problems
bitwise/ishow.c Utility
Helpful program for showing integer
representations
bitwise/fshow.c Utility
Helpful program for showing floating-point
representations
bombNN.zip Download
Part 2 debugging problem. Download from
Server
bombNN/ Directory
Created by unzip bombNN.zip and contains
the files below.
bombNN/bomb.c Provided Part 2 main() definition for bomb
bombNN/bomb Provided Part 2 executable to debug
bombNN/README Provided Describes the “owner” of the bomb program
bombNN/input.txt Edit Input for the bomb program, fill this in.
Part 1: Bitwise Puzzles in Assembly
The first part of this project focuses on files in the bitwise directory. We recommend that you work
within this subdirectory of the starter code for the duration of this part of the project (e.g., using cd in
your terminal).
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 4/15
All puzzles from Project 2 are included again here. Many of the same files from Project 2 are present
again here, although there are some new files for testing as well. The key difference is that the C file
bits.c has been replaced by the assembly file bits.s in Project 3.
The first thing you will likely want to do is run the make command within this subdirectory to compile
the starter code and the useful utilities it provides. This includes ishow , fshow , and the testing
infrastructure ( btest , which you will invoke directly, and the auxiliary btest_server executable). dlc
is no longer needed for Project 3 because you are writing assembly rather than C. However, we have
added a new code checking utility, cc_check , which will verify that your assembly code adheres to
the prescribed x86-64 calling convention.
Note: If you wish to compile this code in your own Linux environment rather than the CSE Labs
machines, you will need to install 32-bit variants of the standard C libraries. With Ubuntu, you can do
this with the following command:
sudo apt install gcc-multilib
Your task is to fill in the bits.s file with solutions to the 12 bitwise puzzle problems. The starter
version of each function simply returns the value 2 for any input. For example:
.global isZero:
minusOne:
 movl $2, %eax
 ret
Many of the coding restrictions of Project 2 are no longer in effect for Project 3. You are free to use
whatever operations you wish, aside from floating-point instructions to implement the solution to each
puzzle. You still may not define any new functions or call any functions from your assembly code.
As long as you adhere to these restrictions, you are free to use any other assembly instructions you
would like. This means there are often more straightforward means of solving each puzzle than
directly translating your C code into assembly, but there are some puzzles where such a
translation will still be the easiest means of obtaining a solution. For example, you may find that
conditionals through the cmpl and testl instructions combined with jumps are more straightforward
ways to solve certain puzzles than a direct replication of what your C solutions were doing in Project
2.
While you are welcome to study the assembly that gcc generates for your Project 2 solutions,
submitted code that is clearly compiler-generated with no hand coding will receive no credit.
No credit will be given on manual inspection, and penalties will be assessed to the autograderdetermined portion of your grade to lower the score to 0.
The Puzzles
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 5/15
The puzzles that you will be solving in bits.s are described below, in the same order as the
functions defined in the provided assembly code.
The puzzles are ordered roughly from least difficult to most difficult. The Rating column gives the
difficulty rating (which also corresponds to the number of points awarded for solving the puzzle).
You will definitely want to consult your C solutions to these puzzles from Project 2 as a starting point.
If you weren’t able to solve one or more puzzles in C from Project 2, contact Prof Kolb who will help
you get those up and running.
Name Description Rating
isZero Returns 1 if the input x is 0 , and 0 otherwise 1
bitNor Compute ~(x|y) for inputs x and y 1
distinctNegation Returns 1 if x != -x for input x and 0 otherwise 2
dividePower2
Compute x/(2^n) for inputs x and n where 0 <= n <= 30 .
Round toward zero.
2
getByte Extract byte n from word x for inputs x and n 2
isPositive Return 1 if x > 0 and return 0 otherwise 2
floatNegate Return bit-level equivalent of expression -f for input f 2
isLessOrEqual If x <= y then return 1 , otherwise return 0 3
bitMask
Generate a mask consisting of all 1 bits between the
specified positions
3
addOK Determine if we can compute x+y without overflow 3
floatScale64 Return bit-level equivalent of expression 64*f for input f 4
floatPower2
Return bit-level representation of the expression 2.0^x for any
32-bit integer x
4
Writing x86-64 Assembly
You will implement your bitwise puzzle solutions in x86-64 assembly, the same assembly variant we
have studied extensively in lectures and labs. One of the most important aspects of writing
assembly code is respecting the standard calling convention, particularly the rules about
when and how different registers may be used.
Name (64
bits)
Name (32
Bits)
Role Notes
%rax %eax General-Purpose
Caller-Save, Holds Function Return
Values
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 6/15
Name (64
bits)
Name (32
Bits)
Role Notes
%rbx %ebx General-Purpose Callee-Save
%rcx %ecx General-Purpose Caller-Save, Fourth Argument
%rdx %edx General-Purpose Caller-Save, Third Argument
%rsi %esi General-Purpose Caller-Save, Second Argument
%rdi %edi General-Purpose Caller-Save, First Argument
%rbp %ebp General-Purpose Callee-Save
%r8 %r8d General-Purpose Caller-Save
%r9 %r9d General-Purpose Caller-Save
%r10 %r10d General-Purpose Caller-Save
%r11 %r11d General-Purpose Caller-Save
%r12 %r12d General-Purpose Callee-Save
%r13 %r13d General-Purpose Callee-Save
%r14 %r14d General-Purpose Callee-Save
%r15 %r15d General-Purpose Callee-Save
%rip %eip Program Counter Do Not Modify Directly
%rsp %esp Stack Pointer Only change to expand/shrink stack
You are free to use any of the general-purpose registers to hold values. Be sure to respect the
callee-save or caller-save rules, otherwise your code will break in strange ways.
1. Usually, try to stick to the caller-save registers as you can use them freely in your function
implementations (particularly since your bitwise functions won't be calling any other functions).
2. If necessary, you can use callee-save registers if you need to store more temporary values, but
make sure to push them to the stack first and pop them back (in reverse order) before you return.
Note that even if you will only need to use a 32-bit callee-save register (e.g., %ebp ), you
must push the entire 64-bit register to preserve its full value first (e.g., with push %rbp ) and
pop the full 64 bits later.
3. You should use %rsp only to adjust the size of the stack, or as part of an operand when retrieving
values from memory.
4. Do not modify %rip as you will break your code.
Other Advice
Probably the most important advice for assembly coding (as identified by both instructors and
your fellow students who have taken 2021): Put tons of comments in your assembly code. In
particular, use comments to help you track which registers are being used to store which values,
like so:
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 7/15
movl %edi, %eax # %eax holds first argument x
andl $0xFF, %eax # %eax holds x & 0xFF
Use descriptive label names when writing jumps. Each label must have a globally unique name,
so you may want to prefix it with an abbreviation for the function you’re currently writing, e.g.,
FLOAT_SCALE_64_RETURN_0 . Also, avoid leading . characters in your label names, as they can
confuse the assembler.
Prefer caller-save registers over callee-save registers. If possible, only use the former in your
solution. The staff solutions do not require the use of any callee-save registers and use only
caller-save registers.
Don’t forget the $ in front of constant values, e.g., $0xFF . Otherwise, assembly will treat that
number as a memory address.
For shift instructions like shll and sarl , if you wish to shift by a variable number of bit positions,
the shift amount must go in the %ecx register. For example, shll %ecx, %eax is legal, but shll
%eax, %ecx is not.
You may see your program crash and report a floating point error. This error message can be
misleading, as the problem may actually stem from an integer division instruction like idivl .
Make sure you have set up all registers (e.g., with cqto and related instructions) correctly before
you perform a division.
Debugging Your Assembly Code
Print statements are no longer a viable option in assembly. You will need to use gdb to inspect your
running code and the intermediate values stored in registers. Here is a good sequence of steps to get
gdb up and running with your code.
First, launch gdb and specify the btest binary as the program being debugged (make sure to
compile your latest changes first):
> gdb btest
Next, enable the invaluable tui mode:
(gdb) tui enable
You will want to view both assembly code and register contents as the btest program executes.
(gdb) layout asm
(gdb) layout regs
Set a breakpoint at the start of the function you are trying to debug, for example:
(gdb) break isZero
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 8/15
Set the command-line arguments to btest_driver . The syntax for these arguments is the same as
for the btest program in Project 2. See the Project 2 spec for full details. For example, if you want to
test the execution of bitXor(4, 5) , you would do the following:
(gdb) set args -f bitXor -1 4 -2 5 -T 0
You should always include -T 0 as an argument to the btest_driver program when running it
under gdb . This disables the “timeout” mechanism that allows the btest_driver program to detect
non-terminating code when run directly from the command-line.
If you fail to include -T 0 , you won’t be able to debug your code within gdb . This is because
the program will jump to a timeout handler function when you are in the middle of trying to debug your
own function.
Unfortunately, Project 3's btest program can be quite a bit slower than Project 2's btest
program. You will almost certainly want to use the -f command-line flag to specify testing for a
specific puzzle to save yourself time.
Part 2: The Binary Bomb
Quick Links
Available Only Lab Machines or on VOLE
Download Bombs
http://52.87.93.66:15213
(http://52.87.93.66:15213)
Score Board
http://52.87.93.66:15213/scoreboard
(http://52.87.93.66:15213/scoreboard)
More details on these are described in subsequent sections.
Overview
The nature of this problem is similar to the previous project's puzzlebox : there is a program called
bomb which expects certain inputs from a parameter file or typed as input. If the inputs are "correct",
a phase will be "defused" earning points and allowing access to a subsequent phases. The major
change is that the bomb program is in binary, so it must be debugged in assembly.
Below is a summary of useful information concerning the binary bomb.
Bombs are Individual
The bomb you will download contains subtle variations so that the solution to yours will not work on
other bombs. Projects are individual work and you'll need to ultimately defuse your own bomb.
Bombs are Binary
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 9/15
A small amount of C code with the main() function is included but the bulk of the code is binary
which will require using gdb to debug the assembly code.
Bombs only Run on Lab Machines
To stay in contact with the scoring server, bombs won't run on your laptop. You'll need to work on
them on the CSE Labs machines, either in person or remotely via SSH.
Bombs Take Input
Similar to puzzlebox , create an input.txt file which will contain your answers. Run bombs with this
input file. Note that if the bomb runs out of input, you can type input directly into the bomb though
this may look a little funny in the debugger.
Defusing Phases Earns Points
As with the earlier puzzlebox , points for this problem are earned based on how many phases are
completed. Each phase that is completed will automatically be logged with the scoring server.
Bomb Explosions Lose Points
If incorrect input is entered and the bomb program is allowed to exit, it will "explode" which causes
credit to be deducted. See the scoring system for details. This can be prevented by setting
breakpoints prior to the explosion sequence and restarting the bomb when those breakpoints are
hit. Bomb explosions are final -- you cannot regain these points once lost.
Use GDB to work with Bombs
The debugger is the best tool to work with running bombs. It may be tempting to try to brute force
the bomb by trying many possible inputs but this may lead to many explosions or crashing the
scoring server. Both of these are a bad idea so work with your bomb by hand.
Machines on Which Bombs Will Run
The binary bomb makes frequent contact with a scoring server so you can only run it on the CSE
Labs machines listed below:
Machine Login Address Location
Login
Machines
login01.cselabs.umn.edu
... Machine Room
login07.cselabs.umn.edu
VOLE csel-vole01.cselabs.umn.edu
Virtual
(http://vole.cse.umn.edu/)
csel-vole02.cselabs.umn.edu
…
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 10/15
Machine Login Address Location
csel-vole99.cselabs.umn.edu
1-250
Lab
csel-kh1250-
01.cselabs.umn.edu
… Keller 1-250
csel-kh1250-
37.cselabs.umn.edu
1-260
Lab
csel-kh1260-
01.cselabs.umn.edu
...
csel-kh1260-
20.cselabs.umn.edu
Keller 1-260
1-262
Lab
csel-kh1262-
01.cselabs.umn.edu
... Keller 1-262
csel-kh1262-
28.cselabs.umn.edu
L-102
Lab
csel-lindl102-
01.cselabs.umn.edu
... Lind L102
csel-lindl102-
35.cselabs.umn.edu
106 Lab
csel-w106-
01.cselabs.umn.edu
... Walter 106
csel-w106-
33.cselabs.umn.edu
B28 Lab csel-wb28- Walter B28
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 11/15
Machine Login Address Location
01.cselabs.umn.edu
...
csel-wb28-
27.cselabs.umn.edu
Attempting to run a bomb on an unauthorized machine will error out immediately as in
> ./bomb
Initialization error: illegal host 'my-laptop'.
Legal hosts are as follows:
 csel-w106-01
 csel-w106-02
 csel-w106-03
 ...
Bomb Download and Setup
Download your bomb from the following web address
http://52.87.93.66:15213 (http://52.87.93.66:15213)
This site must be accessed from a CSE Lab machine listed above or Vole. Using a browser
on Vole (http://vole.cse.umn.edu/) is the easiest way get a bomb onto your CSELabs account
when you are working remotely (and will let you tell friends "I've used a browser inside a
browser.").
Enter your UMN X.500 information (login ID) in the required fields: IDs that don't correspond to
members of the class will be rejected. If you have problems getting a bomb, contact Prof Kolb.
The bomb will download as a .zip file. On Unix machines, extract the contents using the
command unzip as in
 > ls
 bomb10.zip
 
 > unzip bomb10.zip
 bomb10/README
 bomb10/bomb.c
 bomb10/bomb
 
 > ls
 bomb10.zip bomb10/
 
 > cd bomb10
 > ls
 bomb* bomb.c README
Save your bomb directory in your proj3-code directory, alongside the bitwise
subdirectory. You will need to submit your bomb files on Gradescope along with your
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 12/15
bitwise code. With this arrangement, you can simply use make zip to prepare an archive
for submission.
The resulting bomb is unique for the downloader and the owner is in the README and logged on
the download server.
The file bomb (sometimes listed with a * to indicate it is executable) is a compiled binary so
employ your assembly gdb skills to crack it.
Create a file input.txt . The bomb can be run with this file as input like so:
> ./bomb input.txt
but you'll likely want to do this in gdb to avoid exploding the bomb.
Unlike previous puzzles, if input.txt runs out of input, the bomb will prompt for you to type input.
This can be a way to explore ahead a little bit in the bomb after solving a phase.
Bomb Scoring
Scoring is done according to the following table.
Pts Phase Notes
10 Phase 1
10 Phase 2
10 Phase 3
10 Phase 4
10 Phase 5
5 Phase 6
5 Explosion Reduced by 0.5 each time bomb program "explodes"
Explosion Penalty: 0.5 points are deducted for each explosion up to 10 explosions. We will only
enact a deduction (by 1 point) for every two explosions (see below for examples).
Upon successfully defusing a stage, the bomb will contact a server that tracks scores by bomb
number. The scoreboard is here:
http://52.87.93.66:15213/scoreboard (http://52.87.93.66:15213/scoreboard)
The server is reachable only on one of the CSE Lab machines listed above or on VOLE.
You'll need to know your bomb number to see your score, but can also see the scores of others.
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 13/15
Examples of Scoring
Phases
Defused
Explosions Computation Final Score Notes
6 1
55 + (5 -
floor(0.5*1) )
60 1 explosion for free
6 4
55 + (5 -
floor(0.5*4) )
58
6 10
55 + (5 -
floor(0.5*10))
55
6 20
55 + (5 -
floor(0.5*10))
55 Only count 10 explosions
5 7
50 + (5 -
floor(0.5*7))
52
Round down for explosion
penalties
4 4
40 + (5 -
floor(0.5*4))
43
1 0
10 + (5 -
floor(0.5*0))
15
0 2
0 + (5 -
floor(0.5*2))
4
Even trying with an
explosion gets something
0 10
0 + (5 -
(floor(0.5*10)
0
Getting Credit for the Problem
Ensure that the score listed on the Scoreboard site (http://52.87.93.66:15213/scoreboard)
reflects your progress.
Ensure your input.txt along with your bombNN/ directory are in your project directory with the
rest of your code. You will need to submit these files alongside your bitwise assembly code
on Gradescope.
Warning: Do Not Download Multiple Bombs
It is possible to download multiple bombs but this will not reset your explosion count. Quite the
opposite: the scoring system on the server uses the following conventions.
Only the maximum phase defused in any bomb adds points
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 14/15
Total explosions across ALL bombs subtract points with each separately downloaded bomb
contributing up to -5 points.
Since more bombs likely means more explosions, you are strongly advised to download only a single
bomb and work with it.
Advice
If you accidentally run the bomb from the command line, you can kill it with the Unix interrupt key
sequence Ctrl-c (hold control, press C key).
 > ./bomb
 Welcome to my fiendish little bomb. You have 6 phases with
 which to blow yourself up. Have a nice day!
 ^C
 So you think you can stop the bomb with ctrl-c, do you?
 Well...OK. :-)
 > 
Most of the time you should run the bomb in gdb as in
> gdb ./bomb
Refer to the Guide to GDB (https://canvas.umn.edu/courses/391252/pages/gdb-guide) if you have
forgotten how to use gdb and pay particular attention to the sections on debugging assembly.
Figure out what the explosion routine is called and always set a breakpoint there. This will allow
you to stop the bomb.
Make use of other tools to analyze the binary bomb aside from the debugger. Some of these are
described at the end of the Guide to GDB (https://canvas.umn.edu/courses/391252/pages/gdbguide) . They will allow you to search for "interesting" data in the executable bomb . The author of
the bomb is encoded in the binary as a string somewhere which may be relevant to inputs for
some phases.
Disassemble the executable to look at its entire source assembly code as a text file. The Guide
to GDB (https://canvas.umn.edu/courses/391252/pages/gdb-guide) shows how to use objdump to
do this. Looking at the whole source code reveals that one cannot hide secrets easily in
programs.
Project Submission
You will submit your code to Gradescope as you have for Projects 1 and 2. While Gradescope will not
determine your score on the binary bomb exercise (the bomb scoring server fills this role), you are
still required to submit your bomb directory and an input.txt file that can serve as input to the bomb
program.
To submit, first ensure that your code adheres to the following directory structure:
2023/10/25 04:28 Project 3: CSCI 2021 Machine Architecture and Organization (Fall 2023)
https://canvas.umn.edu/courses/391252/pages/project-3 15/15
project3-code/
 Makefile
 bitwise/
 Makefile
 bits.c
 bits.h
 ...
 bombNNN/ # NNN will be a unique number
 input.txt
 bomb
 bomb.c
 README
 ... 
Next, use the make zip command from within the project3-code directory (Not your bitwise or
bomb subdirectories) to create a zip archive suitable for upload to Gradescope. If you need a
refresher on how to use Gradescope, see the instructions at the end of the Lab 1 assignment.
Troubleshooting and Hints
Q: I am not able to compile the bitwise code in my own Linux environment.
A: This same issue occurs with Project 2. Make sure you have installed the necessary packages to
compile 32-bit binaries with gcc . On Ubuntu, you will need to install the gcc-multilib package (e.g.,
with the command sudo apt install gcc-multilib ).
Q: When I run my bitwise code, it crashes and reports a floating point error.
A: Be sure you have done all of the necessary register setup (e.g., with cqto and related
instructions) before doing any division.
Q: When I try to use gdb with my bitwise code, it keeps jumping to a timeout handler and I
can't see my own code.
A: Make sure that you instruct the btest program not to enforce a timeout. You can do this by
passing the command line arguments -T 0 .
Q: My bomb program doesn't seem to see/use the last line in my input.txt file.
A: If this is happening to you, you are probably using VS Code. Add an extra blank line at the end of
your input.txt file to fix this. If you're curious, it isn't the bomb but rather VS Code that is broken
(https://stackoverflow.com/questions/44704968/) in this situation.

## 作业代写价格:

|类型|美元|人民币|
|-----:|-----:|-----:|
|Assignment|$60-$120|¥400-¥800|

### 为了方便快速定价和确定是否代做，麻烦提供私聊的时候提供以下信息：
如果是作业，提供本次作业要求文档；如果是考试，提供考试范围和考试时间
一两句话概括一下作业任务或者考试任务，比如”可以帮忙实现一个决策树算法吗？”、”网络安全选择题考试，范围是内网横向移动知识点”
### 作业定价有两种方式：
    - 根据定价标准进行
    - 通过微信我们一起协商
## 联系方式

微信（WeChat）：design2023866

<img src="design2023866.jpg"  width="200" />
