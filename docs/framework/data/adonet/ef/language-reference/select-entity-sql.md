---
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: af704d00800a72b4ab670781c5bb3adec93683cb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489888"
---
# <a name="select-entity-sql"></a>SELECT (Entity SQL)
指定查詢要傳回的項目。  
  
## <a name="syntax"></a>語法  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>引數  
 ALL  
 指定結果集可以出現重複的項目。 預設值為 ALL。  
  
 DISTINCT  
 指定結果集只能出現唯一的結果。  
  
 VALUE  
 只允許指定一個項目，而且不加入資料列包裝函式。  
  
 `topSubclause`  
 表示查詢所傳回第一組結果的數目，格式為 `top(expr)`。  
  
 LIMIT 參數[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)運算子也可讓您在結果集中選取前 n 個項目。  
  
 `aliasedExpr`  
 以下格式的運算式：  
  
 `expr` 為`identifier`&#124; `expr`  
  
 `expr`  
 常值或運算式。  
  
## <a name="remarks"></a>備註  
 SELECT 子句之後，會評估[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)， [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)，並[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)已評估子句。 SELECT 子句只可參考目前範圍內 (來自 FROM 子句，或來自外部範圍) 的項目。 如果指定了 GROUP BY 子句，SELECT 子句只可參考 GROUP BY 索引鍵的別名。 只允許在彙總函式中參考 FROM 子句項目。  
  
 位於 SELECT 關鍵字之後的一或多個查詢運算式就是所謂的選取清單，較正式的名稱則是投影。 投影最常見的形式是單一查詢運算式。 如果從集合 `member1` 選取成員 `collection1`，將會針對 `member1` 中的每一個物件產生所有 `collection1`值的新集合，如以下範例所示。  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 例如，假設 `customers` 是 `Customer` 型別的集合，而後者具有 `Name` 型別的屬性 `string`，那麼從 `Name` 選取 `customers` 將會產生字串的集合，如以下範例所示。  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 您也可以使用 JOIN 語法 (FULL、INNER、LEFT、OUTER、ON 和 RIGHT)。 ON 是內部聯結的必要項，但不可使用於交叉聯結。  
  
## <a name="row-and-value-select-clauses"></a>資料列選取和值選取子句  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援兩種 SELECT 子句的變異形式。 第一種變異形式是由 SELECT 關鍵字識別的資料列選取，用來指定應該投影來的一或多個值。由於傳回的值會以隱含方式加上資料列包裝函式，所以查詢運算式的結果一定是資料列的多重集。  
  
 資料列選取中的每一個查詢運算式必須指定一個別名。 如果未指定別名，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會嘗試依據別名產生規則產生別名。  
  
 SELECT 子句的另一種變異形式是由 SELECT VALUE 關鍵字識別的值選取。 它只允許指定一個值，而且不加入資料列包裝函式。  
  
 資料列選取永遠可以用 VALUE SELECT 的方式表示，如以下範例所示。  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>All 和 Distinct 修飾詞  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中這兩種 SELECT 的變異形式都可以指定 ALL 或 DISTINCT 修飾詞。 如果指定了 DISTINCT 修飾詞，便會從查詢運算式 (到 SELECT 子句為止) 產生的集合中排除重複項目。 如果指定了 ALL 修飾詞，就不會執行排除重複項目；ALL 是預設值。  
  
## <a name="differences-from-transact-sql"></a>與 Transact-SQL 的差異  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 與 Transact-SQL 的差異在於它不支援在 SELECT 子句中使用 * 引數。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會從 FROM 子句參考集合別名，用此方式讓查詢投影出整個記錄，如以下範例所示。  
  
```  
SELECT * FROM T1, T2  
```  
  
 先前的 TRANSACT-SQL 查詢運算式以表示[!INCLUDE[esql](../../../../../../includes/esql-md.md)]方式如下。  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用 SELECT 運算子指定查詢要傳回的項目。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>另請參閱

- [查詢運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
