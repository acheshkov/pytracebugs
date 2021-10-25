# The PyTraceBugs dataset for software defect prediction

## Dataset description

The dataset contains Python source code collected from public Github repositories (with proper licensing, e.g. Apache, MIT, BSD etc) at the granularity of functions and methods (snippets).
It is aimed at training and evaluating machine learning models for predicting low level bugs in Python source code,
manifested by specific error reports, called traceback reports. Each piece of code in the dataset has its own labeling into either correct or buggy.
Correct snippets are taken from stable codebase of public Github repositories. Buggy pieces are extracted from bugfix commits and pull requests,
linked to Github issues marked by standard labels, used to report bugs in repositories codebase. 

The dataset contains two parts. The first part named `buggy_dataset` contains pieces of
code with bugs whereas the second one called `stable_dataset` is composed of snippets of stable code.
Both these parts of the PyTraceBugs dataset are composed of training, validation and test sets 
to be used to maintain common machine learning workflow.


## Description of buggy dataset

The buggy dataset includes three pickle-files, containing buggy snippets from training, validation and test sets as well as 
a folder with source code of all its snippets. Each training or validation pickle-file contains a pandas dataframe with the following columns:
* `before_merge` - implementation of a snippet, containing a bug;
* `after_merge` - implementation of a snippet, being an immediate fix of bugs in the corresponding snippet in the column `before_merge`;
* `filename` - filename where buggy and its corresponding fixed snippets reside;
* `full_file_code_before_merge` - source code of the module, containing the buggy snippet;
* `full_file_code_after_merge` - source code of the module, containing the fixed snippet;
* `function_name` - a complete function/method name;
* `url` - issue url, where bugs are reported in the buggy snippet;
* `source code and errors` - contains parsed source code and error messages from the issue report; 
* `full_traceback` - complete traceback report;
* `traceback_type` - exception type in the traceback report;
* `before_merge_without_docstrings` - implementation of the buggy snippet without its comments and docstrings;
* `after_merge_without_docstrings` - implementation of the fixed snippet without its comments and docstrings;
* `before_merge_docstrings` - docstrings in the buggy snippet;
* `after_merge_docstrings` - docstrings in the fixed snippet;
* `path_to_snippet_before_merge` - path to the file with source code of the buggy snippet; 
* `path_to_snippet_after_merge` - path to the file with source code of the fixed snippet.

Its test pickle-file contains a table with the following columns:
* `before_merge` - as above;
* `after_merge` - as above; 
* `url` - as above 
* `bug type` - a type of a bug ib the snippet according to the known classification of bugs from https://cwe.mitre.org/ 
* `bug description` - textual description of the bug;
* `bug filename` - a filename where the buggy snippet resides;
* `bug function_name` - a complete function/method name;
* `bug lines` - lines ranges in the snippet source code where the bug is supposed to be located;
* `full_traceback` - as above;
* `traceback_type` - as above;
* `path_to_snippet_before_merge` - as above;
* `path_to_snippet_after_merge` - as above.

## Description of correct dataset

The correct dataset is similarly structured. In distinction to the buggy dataset, source code of the modules, containing snippets, is located
in a separate folder.

The dataset tables have the following columns:
* `before_merge` - implementation of a snippet without bugs, a stable snippet;
* `repo_name` - the repository name with owner where the snippet resides;
* `filename` - as above; 
* `function_name` - as above;
* `path_to_source_file` - path to the file with source code of the module where the snippet is located; 
* `commit` - the last commit where the snippet was changed; 
* `path_to_snippet_before_merge` - path to the file with source code of the snippet.


