# README.lexicon:

This file details how to properly construct a lexicon file so that it can be read by DiaSym.
 
The file should be a tab delimited value file with the extension .tsv.

# THE ROWS

Each row should represent the development, over the different diachronic stages, of an etymon, with each stage being indicated by a column.


# COMMENTING

Any and all comments can only be placed in the final column and must be flagged with a "$". Typically they are used to cite the phonological forms and etymology of a word. For example, from our demonstration simulation for Classical Latin going to French: 

```
s ˌɑ ɡ m ˈɑː r i u m	s ɔ m j e $sommier. Pope s674.
```

# THE COLUMNS

Each column represents a different diachronic stage. 
If any form is given for a particular diachronic stage, a form must be given for every etymon at that stage.
In future versions of DiaSim, it will be possible to indicate that an etymon has either fallen out of use or entered the vocabulary late by specifying "..." for stages where it is not present in the lexicon -- however, this feature is not supported by the current release of DiaSim. 

The first column, the only required one, must contain the initial forms for each etymon at the beginning of the diachronic simulation. 
Specifically, in the case of our French demonstration set, this is the Classical Latin form. 
When and if other columns are specified, they should contain the phonological forms each etymon has at the stage corresponding to the column.
The forms entered in these columns will be the gold standard phonological forms to which the forms obtained by the diachronic simulation at those stages will be compared. 
In order for simulation results at any point to be compared to a gold set, that set must be associated with a stage in the rules file and a column in the lexicon file, with its gold forms for each etymon in the lexicon file. 
Without exception, each column specified must uniquely correspond to a diachronic stage that is declared in the rules file (see rules.README.txt -- a stage should be on a line declared immediately after the last rule that applied to its forms). In the rules file, a proper diachronic stage that will be compared to gold must be flagged with a '~' character, as demonstrated below: 
```
~Middle French
```
Stages where the forms of etyma are just to be recorded, not compared, are instead flagged with a "=" character.

DiaSim will automatically associate stages in the rules file, in the order they are declared, to columns other than the input column, from left to right. 
If there is exactly one more column in use after all declared stages are associated with columns to its left, then the system will assume that this is the specification of the final output.
If there are still columns to the right of this final column, then DiaSim will throw an error. 
Likewise, if there are too few columns so that not every stage declared in the rules file is associated with a column, then DiaSim will also throw an error. 

Here is a sample row, showing the diachronic trajectory of Classical Latin *sagmarium* into French *sommier*, via Popular Latin, Old French, Later Old French, Middle French and Modern French. 

```
s ˌɑ ɡ m ˈɑː r i u m	s ˌɑ w m ˈɑ r ʝ o	s ˌo m ˈi ɛ̯ r	s ˌũ m j ˈe r	s ˌũ m j ˈe	s ɔ m j e $sommier. Pope 674. 	
```

Any questions or requests for clarification on how to use this system can be emailed to: diachronic.simulation@gmail.com
