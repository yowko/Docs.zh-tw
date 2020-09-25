---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: a117f377b3f03b6a1a12e39426a24f3141aa40ff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204459"
---
# <a name="having-entity-sql"></a>HAVING (Entity SQL)

指定群組或彙總的搜尋條件。  
  
## <a name="syntax"></a>語法  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>引數  

 `search_condition`  
 指定群組或彙總要符合的搜尋條件。 搭配 GROUP BY ALL 使用 HAVING 時，HAVING 子句會覆寫 ALL。  
  
## <a name="remarks"></a>備註  

 HAVING 子句是用來在群組的結果上指定額外篩選條件。 如果查詢運算式中未指定 GROUP BY 子句，便會假設為一組隱含的單一群組。  
  
> [!NOTE]
> HAVING 只能搭配 [SELECT](select-entity-sql.md) 語句使用。 未使用 [GROUP BY](group-by-entity-sql.md) 時，其行為就像 WHERE 子句一樣。  
  
HAVING 子句的運作方式很類似 WHERE 字句，唯一不同的是它必須套用在 GROUP BY 運算後面。 這表示 HAVING 子句只能進行對群組別名和匯總的參考，如下列範例所示：
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 前面的範例會將群組限制為包含一件產品以上的項目。  
  
## <a name="example"></a>範例  

 以下 Entity SQL 查詢使用 HAVING 和 GROUP BY 運算子指定群組或彙總的搜尋條件。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 依照 how [to：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式操作。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [查詢運算式](query-expressions-entity-sql.md)
