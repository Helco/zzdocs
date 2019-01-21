# Global variables

There are two script commands referring global variables (`setGlobal` and `beginIf_global`), but these commands don't occur in any scripts in the database. It seems like this system was once used but later deprecated and remained unused until release.

## Internal workings

The two script commands are implemented in the executable and do set one of 49 variables saved in a special class. They are also saved as end section of every savefile, but the values of the variables stay zero. Every variable has an internal change counter which is initialized to a random value (for reasons unknown) between 0 and 2^16.

It stands to reason that this system was deprecated as numeric variable identifiers are not very user-friendly.
