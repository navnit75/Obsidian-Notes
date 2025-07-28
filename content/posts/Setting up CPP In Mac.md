 Well after seeing countless videos, let me summarize it for you !!!
 
 There are two types of compiler variant available for MAC. 
1. Provided by **xcode-developer support** called `clang`
2.  Another one is provided by GCC/GNU , can be downloaded by command `brew install gcc`


To check which version you are using 
1. Run `g++` , if it shows `clang` then , you are using xcode variant
2. if it shows some  a string like `g++-13` in the compilation then you are using the GCC/GNU one  

If you want to use both of them, you can easily choose between them :-
1.  `g++-14 <filename> ` : for GNU/GCC 
2.  `g++ <filename>` : for the clang

If you want to work with `bits/stdc++.h` , you must use GNU/GCC based compiler.
1. If you're using `vscode` do check, at which compiler locations your `g++` settings points. 

I just add an `alias` in my `.zshrc` file
```bash
alias g++="g++-14"
alias gcc="gcc-14"
```

But if you do want to execute your code using `clang++` then you can use following command ?
```bash
clang++ -std=c++17 mul_table.cpp
```

> ![question] Why was all this necessary ? 
> - Because of the fact that `clang` doesn't support `#include<bits/stdc++.h>` 
> - Which was annoying for me...
> - Hope this helps !!