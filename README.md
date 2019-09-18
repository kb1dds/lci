                    # lci - a LOLCODE interpreter written in C.  Ported to OpenVMS 7.2 for VAX
                    
Beware.  Some of the porting process to VAX has been troublesome.  Main issues:
1. VAX C does not like the `long long` type, since VAX is, reasonably enough a 32-bit architecture
2. `getopt_long` simply doesn't exist!  I've just squashed the command line option handling.
3. `strtof` doesn't exist.  I wrote a hack around this.
4. The VAX is an ASCII machine, for the most part.  It choked on the UNICODE translation code...
5. I squashed all the filenames to 6 characters.  This is not strictly necessary for VAX/VMS, but I had visions (now dashed) of compiling this on a PDP-11.  And RT-11 does not support longer names.

# LICENSE

    Copyright (C) 2010-2014 Justin J. Meza

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

# ABOUT

lci is a LOLCODE interpreter written in C and is designed to be correct,
portable, fast, and precisely documented.

    - correct: Every effort has been made to test lci's conformance to the
          LOLCODE language specification. Unit tests come packaged with the lci
          source code.
    - portable: lci follows the widely ported ANSI C specification allowing it
          to compile on a broad range of systems.
    - fast: Much effort has gone into producing simple and efficient code
          whenever possible to the extent that the above points are not
          compromised.
    - precisely documented: lci uses Doxygen to generate literate code
          documentation, browsable here.

This project's homepage is at http://lolcode.org.  For help, visit
http://groups.google.com/group/lci-general.  To report a bug, go to
http://github.com/justinmeza/lci/issues.

Created and maintained by Justin J. Meza <justin.meza@gmail.com>.
Ported to VAX by Michael Robinson <kb1dds@gmail.com>

# PREREQUISITES

1. You must have a VAX running a recent version of OpenVMS.  I am using OpenVMS VAX 7.2.  SIMH should be fine if you don't have an actual VAX, but then I'm not sure why you are doing this...

2. The VAX C compiler

# INSTALLATION: THERE IS NO EASY WAY ON OPENVMS VAX

1. Compile all of the C files

  $ CC MAIN.C
  
  etc.  Hopefully you can then

  $ LINK MAIN, ERROR, INTERP, LEXER, PARSER, TOKEN, UNICOD
  
  but I wouldn't yet bet on it.

# INSTALLATION: ANOTHER OS

Use the original repo, not this fork...
