### Desc

This time, let's separate the database connection information into a .example.pc file.
So the file structure is as follows:

example.h
example.pc
main.pc --> Here, we use connect_to_db of example.pc.

### Build

```bash
1. proc iname=example.pc
2. proc iname=main.pc
3. gcc example.c main.c -o main_program -L$ORACLE_HOME/lib -lclntsh -I$ORACLE_HOME/precomp/public
4. ./main_program
```
