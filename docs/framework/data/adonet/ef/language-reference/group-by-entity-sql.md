---
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 574d952e0183eb65c88864f2788eb7d698c9f2ec
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302942"
---
# <a name="group-by-entity-sql"></a>GROUP BY (Entity SQL)
指定要放置查詢 ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) 運算式所傳回物件的群組。  
  
## <a name="syntax"></a>語法  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>引數  
 `aliasedExpression`  
 在其中執行群組作業的任何有效查詢運算式。 `expression` 可以是屬性或參考 FROM 子句所傳回之屬性的非彙總運算式。 GROUP BY 子句中的每一個運算式都必評估為可以比較是否相等的型別 這些型別通常是純量基本型別，例如數值、字串和日期。 您不可依集合來群組。  
  
## <a name="remarks"></a>備註  
 如果彙總函式都包含 SELECT 子句中\<選取清單 >，GROUP BY 會計算每個群組的摘要值。 當指定 GROUP BY 時，GROUP BY 清單應該包括選取清單中之任何非彙總運算式中的每一個屬性名稱，否則，GROUP BY 運算式必須完全符合選取清單運算式。  
  
> [!NOTE]
>  如果未指定 ORDER BY 子句，由 GROUP BY 子句傳回的群組將不會依照任何特定順序。 若要指定特定資料排序，建議您一律使用 ORDER BY 子句。  
  
 以明確或隱含方式 (例如，利用查詢中的 HAVING 子句) 指定 GROUP BY 子句時，目前的範圍將會被隱藏，並且導入新的範圍。  
  
 SELECT 子句、HAVING 子句和 ORDER BY 子句將無法再參考 FROM 子句中指定的項目名稱。 您只能參考群組運算式本身。 如果要這樣處理，您可以指派新名稱 (別名) 給每一個群組運算式。 如果不為群組運算式指定別名， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會嘗試使用別名產生規則來產生別名，如以下範例所示。  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 GROUP BY 子句無法參考同一個 GROUP BY 子句中前面所定義的名稱。  
  
 除了群組名稱之外，您也可以在 SELECT 子句、HAVING 子句和 ORDER BY 子句中指定彙總。 彙總會包含針對群組的每一個項目評估的運算式。 彙總運算子會縮減所有這些運算式的值 (通常會縮減成單一值，但並非一定如此)。 彙總運算式可參考父範圍中的原始項目名稱變數，或由 GROUP BY 子句本身導入的任何新名稱。 雖然彙是出現在 SELECT 子句、HAVING 子句和 ORDER BY 子句中，不過它們實際上是在群組運算式的相同範圍內評估，如以下範例所述。  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 此查詢使用 GROUP BY 子句來產生所訂購的所有產品的成本報表，並依產品細分。 它將名稱 `name` 指定給產品當成群組運算式的一部分，然後在 SELECT 清單中參考該名稱。 它也在 SELECT 清單中指定以內部方式參考訂單行價格和數量的彙總 `sum` 。  
  
 每個 GROUP By 索引鍵運算式至少要有一個輸入範圍的參考：  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 如需使用 GROUP BY 的範例，請參閱 [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用 GROUP BY 運算子指定查詢傳回的物件所在的群組。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [查詢運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
