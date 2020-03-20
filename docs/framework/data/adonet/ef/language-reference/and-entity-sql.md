---
title: '&amp;&amp;（和）（實體 SQL）'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eccad616de287a39c42e986cea84dc22feec7f70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150504"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp;（和）（實體 SQL）
如果兩個運算式都是 `true` 則傳回 `true`，否則為 `false` 或 `NULL`。  
  
## <a name="syntax"></a>語法  
  
```csharp  
boolean_expression AND boolean_expression
```

或  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>引數  
 `boolean_expression`  
 傳回布林值的任何有效運算式。  
  
## <a name="remarks"></a>備註  
 雙連字號 (&&) 的功能與 AND 運算子相同。  
  
 下表顯示可能的輸入值和傳回型別。  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|FALSE|NULL|  
|`FALSE`|FALSE|FALSE|FALSE|  
|`NULL`|NULL|FALSE|NULL|  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會示範如何使用 AND 運算子。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
