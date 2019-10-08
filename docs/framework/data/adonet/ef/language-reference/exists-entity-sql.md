---
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 44f128a292b013fd3a3a80efdd2d10a63e3cfb07
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833829"
---
# <a name="exists-entity-sql"></a>EXISTS (Entity SQL)
判斷集合是否為空。  
  
## <a name="syntax"></a>語法  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 可傳回集合的任何有效運算式。  
  
 NOT  
 指定 EXISTS 的結果為否定運算。  
  
## <a name="return-value"></a>傳回值  
 如果集合不是空的則為 `true`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
 EXISTS 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。 如需 @no__t 0 設定運算子的優先順序資訊，請參閱[EXCEPT](except-entity-sql.md)。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 EXISTS 運算子判斷集合是否為空的。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 依照 [How 中的程式進行：執行可傳回 StructuralType 結果 @ no__t-0 的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
