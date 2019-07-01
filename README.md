# EdPy
Microbric Edison robot using a subset of Python 2. This fork only adds the option of defining a target .wav file (`-t` switch) instead of using random names.

This software is used by the [OpenRoberta Lab](https://github.com/OpenRoberta/openroberta-lab) to create a WAV file from the Python2 code that is created from the blockly blocks. The code can then be uploaded to the Edison robot.

There are three main python programs:
* EdPy.py -- this will take a file of an EdPy Python2 program, and compile, assemble and create a wav file for download
* EdAsm.py -- this tool can be used to assemble an assembler source file. EdPy.py does this and more! It is
  still available for working directly with the [TASM](https://en.wikipedia.org/wiki/Turbo_Assembler) assembler language
* TranStrings.py -- a tool to find all translatable strings and make sure they are used correctly. This will 
  be used when we start the translation effort
  
All of these programs must be run using Python 2.7 or later, but NOT Python 3.0 or later. So it is a Python 2 program,
which uses some Python 2.7 additions but it isn't cleanly Python 3.0. All new code was developed using future statements
to use new print functionality and import functionality so should be easy to go to Python 3. But some code was taken from
EdWare (token assembler bits) so it will need more work.

All of the main Python programs have a 'help' option -- e.g. `python2 EdPy.py --help.`

Examples
--------

To get help:
<pre>
python2 EdPy.py --help
</pre>

To compile a program:
<pre>
python2 EdPy.py en_lang.json SOURCE.py
</pre>

To compile a program to a specific target directory:
<pre>
python2 EdPy.py en_lang.json SOURCE.py -t TARGET.wav
</pre>

To just check a program. This doesn't generate a wav file.
<pre>
python2 EdPy.py -c en_lang.json SOURCE.py
</pre>

Turn on debugging output and get an assembler listing
<pre>
python2 EdPy.py -d 2 -a test.lst en_lang.json SOURCE.py
</pre>