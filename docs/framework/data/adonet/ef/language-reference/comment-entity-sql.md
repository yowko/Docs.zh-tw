---
title: -- (註解) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 1ea1929b0e6f965f71fbb015ee6795affb3bce7c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251211"
---
# <a name="---comment-entity-sql"></a>-- (註解) (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢可以包含註解。 兩個破折號 (`--`) 就代表註解行的開始。  
  
## <a name="syntax"></a>語法  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a>引數  
 `text_of_comment`  
 這是包含註解文字的字元字串。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢示範如何使用註解。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
- [Entity SQL 參考](entity-sql-reference.md)
