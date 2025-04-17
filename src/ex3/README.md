### Retrieve query statements using dynamic queries.

Command.
Copy files to docker.

```bash
docker cp C:\temp_study\Oracle\employees.pc oracle-db:/home/oracle/source
# Building a .pc file
proc iname=employees.pc
# Building .c files
gcc -o employees employees.c -L$ORACLE_HOME/lib -I$ORACLE_HOME/precomp/public -lclntsh -lpthread -ldl -lm
```
