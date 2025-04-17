### Fetch data in 5 row
```bash
proc SQLCHECK=SEMANTICS iname=dyn4.pc userid=hr/password@ORCLPDB1 INCLUDE=$ORACLE_HOME/rdbms/public
gcc -o dyn4 dyn4.c -L$ORACLE_HOME/lib -I$ORACLE_HOME/precomp/public -I/opt/oracle/product/19c/dbhome_1/rdbms/public -lclntsh -lpthread -ldl -lm
```