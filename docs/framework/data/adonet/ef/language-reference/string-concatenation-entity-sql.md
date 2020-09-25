---
title: '+  (字串串連)  (Entity SQL) '
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 92591448a3707ba11ad2462161050e48e0398728
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173623"
---
# <a name="-string-concatenation-entity-sql"></a>+ (字串串連) (Entity SQL)

串連兩個字串。  
  
## <a name="syntax"></a>語法  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a>引數  

 `expression`  
 EDM.String 資料型別的任何有效運算式。 兩個運算式的資料類型必須相同，或者其中一個運算式必須可以用隱含方式轉換為另一個運算式的資料類型。  
  
## <a name="result-types"></a>結果類型  

 從兩個引數的隱含型別提升產生的資料型別。 如需隱含類型升級的詳細資訊，請參閱 [類型系統](type-system-entity-sql.md)。  
  
## <a name="example"></a>範例  

 下列 Entity SQL 查詢會使用 + 運算子來串連兩個字串。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 依照 how [to：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式操作。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [概念模型類型 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
