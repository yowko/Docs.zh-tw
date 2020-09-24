---
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 89c0a92030f2f067d5e5d45b58d475414a224ce4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150800"
---
# <a name="-or-entity-sql"></a>|| (OR) (Entity SQL)

結合兩個 `Boolean` 運算式。  
  
## <a name="syntax"></a>語法  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>引數  

 `boolean_expression`  
 傳回 `Boolean`的任何有效運算式。  
  
## <a name="return-value"></a>傳回值  

 當其中一個條件為`true` 時就會傳回 `true`，否則會傳回 `false`。  
  
## <a name="remarks"></a>備註  

 OR 是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 邏輯運算子， 它是用來結合兩個條件。 當在陳述式中使用一個以上的邏輯運算子時，OR 運算子會在 AND 運算子之後評估。 然而，您可以使用括號來變更驗算的順序。  
  
 雙分隔號 ( # A2) 具有與 OR 運算子相同的功能。  
  
 下表顯示可能的輸入值和傳回型別。  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|true|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>範例  

 下列 Entity SQL 查詢會使用 OR 運算子結合兩個 `Boolean` 運算式。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
