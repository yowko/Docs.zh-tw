---
title: Entity SQL 與 Transact-SQL 的相異之處
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 96e2283074b6c69e51bb7fee4d4f257cdb58d615
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615627"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL 與 Transact-sql 的差異

本文說明 Entity SQL 與 Transact-sql 之間的差異。  
  
## <a name="inheritance-and-relationships-support"></a>繼承和關聯性支援  
 Entity SQL 直接與概念實體架構搭配運作，並且支援繼承和關聯性等概念模型功能。  
  
 當使用繼承時，從超型別執行個體的集合中選取子型別執行個體的作法通常會很實用。 Entity SQL 中的[oftype](oftype-entity-sql.md)運算子（類似于 `oftype` c # 序列中的）會提供這項功能。  
  
## <a name="support-for-collections"></a>集合的支援  
 Entity SQL 會將集合視為第一類實體。 例如：  
  
- 集合運算式在 `from` 子句中是有效的。  
  
- `in` 和 `exists` 子查詢已通用化，可允許任何集合。  
  
     子查詢是一種集合。 `e1 in e2`和 `exists(e)` 是用來執行這些作業的 Entity SQL 結構。  
  
- Set 作業 (如 `union`、`intersect` 和 `except`) 現在都可針對集合來操作。  
  
- 聯結可針對集合操作。  
  
## <a name="support-for-expressions"></a>運算式的支援  
 Transact-sql 具有子查詢（資料表）和運算式（資料列和資料行）。  
  
 為了支援集合和嵌套集合，Entity SQL 使所有專案成為運算式。 Entity SQL 比 Transact-sql 更具可組合，每個運算式都可以在任何地方使用。 查詢運算式一定會產生投影的型別集合，而且可在允許集合運算式的任何地方使用。 如需 Entity SQL 中不支援之 Transact-sql 運算式的詳細資訊，請參閱[不](unsupported-expressions-entity-sql.md)支援的運算式。  
  
 以下是所有有效的 Entity SQL 查詢：  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>子查詢的統一處理  
 基於資料表的強調，Transact-sql 會執行子查詢的內容相關轉譯。 例如，子句中的子查詢會被 `from` 視為多重集（資料表）。 但是 `select` 子句中使用的相同子查詢會視為純量子查詢。 同樣地，在運算子左邊使用的子查詢會被視為純量 `in` 子查詢，而右側則應該是多重集子查詢。  
  
 Entity SQL 消除了這些差異。 運算式的統一解譯不依賴使用此運算式的內容。 Entity SQL 會將所有子查詢視為多重集子查詢。 如果子查詢需要純量值，Entity SQL 會提供可 `anyelement` 在集合（在此案例中為子查詢）運作的運算子，並從集合中抽取單一值。  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>避免子查詢的隱含強制型轉  
 統一的子查詢處理有一個相關的副作用，就是會隱含地將子查詢轉換成純量值。 具體而言，在 Transact-sql 中，資料列的多重集（具有單一欄位）會隱含地轉換成純量值，其資料類型是欄位。  
  
 Entity SQL 不支援這種隱含強制型轉。 Entity SQL 提供 `ANYELEMENT` 運算子，以從集合中解壓縮單一值，並使用 `select value` 子句來避免在查詢運算式期間建立資料列包裝函式。  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Select Value：避免隱含資料列包裝函式  
 Transact-sql 子查詢中的 select 子句會以隱含方式，在子句中的專案周圍建立資料列包裝函式。 這意味我們無法建立純量或物件的集合。 Transact-sql 允許在 `rowtype` 具有一個欄位的與具有相同資料類型的單一值之間進行隱含強制型轉。  
  
 Entity SQL 提供 `select value` 子句來略過隱含資料列結構。 `select value` 子句中只能指定一個項目。 使用這類子句時，不會在子句中的專案周圍建立資料列包裝函式， `select` 而且可能會產生所需形狀的集合，例如 `select value a` 。  
  
 Entity SQL 也會提供資料列的函數來建立任意資料列。 `select`接受投影中的一或多個元素，並產生具有欄位的資料記錄：  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>左邊相互關聯與別名  
 在 Transact-sql 中，給定範圍內的運算式（例如或的單一子句 `select` `from` ）無法參考先前在相同範圍中定義的運算式。 某些 SQL （包括 Transact-sql）的方言在子句中支援的形式有限 `from` 。  
  
 Entity SQL 一般化子句中的左 `from` 相互關聯，並一致地處理它們。 `from` 子句中的運算式可參考相同子句中的先前定義 (左邊的定義)，而不需要其他語法。  
  
 Entity SQL 也會對涉及子句的查詢施加額外的限制 `group by` 。 `select`這類查詢的子句和子句中的運算式 `having` 只能透過其別名來參考索引 `group by` 鍵。 下列結構在 Transact-sql 中有效，但不在 Entity SQL 中：  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 若要在 Entity SQL 中執行此動作：  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>參考資料表 (集合) 的資料行 (屬性)  
 Entity SQL 中的所有資料行參考都必須以資料表別名來限定。 下列結構（假設 `a` 是資料表的有效資料行 `T` ）在 transact-sql 中有效，而不是在 Entity SQL 中。  
  
```sql  
SELECT a FROM T
```  
  
 Entity SQL 表單為  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 資料表別名在 `from` 子句中為選擇性。 資料表名稱會當做隱含別名使用。 Entity SQL 也允許下列表單：  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>導覽物件  
 Transact-sql 會使用 "." 標記法來參考資料表（之資料列）的資料行。 Entity SQL 會擴充這個標記法（從程式語言借用）來支持對象屬性的導覽。  
  
 例如，如果 `p` 是 Person 類型的運算式，以下是用來參考此人員位址城市的 Entity SQL 語法。  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>不支援\*  
 Transact-sql 支援使用非限定 \* 語法做為整個資料列的別名，以及限定 \* 語法（t. \* ）做為該資料表之欄位的快捷方式。 此外，Transact-sql 允許特殊的 count （ \* ）匯總，其中包含 null。  
  
 Entity SQL 不支援 * 結構。 表單和的 transact-SQL 查詢 `select * from T` `select T1.* from T1, T2...` 可以分別在 Entity SQL 中表示為 `select value t from T as t` 和 `select value t1 from T1 as t1, T2 as t2...` 。 此外，這些建構會處理繼承 (值的可替代性)，而 `select *` Variant 則限制為宣告之型別的最上層屬性。  
  
 Entity SQL 不支援 `count(*)` 匯總。 請改用 `count(0)`。  
  
## <a name="changes-to-group-by"></a>變更成 Group By  
 Entity SQL 支援索引鍵的別名 `group by` 。 `select`子句和子句中的運算式 `having` 必須透過 `group by` 這些別名參考索引鍵。 例如，此 Entity SQL 語法：  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ...相當於下列 Transact-sql：  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>以集合為基礎的彙總  
 Entity SQL 支援兩種類型的匯總。  
  
 以集合為基礎的彙總會針對集合運作，並產生彙總的結果。 這些可以出現在查詢中的任何地方，而且不需要 `group by` 子句。 例如：  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 Entity SQL 也支援 SQL 樣式的匯總。 例如：  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY 子句使用方式  
Transact-sql `ORDER BY` 只允許在最上層區塊中指定子句 `SELECT .. FROM .. WHERE` 。 在 Entity SQL 中，您可以使用嵌套的 `ORDER BY` 運算式，它可以放在查詢中的任何位置，但不會保留在巢狀查詢中的順序。  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>識別碼  
 在 Transact-sql 中，識別碼比較是以目前資料庫的定序為基礎。 在 Entity SQL 中，識別碼一律不區分大小寫且區分重音（也就是 Entity SQL 區分重音和非重音字元; 例如，' a ' 不等於 ' ấ '）。 Entity SQL 會將出現相同但來自不同字碼頁的字母版本視為不同的字元。 如需詳細資訊，請參閱[輸入字元集](input-character-set-entity-sql.md)。  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Entity SQL 中無法使用 Transact-SQL 功能  
 Entity SQL 中無法使用下列 Transact-sql 功能。  
  
 DML  
 Entity SQL 目前不提供 DML 語句（insert、update、delete）的支援。  
  
 DDL  
 Entity SQL 在目前版本中不提供 DDL 的支援。  
  
 命令式程式設計  
 Entity SQL 不會提供命令式程式設計的支援，與 Transact-sql 不同。 請改用程式語言。  
  
 群組函式  
 Entity SQL 尚未提供群組函式的支援（例如 CUBE、ROLLUP 和 GROUPING_SET）。  
  
 分析函式  
 Entity SQL 尚未提供分析函數的支援。  
  
 內建函式，運算子  
 Entity SQL 支援 Transact-sql 內建函數和運算子的子集。 主要存放區提供者可能會支援這些運算子和函式。 Entity SQL 會使用在提供者資訊清單中宣告的存放區特有函式。 此外，Entity Framework 可讓您宣告內建和使用者定義的現有存放區函式，以供 Entity SQL 使用。  
  
 提示  
 Entity SQL 不提供查詢提示的機制。  
  
 批次處理查詢結果  
 Entity SQL 不支援批次處理查詢結果。 例如，下列是有效的 Transact-sql （以批次傳送）：  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 不過，不支援對等的 Entity SQL：  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 Entity SQL 只支援每個命令產生一個結果的查詢語句。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
- [不支援的運算式](unsupported-expressions-entity-sql.md)
