# parsHMMER
### A python module for bioinformatics

#### Description

parsHMMER is essentially a class specificically designed to easily parse the output generated by [HMMER][1].

**This is an ongoing side project**.

parsHMMER is an alternative to the parser included in [Biopython][2]. I just started developing this class in order to have a more readable way of dealing with HMMER output. Additional feature will be added when required.

#### Dependencies :
* python v.3
* json python module

#### Feature :
* `parsHMMER.parse()` : parse the output file from HMMER once instanciated a parser object
* `parsHMMER.best()` : Return the best matched target.
* `parsHMMER.printHMMER()` : print the output of HMMER in json format.

**(!)** parsHMMER have been tested on output generated by `hmmscan` command from the HMMER suite v.3.2.1. Compatibility with previous version and output generated from other commands will be added in future if required.

**(!)** Command to generated compatible output :
~~~
hmmscan -o <output_file> --domtblout <output_domt_file> <HMM_Database> <input_file>
~~~

#### Example :
~~~python
from parsHMMER import parsHMMER
input_file = 'path/to/file'

# Instantiate the parser object providing the path of the input file
instance = parsHMMER(input_file)

# Parse the file and return a dictionary containing informations
extracted_output = instance.parse()

# Return a tuple with best match information from the parsed output
best_match = instance.best()

# Print to screen extracted data in json format
instance.printHMMER()
~~~

#### Contacts and more :

Feel free to use parsHMMER if needed.

If you are interested in using parsHMMER but the parsing method for your problem hasn't been implemented yet, please, contact me.

For problems, doubts and error please, contact me

contact : davide.baldazzi8@unibo.it



[1]:http://hmmer.org
[2]:https://biopython.org