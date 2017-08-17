# C to Single File

Simple script to turn a C project into a single file for online tests submission.

## Usage

All files need to be formatted properly.

There are 5 type of parts that this program reads:

* includes
* macros
* datatypes
* declarations
* definitions

Every part in each file needs to be surrounded by

```c
// start:PARTNAME
// end:PARTNAME
```

For example:

`my_lib.h`

```c
// start:includes
#include <stdlib.h>
// end:includes

// start:macros
#define true 0   // I'm funny
#define false 1  // aren't I?
// end:macros

// start:datatypes
typedef enum _my_enum {
    SINGLE_FILE,
    SUBMISSIONS,
    SUCK
} singlefile_is_cancer_t;
// end:datatypes

// start:declarations
singlefile_is_cancer_t i_really_mean_it();
// end:declarations
```
`my_lib.c`

```c
// start:includes
#include "my_lib.h"
// end:includes

// start:definitions
singlefile_is_cancer_t i_really_mean_it() {
    return SUCK;
}
// end:definitions

```

Will result in:

`$ c2singlefile my_lib.h my_lib.c`
```c
// AUTOMATICALLY GENERATED, DO NOT EDIT
// This file was generated by c2singlefile
// https://github.com/Depaulicious/c2singlefile

// Files included here:
// - my_lib.h
// - my_lib.c

#include <stdlib.h>

// Macros
// From my_lib.h

#define true 0   // I'm funny
#define false 1  // aren't I?

// Datatypes
// From my_lib.h

typedef enum _my_enum {
    SINGLE_FILE,
    SUBMISSIONS,
    SUCK
} singlefile_is_cancer_t;

// Declarations
// From my_lib.h

singlefile_is_cancer_t i_really_mean_it();

// Definitions
// From my_lib.c

singlefile_is_cancer_t i_really_mean_it() {
    return SUCK;
}
```

Everything between `start` and `end` comments will be kept as it is, except for includes.

Only `#include <*>` will be kept, and multiple occurrences of the same include statement are only repeated once.

## Syntax

Simply pass the program a list of files, starting from the least important, dependency-wise. The output will follow the same order.

## Installation

```shell
pip install https://github.com/Depaulicious/c2singlefile/archive/master.zip
```