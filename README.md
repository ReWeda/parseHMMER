# parsHMMER
### A python module for bioinformatics

#### Description

parsHMMER is essentially a class specifically designed to easily parse the output generated by [HMMER][1].

**This is an ongoing side project**.

parsHMMER is an alternative to the parser included in [Biopython][2]. I just started developing this class in order to have a more readable way of dealing with HMMER output. Additional feature will be added when required.

#### Dependencies :
* python v.3
* json

#### Feature :
*Given :*
`instance = parsHMMER('file_path')`
* `instance.parse()` : parse the output file from HMMER once instanciated a parser object
* `instance.best()` : Return the best matched target.
    
    Arguments :
    * `verbose` :  return more information for the best match. ( *Optional*; Default : `False`)
    * `top` : return the first *N* best matches. ( *Optional*; Default : `1`)
* `instance.printHMMER()` : print the output of HMMER in json format.
* `parsHMMER.writeHMMER(output_file, content)` : write a dictionary or array of dictionaries (list) from parsHMMER to file.
    
    Arguments :
    * `output_file` : path to the file where output is written
    * `content` : dictionary or array of dictionaries (list) from parsHMMER
    * `label_list` : list of labels to discriminated written output from different dictionaries given an array of them is provided ( *Optional*; Default : `[]` )

**(!)** parsHMMER have been tested on output generated by `hmmscan` command from the HMMER suite v.3.2.1. Compatibility with previous version and output generated from other commands will be added in future if required.

**(!)** Command to generated compatible output :
~~~
hmmscan -o <output_file> --domtblout <output_domt_file> <HMM_Database> <input_file>
~~~

#### Example :
~~~python
from parsHMMER import parsHMMER
input_file = 'path/to/input/file'
input_file_2 = 'path/to/input/file/2'
output_file = 'path/to/output/file'

# Instantiate the parser object providing the path of the input file
instance = parsHMMER(input_file)

# Parse the file and return a dictionary containing informations
extracted_output = instance.parse()

# Return a tuple in a list with best match information from the parsed output
best_match = instance.best()

# Return a list of tuples with the N best match information from the parsed output
best_match_5 = instance.best(top=5)

# Print to screen extracted data in json format
instance.printHMMER()

# Print to an output file extracted results
parsHMMER.writeHMMER(output_file, extracted_output)

# Extract results from a second file and print everything to an output file with custom labels
instance2 = parsHMMER(input_file_2)
extracted_output2 = instance2.parse()
parsHMMER.writeHMMER(output_file, [extracted_output, extracted_output2], label_list=['out1', 'out2'])
~~~

#### Written Output :
Description coming soon...

#### Contacts and more :

Feel free to use parsHMMER if needed.

If you are interested in using parsHMMER but the parsing method for your problem hasn't been implemented yet, please, contact me.

For problems, doubts and error please, contact me

contact : davide.baldazzi8@unibo.it



[1]:http://hmmer.org
[2]:https://biopython.org