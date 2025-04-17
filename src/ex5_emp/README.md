###

```bash
# Copy into docker
docker cp f:\temp_study\oracle\employees.pc oracle-db:/home/oracle/source
# Build .pc
proc iname=employees.pc
# Build .c
gcc -o sample sample.c -L$ORACLE_HOME/lib -I$ORACLE_HOME/precomp/public -lclntsh -lpthread -ldl -lm
```
