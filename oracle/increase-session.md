# 오라클 세션 늘리기 

오라클 세션 파라미터 processes 변경 

## Process 수 확인
```sql
SHOW PARAMETER PROCESSES;
```
![Image of Parameters of Oracle Sessions](../img/oracle_alter_processes.JPG)

## Proccess 수 변경
```sql
ALTER SYSTEM SET processes = 600 scope=spfile;
```

이후에 DB를 다시 시작하면 반영이 된다. 