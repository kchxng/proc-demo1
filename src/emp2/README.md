### Calling pl/sql in Pro\*C and outputting the result to a cursor.

Here we use plsql block.
In other words, it means using plsql in Pro\*C.
So when building, you also need to enter account information.

```bash
proc SQLCHECK=SEMANTICS iname=employees.pc userid=hr/password@ORCLPDB1
# And the include path is also added in gcc compilation.
gcc -o employees employees.c -L$ORACLE_HOME/lib -I$ORACLE_HOME/precomp/public -I/opt/oracle/product/19c/dbhome_1/rdbms/public -lclntsh -lpthread -ldl -lm
```
