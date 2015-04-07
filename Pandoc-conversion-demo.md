# Pandoc
Pandoc is an open source text file conversion tool.  We can use it to easily convert our .md files to other formats if, for instance, we want to include it in documentation. 

more details can be found here: http://johnmacfarlane.net/pandoc/


# Convert .md to .docx

Note: these instructions are windows-centric.  Pandoc is supported on Windows, Mac, and Linux, so follow their instructions if these aren't sufficient.

1. download and install pandoc from https://github.com/jgm/pandoc/releases
2. verify installation from cmd with pandoc --version
3. save .md file to computer
4. convert by using the following in a command line
     
     pandoc -s -S [yourMDFile] -o [outputFileName].docx
     
For more conversions, see http://johnmacfarlane.net/pandoc/demos.html
