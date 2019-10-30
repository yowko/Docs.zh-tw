---
title: -- (註解) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 43b8cdbf5dbca8822645c27711f6984b8d741ea7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040279"
---
# <a name="---comment-entity-sql"></a>-- (註解) (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢可以包含註解。 兩個破折號 (`--`) 就代表註解行的開始。  
  
## <a name="syntax"></a>語法  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a>引數  
 `text_of_comment`  
 這是包含註解文字的字元字串。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢示範如何使用註解。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
- [Entity SQL 參考](entity-sql-reference.md)
