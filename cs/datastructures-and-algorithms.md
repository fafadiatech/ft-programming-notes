# Notes on Datastructures and Algorithms

## Reference

1. [Big O Cheatsheet](http://bigocheatsheet.com/)
1. [Datastrcutures from David Kempe, USC](http://www-scf.usc.edu/~csci104/20142/lectures/DataStructures.pdf)
1. [Google Interview University](https://github.com/jgwhite/google-interview-university)
1. [System Design Primer](https://github.com/donnemartin/system-design-primer)
1. [Interactive Coding Chanllenge](https://github.com/donnemartin/interactive-coding-challenges)
1. [Datastructure and Object Oriented Design](http://www-scf.usc.edu/~csci104/20142/lectures/)
1. [Awesome Courses](https://github.com/prakhar1989/awesome-courses#programming-languages--compilers)
1. [Every Programmer Should Know](https://github.com/mr-mig/every-programmer-should-know)
1. [Systems Programming](https://github.com/angrave/SystemProgramming/wiki)
1. [How to Make a Computer Operating System](https://github.com/SamyPesse/How-to-Make-a-Computer-Operating-System)
1. [Awesome CPP](https://github.com/gibsjose/cpp-cheat-sheet)
1. [Google Stack](http://malteschwarzkopf.de/research/assets/google-stack.pdf)
1. [Facebook Stack](http://malteschwarzkopf.de/research/assets/facebook-stack.pdf)
1. [Operating system support for warehouse-scale computing](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.722.1768&rep=rep1&type=pdf)
1. [Application of Binary Search Trees](https://stackoverflow.com/questions/2130416/what-are-the-applications-of-binary-trees)
1. [Standard Template Library](http://web.eng.fiu.edu/watsonh/eel3160/Lectures/STL-Lectures.pdf)
1. [Principles of Algorithmic Problem Solving](http://www.csc.kth.se/~jsannemo/slask/main.pdf)
1. [gods: Go Language Data Structure](https://github.com/emirpasic/gods)
1. [cosmos: Collections of Algorithms implemented](https://github.com/OpenGenus/cosmos)
1. [Compiler Design: Tutorials Point](https://www.tutorialspoint.com/compiler_design/index.htm)
1. [Programming Paradigms for Dummies: What Every Programmer Should Know](https://www.info.ucl.ac.be/~pvr/VanRoyChapter.pdf)
1. [Esstential C](http://cslibrary.stanford.edu/101/EssentialC.pdf)
1. [Notes on Data Structures and Programming Techniques (CPSC 223, Spring 2015)](http://cs.yale.edu/homes/aspnes/classes/223/notes.html)
1. [The Intuitive Guide to Data Structures And Algorithms](https://www.interviewcake.com/data-structures-and-algorithms-guide)
1. [500 Data Structures and Algorithms practice problems and their solutions](https://techiedelight.quora.com/500-Data-Structures-and-Algorithms-practice-problems-and-their-solutions?__filter__&__nsrc__=2&__snid3__=1594232728&share=1)
1. [Stanford: Data Structures](https://web.stanford.edu/class/cs166/)

## Intermedia Data Structures

1. [Rope Science](https://github.com/google/xi-editor/blob/master/doc/rope_science/intro.md)
1. [Gap Buffer](https://en.wikipedia.org/wiki/Gap_buffer)
1. [Text Editor: Data Structures](http://www.averylaird.com/programming/editor/2017/09/30/the-piece-table/)
1. [Piece Table](https://en.wikipedia.org/wiki/Piece_table)
1. [Craft of Text Editing](http://www.finseth.com/craft/craft.pdf)
1. [Streams: a new general purpose data structure in Redis.](http://antirez.com/news/114)
1. [What are the lesser known but useful data structures?](https://stackoverflow.com/questions/500607/what-are-the-lesser-known-but-useful-data-structures)]
1. [Log Structured Merge Trees](https://en.wikipedia.org/wiki/Log-structured_merge-tree)
1. [Concurrent Data Structures](https://www.cs.tau.ac.il/~shanir/concurrent-data-structures.pdf)
1. [Sketching Datastructures](http://lkozma.net/blog/sketching-data-structures/)

## C++ Programming

1. [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)
1. [Bjarne Stroustrup's C++ Style and Technique FAQ](http://www.stroustrup.com/bs_faq2.html#slow-containers)
1. [More C++ Idioms](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms)
1. [C++ Node.js integration](https://nodeaddons.com/c-processing-from-node-js/)
1. [googletest](https://github.com/google/googletest/blob/master/googlemock/docs/ForDummies.md)
1. [Learning C++](https://blog.tartanllama.xyz/learning-cpp/)
1. [Stanford: Standard C++ Programming Course](http://web.stanford.edu/class/cs106l/lectures.html)
1. [Stanford: Programming Abstractions](https://see.stanford.edu/Course/CS106B)
1. [Stanford: Programming Paradigms](https://see.stanford.edu/Course/CS107)

## Dynamic Programming

- Dynamic Programming is class of problems that have following properties:
    1. Objective Function and Constraints {Maximize Value Given Some Condition}
    1. State {Each problem have control variables}
    1. Sub Structure {Problem can be divided into sub-problems}
    1. Decision Point {At each step you're trying to minimize/mazimize something}
- Dynamic Programming can furthure be divided into:
    1. Top Down Approach: Start with  solving the problem. If sub-problem is already solved return the result {This technique uses Memoization}
    1. Bottom Up Approach: Start with sub-problems/trivial cases and build final solution
- Common Patterns in Dynamic Programming:
[What are the top 10 most popular dynamic programming problems among interviewers?](https://www.quora.com/What-are-the-top-10-most-popular-dynamic-programming-problems-among-interviewers)
    1. 0/1 Knapsack Problem
    1. Coin Changing Problem: Given collection of coin denomination {with infinite supply} and a total value, find minimum number of coins needed to realize total value
    1. Longest Increasing Subsequence: Given an array, find the sub-sequence of numbers with increasing value
    1. Min Edit Distance: Given two strings, how many edits would it take to convert strings
    1. Longest Common Subsequence: Given two strings find subsequnce of longest common sub-sequence
    1. Text Juxtification: Given a string and width how would you adjust the string so that each line fits within that width
    1. Word Break Problem: You are given a long word and a dictionary, find if long wod is present in dictionary
    1. Sting interleaving problem: Given 3 strings see if a combination of 2 strings produce 3 strings
    1. Subset sum problem: You are given
- Other References:
    1. [Dynamic Programming – From Novice to Advanced](https://www.topcoder.com/community/data-science/data-science-tutorials/dynamic-programming-from-novice-to-advanced/)
    1. [DP Zoo Tour](http://blog.ezyang.com/2010/11/dp-zoo-tour/)

## Blog

1. [Image Dithering: Eleven Algorithms and Source Code](http://www.tannerhelland.com/4660/dithering-eleven-algorithms-source-code/)
1. [Visual explaination of compression algorithms](https://unwttng.com/compression-decompressed)
1. [Consistent Hashing](http://www.acodersjourney.com/2017/10/system-design-interview-consistent-hashing/)
1. [The Simple Magic of Consistent Hashing](http://www.paperplanes.de/2011/12/9/the-magic-of-consistent-hashing.html)
1. [A Fast, Minimal Memory, Consistent Hash Algorithm](https://arxiv.org/pdf/1406.2294.pdf)
1. [AlgoWiki](https://github.com/vicky002/AlgoWiki)
1. [Parson's Code](https://en.wikipedia.org/wiki/Parsons_code)
1. [Acoustic fingerprint](https://en.wikipedia.org/wiki/Acoustic_fingerprint)
1. [How does Shazam work?](https://www.acrcloud.com/blog/how-does-shazam-work)
1. [pyAudio Extraction Features](https://github.com/tyiannak/pyAudioAnalysis/wiki/3.-Feature-Extraction)