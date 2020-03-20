---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: b3fc2484e80b637ed5841375985f7bae476bbbf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150196"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
判斷查詢運算式是否為 null。  
  
## <a name="syntax"></a>語法  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何有效的查詢運算式。 不可為集合、不可有集合成員，也不可為集合型別屬性的記錄型別。  
  
 NOT  
 否定 IS NULL 的 EDM.Boolean 結果。  
  
## <a name="return-value"></a>傳回值  
 如果 `true` 傳回 null 則為 `expression`；否則為 `false`。  
  
## <a name="remarks"></a>備註  
 使用 `IS NULL` 判斷外部連結的項目是否為 null：  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 使用 `IS NULL` 判斷成員是否有實際值：  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 下表所示為 `IS NULL` 在某些模式上的行為。 所有例外狀況都是在叫用提供者之前從用戶端擲回：  
  
|模式|行為|  
|-------------|--------------|  
|null IS NULL|傳回 `true`。|  
|TREAT (null AS EntityType) IS NULL|傳回 `true`。|  
|TREAT (null AS ComplexType) IS NULL|擲回錯誤。|  
|TREAT (null AS RowType) IS NULL|擲回錯誤。|  
|EntityType IS NULL|傳回 `true` 或 `false`。|  
|ComplexType IS NULL|擲回錯誤。|  
|RowType IS NULL|擲回錯誤。|  
  
## <a name="example"></a>範例  
 以下[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢使用 IS NOT Null 運算子來確定查詢運算式是否為空。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
