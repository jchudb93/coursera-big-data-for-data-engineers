#File Content Exploration

#### cat

concatente files

#### head
Print the first lines of files

head -x file.txt

#### tail

Print the first lines of files

tail -n axv.txt

#### more/less

Output file content by screens

#### wc

Word count

#### grep

Find any lines matching with pattern

#### cut 

cut -f " " -f file

Example show first five columns of a file

cut -d ' ' -f5 input.txt
#### tr

Translate characters

tr ' ' '.' changes spaces for dots

Example 1: cat multilined_file.txt | tr ' ' '.', this replaces spaces for . in all file

Example 2: cat multilined_file | tr -d ' ', deletes all spaces in file

#### sort
xample 2: cat multilined_file | tr -d ' ', deletes all spaces in file

#### awk

#### TODO

#### > and >>

> overrides
>> appends

#### pipe |
