---
title: '- （除法）(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 506553de78ce9fbdf5f3710805906ee8cd5b8757
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760436"
---
# <a name="-divide-entity-sql"></a>/ (除號) (Entity SQL)
將一個數字除以另一個數字。  
  
## <a name="syntax"></a>語法  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>引數  
 `dividend`  
 要當做被除數的數值運算式。 `dividend` 是任何一個數值資料型別的任何有效運算式。  
  
 `divisor`  
 要當做除數的數值運算式。 `divisor` 是任何一個數值資料型別的任何有效運算式。  
  
## <a name="result-types"></a>結果型別  
 從兩個引數的隱含型別提升產生的資料型別。 如需隱含類型提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 / 算術運算子讓兩個數字相除。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
