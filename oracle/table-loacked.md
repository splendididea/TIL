# Oracle Lock 테이블 확인 

## 락 발생 사용자확인
```sql
SELECT   distinct x.session_id,  a.serial#,
  d.object_name,  a.machine,  a.terminal,  a.program,
  a.logon_time ,  'alter system kill session ''' || a.sid || ',  ' || a.serial# || ''';'
FROM   gv$locked_object x, gv$session a,  dba_objects d
WHERE   x.session_id = a.sid  and  x.object_id = d.object_id
order by logon_time;
```


## 접속 사용자 제거 
```sql
--alter system kill session 'session_id,serial#';
alter system kill session '601,6569';
```
---

## 락걸린 테이블 확인
```sql
SELECT  do.object_name,  do.owner,  do.object_type,  do.owner,
  vo.xidusn,  vo.session_id,  vo.locked_mode
FROM
  v$locked_object vo ,  dba_objects do
WHERE   vo.object_id = do.object_id ;
```

## 해당테이블이 락에 걸렸는지 확인
```sql
SELECT   A.SID,  A.SERIAL#,  B.TYPE,  C.OBJECT_NAME
FROM   V$SESSION A,  V$LOCK B,  DBA_OBJECTS C
WHERE   A.SID=B.SID AND  B.ID1=C.OBJECT_ID
   AND  B.TYPE='TM'  AND  C.OBJECT_NAME IN ('테이블명');
```

## 락발생 사용자와 sql, object 조회
```sql
SELECT   distinct x.session_id,  a.serial#,
  d.object_name,  a.machine,  a.terminal,
  a.program,  b.address,  b.piece,  b.sql_text
FROM  v$locked_object x,  v$session a,  v$sqltext b,  dba_objects d
WHERE  x.session_id = a.sid  and
  x.object_id = d.object_id  and
  a.sql_address = b.address
order by b.address,b.piece;
```

## 현재 접속자의 sql 분석 
```sql
SELECT   distinct a.sid,  a.serial#,
  a.machine,  a.terminal,  a.program,
  b.address,  b.piece,  b.sql_text
FROM   v$session a,  v$sqltext b
WHERE   a.sql_address = b.address
order by a.sid, a.serial#,b.address,b.piece;
```