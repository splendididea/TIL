# 핸드폰 번호에 - 입력 
DB 작업 동기화 중 핸드폰 번호를 입력해야 하는 곳에 번호만 가져와서 담겨 에러가 발생한적이 있다. 

01022223333 -> 010-2222-3333 으로 바꿔야 한다. 


```sql

DELIMITER $$
DROP PROCEDURE IF EXISTS UPDATE_MOBILE_NUMBER$$
  CREATE PROCEDURE UPDATE_MOBILE_NUMBER()
  BEGIN
  DECLARE p_psn_id varchar(30);
  DECLARE l_mobile_number VARCHAR(30);
  DECLARE rowcnt INT;
  DECLARE EXIT HANDLER FOR SQLEXCEPTION
  BEGIN
  ROLLBACK;
  SELECT -1; 
  END;
  
  set p_psn_id = (select psn_id from org_person WHERE mobile NOT LIKE '%-%' AND mobile != '' AND mobile != 'false' order by mobile limit 1 );
  select p_psn_id;
  set l_mobile_number = (select CONCAT(LEFT(MOBILE,3),'-',SUBSTRING(MOBILE,3,4),'-',RIGHT(MOBILE,4)) from org_person WHERE mobile NOT LIKE '%-%' AND mobile != '' AND mobile != 'false' order by mobile limit 1 );
  select l_mobile_number;
  
  update ORG_PERSON 
  SET  mobile = l_mobile_number 
  WHERE PSN_ID = p_psn_id;
  
 
  SELECT MOBILE FROM ORG_PERSON WHERE PSN_ID = p_psn_id;
  

  END$$
DELIMITER;

```
