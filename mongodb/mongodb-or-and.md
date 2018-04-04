# MongoDB and문 안에 or문 쓰기 
$and 배열안에 $or 객체를 각각 삽입 

> 문법: { $and: [ { expression1 }, { expression2} , ... , {expressionN} ]}

```json
db.inventory.find( {
    $and : [
        {$or: [ {price: 0,99} , {price: 1.99 }]},
        {$or: [ {sale: true }, {qty: {$lt: 20 }}]}
    ]
} )

```
[Mongodb 원문보기 ](https://docs.mongodb.com/manual/reference/operator/query/and/)