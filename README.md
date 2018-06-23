Author: Michael McCarrin
email:  mrmccarr@nps.edu


This repository contains all tex files for materials
used in CS3920. The materials are organized into
folders for slides, labs, and tests. Running
"make" from any of these directories will build
all pdfs for all source files in the directory.

The art folder contains all graphics used by any
of the slides, labs or tests.

The source for slides uses the powerdot class,
for consistency with Ben Ari.  The figures.tex 
file was written by Ben Ari and contains
the figures in his textbook, Mathematical
Logic for Computer Science. The mlextra.sty
file is based on Ben Ari's style file but
has been altered to include more shortcuts
that I found useful.

The source for labs and tests uses the MIT
exam class. This class supports the option
to print with or without answers using the
\noprintanswers or \printanswers commands.
I have left \noprintanswers as the default.

