---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 76999bcbbb3b63fd945d2048734c58d97de8baea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249230"
---
# <a name="set-entity-sql"></a>SET (Entity SQL)
SET 運算式會產生移除所有重複項目的新集合，利用這種方式將物件的集合轉換成集合。  
  
## <a name="syntax"></a>語法  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 傳回集合的任何有效查詢運算式。  
  
## <a name="remarks"></a>備註  
 SET 運算式 `SET(c)` 在邏輯上相當於下列 SELECT 陳述式 (Statement)：  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。 如[需](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子的優先順序資訊，請參閱。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 SET 運算式，將物件的集合 (Collection) 轉換成單一集合 (Set)。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 PrimitiveType 結果](../how-to-execute-a-query-that-returns-primitivetype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
