---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: c0f7686f7ff3f6458637b51e29ecafe0c0ccfbc4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040316"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
從多重值集合中擷取元素。  
  
## <a name="syntax"></a>語法  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 傳回可從中擷取元素之集合的任何有效查詢運算式。  
  
## <a name="return-value"></a>傳回值  
 如果集合具有多個元素，就是集合中的單一元素或任意元素。如果集合是空的，則傳回 `null`。 如果 `collection` 是 `Collection<T>`類型的集合，則 `ANYELEMENT(collection)` 是產生 `T`類型實例的有效運算式。  
  
## <a name="remarks"></a>備註  
 ANYELEMENT 會從多重值集合中擷取任意元素。 例如，下列範例會嘗試從 `Customers`集合中擷取單一元素。  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>範例  
 下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢會使用 ANYELEMENT 運算子，從多重值集合中擷取元素。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [可為 Null 的結構類型](nullable-structured-types-entity-sql.md)
