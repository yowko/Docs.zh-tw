---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833898"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
對參考值取值並且產生該取值的結果。  
  
## <a name="syntax"></a>語法  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 傳回集合的任何有效查詢運算式。  
  
## <a name="return-value"></a>傳回值  
 所參考之實體的值。  
  
## <a name="remarks"></a>備註  
 DEREF 運算子會對參考值取值並且產生該取值的結果。 例如，如果 `r` 是類型 ref @ no__t-1T > 的參考，`Deref(r)` 是會產生 `r` 所參考之實體的類型為 `T` 的運算式。 如果此參數值為 null，或為懸空 (也就是參考的目標不存在)，DEREF 運算子的結果就會是 null。  
  
## <a name="example"></a>範例  
 以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 DEREF 運算子對參考值取值並且產生該取值的結果。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 依照 [How 中的程式進行：執行可傳回 PrimitiveType 結果 @ no__t-0 的查詢。  
  
2. 將下列查詢當成引數傳遞至 ExecutePrimitiveTypeQuery 方法：  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [可為 Null 的結構類型](nullable-structured-types-entity-sql.md)
