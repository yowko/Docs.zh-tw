---
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 4055d56d878b817fe88bb0dacb53ea39061bc4b2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249866"
---
# <a name="-not-entity-sql"></a>! (NOT) (Entity SQL)
執行 `Boolean` 運算式的否定運算。  
  
## <a name="syntax"></a>語法  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a>引數  
 `boolean_expression`  
 傳回布林值的任何有效運算式。  
  
## <a name="remarks"></a>備註  
 驚嘆號 (!) 的功能與 NOT 運算子相同。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 NOT 運算子執行 `Boolean` 運算式的否定運算。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
