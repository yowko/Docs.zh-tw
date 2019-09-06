---
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: c64e440e8cd8f86706db69d923ba7085d0cb3b3a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248984"
---
# <a name="then-entity-sql"></a>THEN (Entity SQL)
當 WHEN 子句評估為 `true`時，該子句的結果。  
  
## <a name="syntax"></a>語法  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>引數  
 `when_expression`  
 任何有效的 Boolean 運算式。  
  
 `then_expression`  
 傳回集合的任何有效查詢運算式。  
  
## <a name="remarks"></a>備註  
 如果 `when_expression` 評估為 `true`值，結果就是對應的 `then-expression`。 如果沒有滿足任何 WHEN 條件，就會評估 `else-expression` 。 不過，如果沒有任何 `else-expression`，結果就是 null。  
  
 如需範例，請參閱[案例](case-entity-sql.md)。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 CASE 運算式來評估一組 `Boolean` 運算式。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 PrimitiveType 結果](../how-to-execute-a-query-that-returns-primitivetype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>另請參閱

- [CASE](case-entity-sql.md)
- [Entity SQL 參考](entity-sql-reference.md)
