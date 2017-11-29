---
title: ORDER BY (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b805d4437ffd8d3d56a7cdc599bdda797a763d13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="order-by-entity-sql"></a>ORDER BY (Entity SQL)
指定 SELECT 陳述式所傳回物件使用的排序順序。  
  
## <a name="syntax"></a>語法  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a>引數  
 `order_by_expression`  
 任何指定要排序之屬性的有效查詢運算式。 可以指定多個排序運算式。 ORDER BY 子句中排序運算式的順序會定義排序結果集的組織方式。  
  
 COLLATE {collation_name}  
 指定 ORDER BY 運算要依照 `collation_name`中指定的定序執行。 COLLATE 只適用於字串運算式。  
  
 ASC  
 指定特定屬性中的值要以遞增順序 (從最低值到最高值) 排序。 這是預設值。  
  
 DESC  
 指定特定屬性中的值要以遞減順序 (從最高值到最低值) 排序。  
  
 LIMIT `n`  
 只選取前 `n` 個項目。  
  
 SKIP `n`  
 略過前 `n` 個項目。  
  
## <a name="remarks"></a>備註  
 ORDER BY 子句會以邏輯方式套用到 SELECT 子句的結果。 ORDER BY 子句可以利用項目的別名參考選取清單中的項目。 ORDER BY 子句也可以參考目前在範圍內的其他變數。 但是，如果已經配合 DISTINCT 修飾詞指定了 SELECT 子句，那麼 ORDER BY 子句就只能參考來自 SELECT 子句的別名。  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 ORDER BY 子句中的每個運算式都必評估為可以比較排序是否不相等 (小於或大於等) 的型別。 這些型別通常是純量基本型別，例如數值、字串和日期。 屬於可比較型別的 RowTypes 也可以比較排序。  
  
 如果程式碼要在最上層投影以外的排序集上重複執行，輸出不一定會保持原排序。  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 如需排序的 UNION、UNION ALL、EXCEPT 或 INTERSECT 運算，請使用下列模式：  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>限制關鍵字  
 使用於 `ORDER BY` 子句時，下列關鍵字必須括在引號內：  
  
-   CROSS  
  
-   FULL  
  
-   KEY  
  
-   LEFT  
  
-   ORDER  
  
-   OUTER  
  
-   RIGHT  
  
-   ROW  
  
-   VALUE  
  
## <a name="ordering-nested-queries"></a>排序巢狀查詢  
 在 Entity Framework 中，巢狀運算式可放在查詢中的任何地方；巢狀查詢的順序並不會保留。  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>範例  
 以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 ORDER BY 運算子指定 SELECT 陳述式所傳回物件使用的排序順序。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>另請參閱  
 [查詢運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [略過](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [限制](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
