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

   need typo::

      With a editor you can scrooll the page, move the cursor, delete lines, nisret characters, and more while results of your edits as you make tham.
      Since they allow you to make changes as you read through a file, much as you would edit a printed copy,
      screen editors are very popular.

   typo result::

      With a screen editor you can scroll the page, move the cursor, delete lines, insert characters, and more while results of your edits as you make them.
      Screen editors are very popular since they allow you to make changes as you read through a file, much as you would edit a printed copy.

Appending Text
--------------
``a``
   You can append text at any place in your file with the append command, *a.*
   You may have noticed that when you press ``i`` to enter insert mode,

   - The cursor doesn't move until after you enter some text,**
   - By contrast, when you press ``a`` to enter insert mode, the cursor moves one space to the right.

Changing Text
-------------
``c``
   You can replace any text in your file with the change command, *c.*
   
   - When the change affects only the current line, *vi* marks the end of the text that will be changed with a ``$`` so that you can see what part of the line is affected

General Form of vi commands
^^^^^^^^^^^^^^^^^^^^^^^^^^^
   In the change commands we've mentioned up to this point, you may have noticed the follwing pattern::

      (command)(text object)

   command is the change command ``c`` and the text object is movement command.
   But ``c`` is no the only command that requires a text object.
   The ``d`` command (delete) and the ``y`` (yank) follow this pattern as well.

   Rememeber also that movement commands take numeric arguments, so numbers can be added to the text objects of ``c, d`` and ``y`` commands.
   For example, ``d2w`` and ``2dw`` are commands to delete two words.
   With this in mind, you can see that most *vi* commands follow a general pattern::

      (command)(number)(text object)

   When you realize how many combinations are possible in this way, *vi* becomes a powerful editor indeed!

Problems with deletions
^^^^^^^^^^^^^^^^^^^^^^^
   - You've deleted the wrong text and you want to get it back.
      1. simply type ``u`` to undo the last command.
      2. ``U`` will restore the line to it's pristine state, the way it was before any changes were applied to it.
      3. By ``p`` command, since *vi* saves the last nine deletions in nine numbered deletion buffers. **(Only work for a deleted line)**
         - the third deletion back is the one you want to restore, type: ``"3p`` to *put* the contents of buffer number 3 on the line below the cursor.
     
Moving Text
-----------
   In *vi,* You move text by deleting it and then placing that deleted text elsewhere in the file, like a "cut and paste."
   Each time you delete a text block, that deletion is temporarily saved in a special buffer.

Copying Text
------------
   A yank command copies the selected text into a special buffer, where it is hel until another yank or deletion occurs.
   Yank is most frequently used with a line of text, because to yank and put a word usually takes longer than simply to insert the word.

   - Yanking uses the same buffer as deleting.
   - Each new deletion or yank replaces the previous contents of the yank buffer.

Repeating or Undoing Your Last Command
--------------------------------------
   Each edit command that you give is stored in a temporary buffer until you give the next command.
      For example, if you insert the after a word in your file, the command used to insert the text, along with the text that you entered, is temporarily saved.

Numeric Arguments for Insert commands
-------------------------------------
   Except for ``o`` and ``O``, the insert commands just listed (plus i and a) take numeric prefixes.
   With numeric prefixes, you might use the commands ``i, I, a, A`` to insert a row of underlines or alternating characters.
      For example, typing ``25a*-`` appends 50 characters (25 pairs of asterisk and hyphen).
      It's better to repeat only a small string of characters.

   With a numeric prefix, ``r`` replaces that number of characters with a reapeated instance of a single character.
      For example, in C or Cpp code, to change || to &&, you would place the cursor on the first pipe character and type ``2r&``

