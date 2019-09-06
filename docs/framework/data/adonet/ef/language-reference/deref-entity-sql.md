---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 10c5ecb2b44c85dccd758cc1cf63a152da045cc1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251086"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
對參考值取值並且產生該取值的結果。  
  
## <a name="syntax"></a>語法  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 傳回集合的任何有效查詢運算式。  
  
## <a name="return-value"></a>傳回值  
 所參考之實體的值。  
  
## <a name="remarks"></a>備註  
 DEREF 運算子會對參考值取值並且產生該取值的結果。 例如，如果`r`是類型`r`ref\<T > 的參考，就是`Deref(r)`類型`T`的運算式，它會產生所參考的實體。 如果此參數值為 null，或為懸空 (也就是參考的目標不存在)，DEREF 運算子的結果就會是 null。  
  
## <a name="example"></a>範例  
 以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 DEREF 運算子對參考值取值並且產生該取值的結果。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 PrimitiveType 結果](../how-to-execute-a-query-that-returns-primitivetype-results.md)的查詢。  
  
2. 將下列查詢當成引數傳遞至 ExecutePrimitiveTypeQuery 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [可為 Null 的結構類型](nullable-structured-types-entity-sql.md)
