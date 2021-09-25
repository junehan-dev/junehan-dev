Moving Around in a Hurry
========================

You will not use vi just to create new files.
you want to get to a specific place in a file and start working.

All edits start with you moving the cursor to where you want to begin the edit (or, with ``ex`` line editor commands, by identifying the line numbers to be edited). There are many ways to move in vi, since editing speed depends on getting to your destination with only a fewstrokes.

The Chapter covers:
   - Movement by screens
   - Movement by text blocks
   - Movement by searches for patterns
   - Movement by line number

Movement by Screens
-------------------
   When you read a book, you think of "places" in the book in terms of pages: the page where you stpped reading or the page number in an index. you don't have this convenience when you're editing files.
   You can think of a file as text on a long roll of paper. The screen is a window of 24 lines of text on that long roll.

*Scrolling*
   In insert mode, as you fill up the screen with text, you will end yp typing on the bottom line of the screen. When you reach teh end and press ENTER, the top line rolls out of signe, and a blank line appears on the bottom of the screen for new text.
   This is called *scrolling.*

   In command mode, you can move through a file to see any text in it by scrolling the screen agead or back. And since cursor movements can be multiplied by numeric prefixes, you can move quickly to anywhere in your file.

Scrolling the Screen
--------------------
   There are *vi* commands to scroll forward and backward through the file by full and half screens

   - ``^F``
      **Forward** scroll one screen.
   - ``^B``
      **Backward** scroll one screen.
   - ``^D``
      **Down** half forward screen.
   - ``^U``
      **Up** half backward screen.

Repsopositioning the Screen with ``z``
--------------------------------------
   If you want to scroll the screen up or down, but you want the **cursor to remain on the line where you left it,** use the ``z`` command.

   - ``zENTER``
      Move current line to top of screen and scroll.
   - ``z.``
      Move current line to center of screen and scroll.
   - ``z-``
      Move current line to bottom of sreen and scroll.

   With the ``z`` command, using a numeric prefix as a multiplier makes no sense.(moving cursor to same place multiple times?)
   Instead, ``z`` understands a numeric prefix as a line number that it will use in place of the current line.

Redrawing the Screen
--------------------
   Sometime while you're editing, messages from your computer system will display on your screen.
   These messages don't become part of your editing buffer, but ther do interfere with your work.
   When system messages appear on your screen, you need to redisplay, or redraw, the screen.

   Whenever you scroll, you redraw part of the screen, so you can always get rid of unwanted messages by scrolling them off the screen and then returning to your previous position.
   But you can redraw the screen without scrolling, by typing ``^L``

Movement by Text Blocks
-----------------------
   Another way that you can think of moving though *vi* file is by text blocks(words, sentences, paragraphs, or sections).
   You have already learned to move forward and backward by word *(w, W, b, B).*
   In addition, you can use these commands:

   - ``e``
      Move to end of word.
   - ``E`` 
      Move to end of word(ignore punctuation).
   - ``(``
      Move to beginning of current sentence.
   - ``)``
      Move to beginning of next sentence.
   - ``{``
      Move to beginning of current paragraph.
   - ``}``
      Move to beginning of next paragraph.
   - ``[[``
      Move to beginning of current section.
   - ``]]``
      Move to beginning of next section.

Sentence
^^^^^^^^
   To find the end of a sentence, *vi* looks for one of these punctuation marks: *?,.,!*
   *vi* locates the end of a sentence when the punctuation is followed by at least two spaces or when it appears as the last nonblank character on a line. If you have left only a single space following a period, or if the sentence ends with a quotation mark, *vi* won't recognize the sentence.

Paragraph
^^^^^^^^^
   A Pragraph is defined as text up to the next blank line, or up to one of the default paragraph macros(.IP, .PP, .LP, or .QP) from the *troff MS* macro package. similarly, a section is defined as text up to next default section macro (.NH, .SH, .H 1, or .HU).
   The macros that are recognized as paragraph or section separators can be customized with the ``:set`` command, as decribed in Chapter 7.

Movement by Searches
--------------------
   One of the most useful ways to move around quickly in a large file is by searching for text, or more properly, a *pattern* of characters.
   Sometimes a search can be performed to find a misspelled word or to fine each occurence of a variable in a program.

   The Search command is the special character */* (slash). When you enter a slash, it appears on the bottom line of the screen;
      you then type in the *pattern* that you want to find: ``:/pattern``
   A pattern can be a whole word or any other sequence of characters (called a "character string").

   *vi,* like all other Unix editors, has a special pattern-matching language that allows you to look for variable text patterns.
   We'll talk about this more powerful pattern-matching syntax in Chapter 6.

   *vi* begins the search at the cursor and searches forward, wrapping around to the start of the file if necessary.
   To search backward, type ``?`` instead of a ``/`` .

Repeating Searches
------------------
