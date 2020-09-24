---
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: f038f242bc0873df3d72700aa05fca2f76f777ff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161668"
---
# <a name="then-entity-sql"></a>THEN (Entity SQL)

當 WHEN 子句評估為 `true`時，該子句的結果。  
  
## <a name="syntax"></a>語法  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>引數  

 `when_expression`  
 任何有效的 Boolean 運算式。  
  
 `then_expression`  
 傳回集合的任何有效查詢運算式。  
  
## <a name="remarks"></a>備註  

 如果 `when_expression` 評估為 `true`值，結果就是對應的 `then-expression`。 如果沒有滿足任何 WHEN 條件，就會評估 `else-expression` 。 不過，如果沒有任何 `else-expression`，結果就是 null。  
  
 如需範例，請參閱 [大小寫](case-entity-sql.md)。  
  
## <a name="example"></a>範例  

 下列 Entity SQL 查詢會使用 CASE 運算式來評估一組 `Boolean` 運算式。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 依照 how [to：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式操作。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a>另請參閱

- [CASE](case-entity-sql.md)
- [Entity SQL 參考](entity-sql-reference.md)
