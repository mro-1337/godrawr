===============================================================================
 Illusion/X BBS                                                GODRAWR.TXT
 godrawr - the ANSI drawing program, on its own
===============================================================================

 Contents
   1. What it is
   2. Starting it
   3. Files: Open, Save, Save As
   4. Sixels: exporting, the viewer, importing pictures
   5. Drawing
   6. Switches
   7. Building it from the source

-------------------------------------------------------------------------------
 1. WHAT IT IS
-------------------------------------------------------------------------------

   godrawr is the BBS's ANSI editor (Sysop -> ANSI editor on the web) as a
   program of its own, for drawing on your own computer: Windows
   (godrawr.exe) or Linux (godrawr).  It needs no BBS.  It opens in a
   window of its own (Edge, Chrome or Chromium without an address bar);
   it ends when you close the window.

   It draws 80-column ANSI screens of VGA characters, in the spirit of
   Moebius and PabloDraw, in the 16 PC colours or true colour, and works
   with sixel pictures.

-------------------------------------------------------------------------------
 2. STARTING IT
-------------------------------------------------------------------------------

   Double-click godrawr.exe (Windows), or run ./godrawr (Linux).  To open
   a file at once:
          godrawr MAIN.ANS
   On Windows, a screen can be opened with godrawr: right-click a .ANS ->
   Open with -> Choose another app -> godrawr.exe.

   It remembers the last folder you used (in godrawr\godrawr.json of your
   settings folder: %AppData% on Windows, ~/.config on Linux).

   Without Edge, Chrome or Chromium it opens in your usual browser.  It
   only answers this computer (127.0.0.1), and only its own window (a
   secret in its address).

-------------------------------------------------------------------------------
 3. FILES: OPEN, SAVE, SAVE AS
-------------------------------------------------------------------------------

   Open... (Ctrl+O) shows a file dialog:
     Up / the folder line / Places    move between folders and drives (type
                  a folder in the folder line and press Enter)
     Search       finds files as you type: part of the name, or * and ?
                  (*.ANS); "in subfolders" searches the folders below too
     the list     Name, Type, Size, Modified (click a heading to sort);
                  a click shows the file in the preview; a double-click
                  (or Enter, or Open) opens it; folders open with a
                  double-click; Backspace goes up
     the kinds    screens and pictures, ANSI screens, pipe codes, sixels,
                  pictures, or all files
   A file dropped on the drawing opens too.

   Save (Ctrl+S) saves the file again.  Save As... (Ctrl+Shift+S) picks
   the folder, the name and the kind:
          .ANS     16 colours (true colours become the nearest of the 16)
          .ANSI    high colour (NAME.ANSI1 ... NAME.ANSI9: the BBS's random
                   variants)
          .ASC     pipe colour codes (|00-|23)
          .SIXEL   a picture of the drawing
   Typing the extension picks the kind (MAIN.ANSI3).  A file that's there
   already is replaced only when you say so.

   The window's title shows the file; * means changes not saved yet
   (closing the window asks first).

-------------------------------------------------------------------------------
 4. SIXELS: EXPORTING, THE VIEWER, IMPORTING PICTURES
-------------------------------------------------------------------------------

   Export Sixel... saves a picture of the drawing as a sixel (NAME.SIXEL):
          Sixel, BBS size    at most 640x400 pixels (what the BBS shows
                             callers; -sixel changes it): a taller drawing
                             is shrunk to fit
          Sixel, full size   as drawn, 8x16 pixels a character cell
   (Save As... with the .SIXEL kind is the same, at the BBS size.)

   Sixel Viewer... opens a .SIXEL (or a PNG, GIF or JPEG) and shows it:
   Fit or 1x-4x zoom, its size and colours.  Opening a .SIXEL with Open...
   shows it there too.  In the viewer:
     Import as a New Screen   the picture becomes the drawing, in half-
                  blocks (two pixels a character cell)
     Paste into the Drawing   then click where it goes
     columns      how wide (80, 64, 40, 32 or 20 columns)
     colours      the 16 colours dithered (smooth), the 16 colours flat,
                  or true colour (save it as .ANSI)
     Save as .SIXEL...        a PNG, GIF or JPEG saved as a sixel
   Import Picture... is the same, starting from the file dialog.

   Pictures are saved as sixels at most 640x400 pixels (the BBS's
   default; -sixel changes it): bigger ones are shrunk to fit.

-------------------------------------------------------------------------------
 5. DRAWING
-------------------------------------------------------------------------------

   The same as the BBS's ANSI editor (SCREENS.TXT section 13): the
   keyboard with the F1-F10 character sets, the brush, half-blocks,
   shading, colourizing, lines, rectangles, fill, erase, pick, select /
   copy / cut / paste / move, undo and redo; rows (up to 1000), zoom,
   clear screen first, iCE colours.  Help at the bottom of the window.

-------------------------------------------------------------------------------
 6. SWITCHES
-------------------------------------------------------------------------------

   godrawr [switches] [FILE]
     -sixel WxH   the BBS-size sixels' largest size (default 640x400)
     -port N      its local port (default: any free one)
     -nowindow    no window: it prints its address to open in a browser,
                  and runs until Ctrl-C
     -version     its version

-------------------------------------------------------------------------------
 7. BUILDING IT FROM THE SOURCE
-------------------------------------------------------------------------------

   godrawr-source (a zip and a .tar.gz) is its complete source, a Go
   module of its own; Go 1.21 or newer, nothing to download:
          Windows:  build.bat          -> godrawr.exe
          Linux:    make               -> godrawr
                    make windows       -> godrawr.exe
   It's also in the BBS's source (cmd/godrawr, internal/ansiedit, which
   the BBS's web ANSI editor uses too).

===============================================================================
