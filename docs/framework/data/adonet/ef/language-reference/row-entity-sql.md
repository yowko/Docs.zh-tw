---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: b83020601373ba93124dfb24308dd048bfa3c6dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797822"
---
# <a name="row-entity-sql"></a>ROW (Entity SQL)
從一個或多個值建構匿名、結構式型別的記錄。  
  
## <a name="syntax"></a>語法  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 資料列型別中任何傳回值到結構的有效查詢運算式。  
  
 `alias`  
 為資料列型別中指定的值指定別名。 如果未提供別名， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會嘗試依據 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 別名產生規則產生別名。  
  
## <a name="return-value"></a>傳回值  
 資料列型別。  
  
## <a name="remarks"></a>備註  
 在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中必須使用資料列建構函式從一或多個值建構匿名、結構式型別的記錄。 資料列建構函式的結果型別是資料列型別，而且它的欄位型別對應到用於建立此資料列的值的型別。 例如，下列運算式會建構 `Record(a int, b string, c int)`型別的值。  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 如果您沒有提供資料列建構函式中運算式的別名，Entity Framework 將會嘗試產生一個別名。 如需詳細資訊，請參閱 [識別項](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) 主題中的＜別名規則＞章節。  
  
 下列規則適用於資料列建構函式中的運算式別名：  
  
- 資料列建構函式中的運算式不可參考同一個建構函式中的其他別名。  
  
- 同一個資料列建構函式中的兩個運算式不能有相同的別名。  
  
 如需有關查詢建構函式的詳細資訊，請參閱 <<c0> [ 建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢使用 ROW 運算子來建構匿名、結構式型別的記錄。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>另請參閱

- [建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [型別定義](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
