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
^^^^^^^^^^^
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

