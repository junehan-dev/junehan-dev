ch02
====

**Simple Editing**

You can't learn *vi* by memorizing every single *vi* command. Start out by learning the basic commands introduced in this chapter.
Note the patterns of use that the commands have in common.

As you learn *vi,*  be on the lookout for more tasks that you can delegate to the editor, and then find the command that accomplishes it.
In later chapters you will leran more advanced features of vi, but before you can handle the advanced, you must master the simple.

This chapter covers::

   - Moving the cursor
   - Adding and changing text
   - Deleting, moving, and copying text
   - More ways to enter insert mode

*vi* commands
-------------

vi has two modes
   command mode and insert mode.

As soons as you enter a file, you are in command mode, and the editor is waiting for you to enter a commnad.
Commands enable you to move anywhere in the file, to perform edits, or to enter insert mode to add new text.
Commands can also be given to exit the file (saving or ignoring your edits) in order to return to the Unix prompt.

Insert mode
-----------
   There are several ways to tell *vi* that you wnat to begin insert mode.
   One of the mode common is to press ``i.`` The ``i`` doesn't appear on the screen, but after you press it, whatever you type will appear on the screen and will be entered into the buffer.
   The cursor marks the currnet insertion point.
      to tell *vi* that you wnat to stop inserting text, press ``ESC.``
   Pressing ``ESC`` will move the cursor back one space (so that is is on the last character you typed) and returns *vi* to command mode.

   Note that you can't use the backspace key to back up beyond the point where you entered insert mode.
      If you disabled *vi* compatibility, *Vim* allows you to backspace beyond the point where you entered insert mode.

   *vi* has option that lets you define a right margin and provides a carriage return automatically when you reach it.
   For right now, while you are inserting text, press ``ENTER`` to break the lines.

Moving the Cursor
-----------------
   There are *vi* commands to move the cursor.
      - Up, down, left or right - one character at a time
      - Forward or backward by blocks of text such as words, sentence, or parapraphs
      - Forward or backward through a file, one screen at a time.

Single Movements
----------------
   The Key *h, j, k and l* right under your fingertips, will move the cursor:
      - *h*
         Left, one space
      - *j*
         Down, one line
      - *k*
         Up, one line
      - *l*
         Right, one space

   **You can move around without ever taking your fingers off the center of the keyboard.**
   Before you move the cursor, press *ESC* to make sure that you are in command mode.
   When you have gone as far as possible in one direction, you hear a beep and the cursor stops.

Numeric Arguments
-----------------
   You can precede movement commands with numbers.
   ``4l`` moves the cursor four spaces to the right, just as if you had typed ``l`` four times.
   This ability to multiply commands gives you more options and power for each command you learn.
   Keep this in mind as you are introduced to additional commands.

Movement withing a Line
-----------------------
   when you saved the file, *vi* displayed a message telling you how many lines are in that file.
   A line is any text entered between newlines.
   *vi* has an option that allows you to set a dinstance from the right margin at which *vi* will automatically insert a new line character. This option is *wrapmargin* you can set a *wrapmargin* at 10 characters with ``:set wm=10``
      this command doesn't affect lines that you've already typed. We'll talk more about setting options in *chapter 7.*

Movement by text blocks
-----------------------
   To move to a specific line, you can use the *G* command. Plain ``G`` goes the the end of the file, ``1G`` goes the the top of the file, ``42G`` goes to line 42.
   This is described in more detail later in the sction "The G(Go To) command" on page 43.

Simple Edits
------------
   When you enter text in your file, it is rarely perfect. You find typos or want to improve on a phrase;
      *'sometimes your program has a bug.'*
   Once you enter text, you have to be able to change it, delete it, move it, or copy it.

