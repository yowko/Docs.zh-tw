---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 44e411b8ae2f43bf3a729ac091ffd1eb4c462c63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303033"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)
從值清單建立多重集的執行個體。 MULTISET 建構函式 (Constructor) 中的所有值都必須是相容型別 `T`。 不允許空的多重集建構函式。  
  
## <a name="syntax"></a>語法  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何有效的值清單。  
  
## <a name="return-value"></a>傳回值  
 集合的型別 MULTISET\<T >。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供三種建構函式：資料列建構函式、物件建構函式和多重集 (或集合) 建構函式。 如需詳細資訊，請參閱 <<c0> [ 建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。  
  
 多重集建構函式會從值清單建立多重集的例項。 該建構函式中的所有值都必須是相容型別。  
  
 例如，下列運算式會建立整數的多重集。  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  包裝多重集有單一多重集項目; 時，才支援巢狀多重集常值比方說， `{{1, 2, 3}}`。 在包裝多重集有多個多重集項目 (例如 `{{1, 2}, {3, 4}}`) 的情況下，並不支援巢狀多重集常值。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 MULTISET 運算子，從值清單建立多重集的例項。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>另請參閱

- [建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
