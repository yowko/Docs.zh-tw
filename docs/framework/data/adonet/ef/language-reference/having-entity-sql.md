---
title: HAVING (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a64bc0c9b5e1358046e78429780af796f60e404e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="having-entity-sql"></a>HAVING (Entity SQL)
指定群組或彙總的搜尋條件。  
  
## <a name="syntax"></a>語法  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>引數  
 `search_condition`  
 指定群組或彙總要符合的搜尋條件。 搭配 GROUP BY ALL 使用 HAVING 時，HAVING 子句會覆寫 ALL。  
  
## <a name="remarks"></a>備註  
 HAVING 子句是用來在群組的結果上指定額外篩選條件。 如果查詢運算式中未指定 GROUP BY 子句，便會假設為一組隱含的單一群組。  
  
> [!NOTE]
>  可以使用 HAVING 只能搭配[選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)陳述式。 當[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)是未使用，HAVING 的行為就像是 WHERE 子句。  
  
 HAVING 子句的運作方式很類似 WHERE 字句，唯一不同的是它必須套用在 GROUP BY 運算後面。 這表示 HAVING 子句只能參考群組別名和彙總，如以下範例所述。  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 前面的範例會將群組限制為包含一件產品以上的項目。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用 HAVING 和 GROUP BY 運算子指定群組或彙總的搜尋條件。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  請依照下列中的程序[如何： 執行查詢，傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2.  將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [查詢運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
