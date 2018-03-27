# 몽고DB where 사용하여 업데이트 처리하기 

기존의 RDBMS에서 update를 할때는 where절에 조건을 주어서 만족하는 조건의 경우만 update를 쳤다. 

```sql
update users
   set name = 'anonymous'
 where name is null
```

마찬가지로 mognodb 역시 where절을 줄 수 있다. 
```javascript
db.getCollection('users').update({'pushAlarm': {$exists: false}}, {$set: {"pushAlarm" : {
        "note" : [ 
            "jay"
        ]
    }}} , { "multi": true })
```