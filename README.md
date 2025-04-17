## Proc\*C language

### Structure

```bash
pro_c_app/
|── bin/
|   |── program.o # file.o or file or file.exe
|── include/
|   |── db.h
|── src/
|   |── app.pc
|   |── Makefile
|── README.md
```

### Compile and run

```bash
cd src
make
./app
```

### Study on korea website as `https://blog.allres.co.kr/Board/Detail/1026/ORACLE`

```bash
docker exec -it --user root oracle-db bash
#
yum install gcc
#
proc iname=sample.pc : docker exec -it oracle-db bash
#
gcc -o sample sample.c -L$ORACLE_HOME/lib -I$ORACLE_HOME/precomp/public -lclntsh -lpthread -ldl -lm
# Emp proc
proc iname=employees.pc
#
gcc -o employees employees.c -L$ORACLE_HOME/lib -lclntsh -lpthread -ldl -lm -lclntshcore -lnnz19 -lons
#
./employees
```

- how to Build proc

```bash
1.  proc iname=main.pc
2.  gcc main.c -o main_program -L$ORACLE_HOME/lib -lclntsh -I$ORACLE_HOME/precomp/public
```

### Oracle

```bash
sqlplus
#
sqlplus sys/YourPassword123@ORCLCDB as sysdba
#
SQL> select pdb_name from cdb_pdbs;
```

### After installing oracle, register an account and check database information

Youtube: https://youtu.be/ID6uJlcIzIg

1. Before proceeding, you need to check the basic environment variables.

Check if the Oracle environment variable TNS_ADMIN is set correctly. This variable specifies the location of the tnsnames.ora file.
echo $TNS_ADMIN
If TNS_ADMIN is not set, the default path $ORACLE_HOME/network/admin is used.
If this variable points to the wrong location, correct it:
export TNS_ADMIN=/path/to/your/network/admin

2. Register a new user.
   First, you need to connect to the database as a user with SYSDBA or DBA privileges through a client tool such as SQL\*Plus or SQL Developer.

Input in Windows command: docker exec -it oracle-db bash
sqlplus sys/YourPassword123@ORCLCDB as sysdba
Add user after connecting to sqlplus
CREATE USER new_user IDENTIFIED BY your_password;
If an error occurs here, you should first perform the following steps.
select pdb_name from cdb_pdbs; -- Check pdb information
alter session set container = pdb_name

3. Grant permissions to the user
   A newly created user has no permissions in the database by default. At a minimum, you need to grant the following permissions so that the user can connect to the database and create objects:

CONNECT permission: Allows the user to connect to the database.
RESOURCE permission: Allows the user to create database objects such as tables and indexes.
GRANT CONNECT, RESOURCE TO new_user;
GRANT DBA TO new_user; In my case, I gave dba rights to a new user for the purpose of using it on my PC, but in practice, you should never do this. (Security issue)

4. Check the database name using the V$DATABASE view
   Check the name of the database you are currently connected to

SELECT name FROM v$database;
