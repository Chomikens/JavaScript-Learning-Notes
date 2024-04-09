# JavaScript Engines
Java Script is interpreted language. What does it mean?

Consider the JavaScript statement:

```js
const awsome = 'JavaScipt is awsome'
```

A JavaScript engine would take this high-level instruction and, through the processes described above, translate it into binary instructions that the processor can execute directly. This is a simplified view of what happens, as the actual machine code will involve memory allocation, value assignment, and potentially garbage collection processes.


In programming, translating high-level code into machine language (or another form of executable instructions) can be achieved through two primary methods: interpretation and compilation.

## Interpreters
An interpreter directly executes the instructions in the source code on the fly, without converting the code into machine language ahead of time.  It parses, interprets, and executes each line of code one by one. This process involves reading the source code, analyzing and converting it into an intermediate representation, and then executing it directly.

-   **Advantages**:
    -   **Immediate Execution**: Since interpretation happens in real-time, it is easier to debug and test code because you can get immediate feedback.
    -   **Portability**: Interpreted languages can run on any platform without the need for recompilation since the interpreter itself handles the execution.
-   **Disadvantages**:
    -   **Speed**: Interpreted code runs slower than compiled code because the source code is analyzed and executed on the fly (for example in loops).

## Compilers 
 A compiler translates the entire source code of a program into machine language (or an intermediate form) before the program is executed. The compilation process involves several stages, including lexical analysis, parsing, semantic analysis, optimization, and code generation. The result is a standalone executable file or object code.

-   **Advantages**:
    -   **Performance**: Compiled code runs faster than interpreted code because the translation happens before execution, allowing for optimization.
    -   **Optimization**: Compilers can optimize the code during the compilation process, improving the efficiency of the executable program.
-   **Disadvantages**:
    -   **Compilation Time**: The process of compiling a program can be time-consuming, especially for large projects.
    -   **Platform Dependency**: Compiled executables are often platform-specific. To run the program on a different platform, you need to recompile the code for that specific platform.


## JiT Compilers 
Imagine you're translating a book from one language to another. You could do it all at once before anyone reads it (like a traditional compiler), or translate each sentence as someone reads it out loud (like an interpreter). A JIT compiler blends these two methods in a clever way, aiming to get the best of both worlds.

-   **A Simple Idea**: A JIT compiler is like a smart translator for computer programs. Instead of translating the whole program before you start using it (which can take a lot of time) or translating it as you go (which can be slow), it waits until the last minute to do the translation. This way, it only translates the parts that you're actually using, and it does so just in time for you to use them.
-   **Why It's Cool**: This method helps your programs run faster because it's doing the heavy lifting only for the parts you need, right when you need them. It's like having a translator who knows exactly which parts of the book you're going to read next and prepares them for you in advance.

### How it works? 

1.  **Starting Off**: Imagine your program is a play, and the JIT compiler is the director. The play is written in a language that not all actors understand completely.
2.  **During the Show**: As the play goes on, the director (JIT compiler) quickly teaches the actors (the computer) their lines (the code) in a language they understand, just before they need to perform them. This way, there's no delay; the show goes on smoothly and quickly.
3.  **Selectively Choosing**: The director doesn't teach every line to every actor at once. Instead, they focus on the lines that are most important or are repeated often, making the process efficient and the performance smoother.

In essence, JIT compilers make your computer programs run faster and more efficiently by being smart about how and when they translate the program's code into a language your computer understands. It's a behind-the-scenes hero that helps everything run smoothly without you having to worry about the details.

## Transpilers 
A transpiler, also known as a source-to-source compiler, converts source code written in one programming language into the source code of another language at the same abstraction level. Transpilers are often used for language transformation tasks such as converting TypeScript to JavaScript or enabling new language features in environments that do not natively support them.

-   **Advantages**:
    -   **Language Features**: Allows developers to use new or extended language features not supported in the target environment.
    -   **Cross-Platform Development**: Facilitates writing code in a preferred language and then transpiling it to the language required by the platform.
-   **Workflow Integration**: Transpilers are commonly integrated into the development workflow, alongside or as part of the build process, to automatically convert source code as needed.

