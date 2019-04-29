---
title: CASE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: e44f48d040fc77bf702759be0c53a618cd84f9fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607189"
---
# <a name="case-entity-sql"></a>CASE (Entity SQL)
評估一組 `Boolean` 運算式，以便判斷結果。  
  
## <a name="syntax"></a>語法  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a>引數  
 `n`  
 這是一個預留位置，表示可以使用多個 WHEN `Boolean_expression` THEN `result_expression` 子句。  
  
 THEN `result_expression`  
 是在 `Boolean_expression` 評估為 `true`時傳回的運算式。 `result expression` 是任何有效的運算式。  
  
 ELSE `else_result_expression`  
 這是沒有任何比較作業評估為 `true`時，所傳回的運算式。 如果省略這個引數，而且沒有比較作業評估為 `true`，CASE 便傳回 null。 `else_result_expression` 是任何有效的運算式。 `else_result_expression` 和任何 `result_expression` 的資料型別都必須相同，或必須為隱含轉換。  
  
 WHEN `Boolean_expression`  
 這是使用搜尋的 CASE 格式時所評估的 `Boolean` 運算式。 `Boolean_expression` 是任何有效的 `Boolean` 運算式。  
  
## <a name="return-value"></a>傳回值  
 從 `result_expression` 和選擇性 `else_result_expression`的型別集中，傳回優先順序最高的型別。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] CASE 運算式與 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CASE 運算式很相似。 您可以使用 CASE 運算式來進行一連串條件式測試，以便判斷哪一個運算式會產生適當的結果。 這種 CASE 運算式形式會套用至一個或多個 `Boolean` 運算式，以便判斷正確的結果運算式。  
  
 CASE 函式會按照指定的順序針對每個 WHEN 子句評估 `Boolean_expression` ，然後傳回評估為 `result_expression` 之第一個 `Boolean_expression` 的 `true`。 此時，系統就不會評估其餘運算式。 如果沒有任何 `Boolean_expression` 評估為 `true`，Database Engine 就會傳回 `else_result_expression` (如果指定了 ELSE 子句) 或 null 值 (如果沒有指定任何 ELSE 子句)。  
  
 CASE 陳述式無法傳回多重集 (Multiset)。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 CASE 運算式來評估一組 `Boolean` 運算式，以便判斷結果。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>另請參閱

- [THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)
- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
