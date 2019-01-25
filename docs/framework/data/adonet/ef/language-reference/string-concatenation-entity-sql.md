---
title: + （字串串連）(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: e53bd0a2607deb67d45edc44e51cf4ad283b21c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633911"
---
# <a name="-string-concatenation-entity-sql"></a>+ (字串串連) (Entity SQL)
串連兩個字串。  
  
## <a name="syntax"></a>語法  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 EDM.String 資料型別的任何有效運算式。 兩個運算式的資料型別必須相同，或者其中一個運算式必須可以用隱含方式轉換為另一個運算式的資料型別。  
  
## <a name="result-types"></a>結果型別  
 從兩個引數的隱含型別提升產生的資料型別。 如需有關隱含型別提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 + 運算子來串連兩個字串。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2.  將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a>另請參閱
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [概念模型類型 (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
