# G
a postscript golfing library

The 'G' library offers a base-level, activated by running the file within your Postscript program `(G)run`, defining these functions:

 * *integer*  `.`  *-*  
    execute operator by code-number (PLRM, Appendix F)
 * *string*  `$`  *-*  
    execute each char in string using `.`
 * *string*  `@`  *-*  
    execute each char in string using `.`, first subtracting 32
 * *string*  `#`  *-*  
    execute each char in string using `.`, first adding 95
 * composite [index-array]  `!`  *-*  
    fetch value from nested composite object using indices from array
 * composite [index-array] object  `*`  *-*  
    store value in nested composite object using indices from array

An optional level, selected by prefixing the number 1 to the library-load command `1(G)run`, adds abbreviated operator names. As with the `.` and other operator shortcut functions, the names correspond to the System Names Table. The names in the abbreviation dict are generated by enumerating the codes in descending order, scanning them to produce operator objects and defining them in a dictionary. Since the codes as listed in the PLRM Appendix F are already alphabetized, this results in the shortest, earliest (alphabetically) name for each operator.

An optional level, selected by prefixing the number 2 and suffixing the dollar-sign `$` to the library-load command `2(G)run $` (or just suffixing the letter `D`, eg. `(G)run D`), begins an *implicit-procedure block*. Each line, until the next blank line is scanned and defined as upper-case single-letter names, `/A` `/B` `/C` ....

The two options may be combined by prefixing the number 3 and suffixing the dollar-sign `$`. The trailing dollar-sign is needed to execute the implicit-procedure block *after* the library file has finished and `currentfile` refers to the client program file.

More details (and the code itself) are in the `G` source file itself.

# History

Previously "released" to usenet.
https://groups.google.com/d/topic/comp.lang.postscript/3gaExFSE4ZE/discussion

But its usefulness now has much greater potential with a url and version control and stuff.

The implicit procedure definitions were developed in another thread.
https://groups.google.com/d/topic/comp.lang.postscript/FsTRotu4RaU/discussion

The abbreviated system names code was developed in an earlier thread.
https://groups.google.com/d/topic/comp.lang.postscript/jDG3PHIqoCk/discussion

The idea for making a library for golfing was developed in this still earlier thread.
https://groups.google.com/d/topic/comp.lang.postscript/81Rlq5HeaNg/discussion

An earlier thread about golfing.
https://groups.google.com/d/topic/comp.lang.postscript/q9jkuEkEiQo/discussion

Earlier golfing the Sierpinski Triangle (with thomasW).
https://groups.google.com/d/topic/comp.lang.postscript/tIkud9Ug0Vc/discussion

Earlier thread about Lindenmayer systems and Line Fractals.
https://groups.google.com/d/topic/comp.lang.postscript/5xKJBYOhmP4/discussion

Dang! I found one more, before all the others.
https://groups.google.com/d/topic/comp.lang.postscript/5ivdnXta_Bc/discussion

An old idea.
https://groups.google.com/d/topic/comp.lang.postscript/0tW8JTt451Q/discussion

The seeds of the idea came from my first postscript codegolf. Around revision 5.
http://codegolf.stackexchange.com/revisions/3877/5

At revision 7, I added the working version with comment-key. The program works by re-using tokens from the main procedure by using strings of chars as indices. So the main procedure does double-duty as code-to-be-executed and storage-bank-of-names-and-numbers.
http://codegolf.stackexchange.com/revisions/3877/7

But as later revisions show, ultimately accessing operators with strings of numbers yields far greater gains.
