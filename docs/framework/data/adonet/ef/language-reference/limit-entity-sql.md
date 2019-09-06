---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 432dfe2c8b2b87daf885be6de4da9bbeaaa37638
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250439"
---
# <a name="limit-entity-sql"></a>LIMIT (Entity SQL)
在 ORDER BY 子句中使用 LIMIT 次子句可以執行實際分頁。 LIMIT 不可單獨使用於 ORDER BY 子句之外。  
  
## <a name="syntax"></a>語法  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>引數  
 `n`  
 要選取的項目的數目。  
  
 如果 ORDER BY 子句中有 LIMIT 運算式次子句，此查詢將會依據排序規格排序，而且所產生的資料列數目將會受到 LIMIT 運算式的限制。 例如，LIMIT 5 會將結果集限制為 5 個執行個體或資料列。 LIMIT 在功能上就相當於 TOP，不同之處在於 LIMIT 必須配合 ORDER BY 子句。 SKIP 和 LIMIT 可以各自配合 ORDER BY 子句使用。  
  
> [!NOTE]
> 如果 TOP 修飾詞和 SKIP 次子句出現在同一個查詢運算式中，Entity SQL 查詢會被視為無效。 請將 TOP 運算式變更為 LIMIT 運算式來重新撰寫此查詢。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用 ORDER BY 運算子配合 LIMIT 來指定 SELECT 陳述式所傳回物件使用的排序順序。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>另請參閱

- [ORDER BY](order-by-entity-sql.md)
- [如何：逐頁查看查詢結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [分頁](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
