---
title: Entity SQL 與 Transact-SQL 的相異之處
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150227"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL 與 Transact-SQL 的相異之處
本主題介紹和交易[!INCLUDE[esql](../../../../../../includes/esql-md.md)]SQL 之間的差異。  
  
## <a name="inheritance-and-relationships-support"></a>繼承和關聯性支援  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]直接與概念實體架構配合使用，並支援概念模型功能，如繼承和關係。  
  
 當使用繼承時，從超型別執行個體的集合中選取子型別執行個體的作法通常會很實用。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]中的[類型](oftype-entity-sql.md)運算子（類似于`oftype`C# 序列中）提供此功能。  
  
## <a name="support-for-collections"></a>集合的支援  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]將集合視為一流的實體。 例如：  
  
- 集合運算式在 `from` 子句中是有效的。  
  
- `in` 和 `exists` 子查詢已通用化，可允許任何集合。  
  
     子查詢是一種集合。 `e1 in e2` 和 `exists(e)` 是用來執行這些作業的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 建構。  
  
- Set 作業 (如 `union`、`intersect` 和 `except`) 現在都可針對集合來操作。  
  
- 聯結可針對集合操作。  
  
## <a name="support-for-expressions"></a>運算式的支援  
 Transact-SQL 具有子查詢（表）和運算式（行和列）。  
  
 要支援集合和嵌套集合，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]使一切成為運算式。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]比 Transact-SQL 更可組合， 每個運算式都可以在任何地方使用。 查詢運算式一定會產生投影的型別集合，而且可在允許集合運算式的任何地方使用。 有關 中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]不支援的 Transact SQL 運算式的資訊，請參閱[。](unsupported-expressions-entity-sql.md)  
  
 下列全都是有效的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢：  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>子查詢的統一處理  
 鑒於它強調表，Transact-SQL 對子查詢執行上下文解釋。 例如，子句中的`from`子查詢被視為多集（表）。 但是 `select` 子句中使用的相同子查詢會視為純量子查詢。 同樣，運算子左側`in`使用的子查詢被視為標量子查詢，而右側應被視為多集子查詢。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會消除這些差異。 運算式的統一解譯不依賴使用此運算式的內容。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]將所有子查詢視為多集子查詢。 如果需要子查詢中的標量值，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]請提供對集合操作的`anyelement`運算子（在本例中為子查詢），並從集合中提取單例值。  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>避免子查詢的隱含強制型轉  
 統一的子查詢處理有一個相關的副作用，就是會隱含地將子查詢轉換成純量值。 具體而言，在 Transact-SQL 中，多組行（具有單個欄位）隱式轉換為資料類型為欄位的標量值。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支援這種隱含強制型轉。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供了可從集合中擷取單一值的 ANYELEMENT 運算子，以及一個可在查詢運算式期間避免建立資料列包裝函式的 `select value` 子句。  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Select Value：避免隱含資料列包裝函式  
 Transact-SQL 子查詢中的 select 子查詢中隱式創建圍繞子句中的項的行包裝器。 這意味我們無法建立純量或物件的集合。 Transact-SQL 允許在具有一個欄位的行型和相同資料類型的單例值之間隱式強制。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供 `select value` 子句來略過隱含資料列建構。 `select value` 子句中只能指定一個項目。 使用這類子句時，將不會建構包含 `select` 子句中這個項目的資料列包裝函式，並且可以產生所需形狀的集合，例如：`select value a`。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也提供資料列建構函式來建構任意資料列。 `select` 會擷取投影中的一個或多個項目，並產生具有欄位的資料記錄，如下所示：  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>左邊相互關聯與別名  
 在 Transact-SQL 中，給定作用域中的運算式（單個子句`select`（`from`如 或 ） 不能引用之前在同一作用域中定義的運算式。 SQL 的某些方言（包括 Transact-SQL）確實支援`from`子句中的有限形式。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]概括子句中的`from`左相關性，並統一處理它們。 `from` 子句中的運算式可參考相同子句中的先前定義 (左邊的定義)，而不需要其他語法。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也會針對與 `group by` 子句有關的查詢做出其他限制。 此類查詢的`select`子句和`having`子句中的運算式只能通過其別名引用`group by`鍵。 以下構造在 Transact-SQL 中有效，但不在[!INCLUDE[esql](../../../../../../includes/esql-md.md)]中：  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 若要在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中進行這項處理：  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>參考資料表 (集合) 的資料行 (屬性)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的所有資料行參考都必須以資料表別名來限定。 以下構造（假設是`a`表`T`的有效列）在 Transact-SQL 中有效，但在 中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]無效。  
  
```sql  
SELECT a FROM T
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 格式如下：  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 資料表別名在 `from` 子句中為選擇性。 資料表名稱會當做隱含別名使用。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也會顯示下列格式：  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>導覽物件  
 Transact-SQL 使用"." 標記法來引用表的列（一行）。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會擴充這個標記法 (從程式語言借用) 來支援物件之屬性的導覽。  
  
 例如，如果 `p` 是 Person 型別的運算式，下列是用來參考這個人之地址所在城市的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 語法。  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>* 表示不支援  
 Transact-SQL 支援將限定的 + 語法作為整個行的別名，並將\*限定語法 （t.\*） 作為該表字段的快捷方式。 此外，Transact-SQL 允許特殊計數 （\*） 聚合，其中包括 null。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支援 * 建構。 `select * from T`表單的轉算 SQL 查詢，`select T1.* from T1, T2...`並可以分別以[!INCLUDE[esql](../../../../../../includes/esql-md.md)]和`select value t from T as t``select value t1 from T1 as t1, T2 as t2...`表示。 此外，這些建構會處理繼承 (值的可替代性)，而 `select *` Variant 則限制為宣告之型別的最上層屬性。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支援 `count(*)` 彙總， 請改用 `count(0)`。  
  
## <a name="changes-to-group-by"></a>變更成 Group By  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援 `group by` 索引鍵的別名。 子句和`select``having`子句中的運算式必須通過這些別名引用`group by`鍵。 例如，這個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 語法：  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ...等效于以下交易 SQL：  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>以集合為基礎的彙總  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援兩種彙總。  
  
 以集合為基礎的彙總會針對集合運作，並產生彙總的結果。 這些可以出現在查詢中的任何地方，而且不需要 `group by` 子句。 例如：  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也支援 SQL 樣式彙總。 例如：  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY 子句使用方式  
Transact-SQL`ORDER BY`允許僅在最`SELECT .. FROM .. WHERE`頂層塊中指定子句。 在[!INCLUDE[esql](../../../../../../includes/esql-md.md)]中可以使用嵌套`ORDER BY`運算式，它可以放置在查詢的任意位置，但不會保留巢狀查詢中的排序。  
  
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
 在 Transact-SQL 中，識別碼比較基於當前資料庫的排序規則。 在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，識別項一律不會區分大小寫，但是會區分腔調字 (Accent Sensitive) (亦即，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會區別有腔調和無腔調字元。例如，'a' 不等於 'ấ')。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會將看起來一樣卻來自不同字碼頁的字母版本視為不同字元。 有關詳細資訊，請參閱[輸入字元集](input-character-set-entity-sql.md)。  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Entity SQL 中無法使用 Transact-SQL 功能  
 以下 Transact-SQL 功能在 中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]不可用。  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]目前不支援 DML 語句（插入、更新、刪除）。  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不提供目前版本中的任何 DDL 支援。  
  
 命令式程式設計  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]與 Transact-SQL 不同，不提供命令式程式設計的支援。 請改用程式語言。  
  
 群組函式  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 尚未提供群組函式 (如 CUBE、ROLLUP 和 GROUPING_SET) 的支援。  
  
 分析函式  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 尚未提供分析函式的支援。  
  
 內建函式，運算子  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]支援 Transact-SQL 內建函數和運算子的子集。 主要存放區提供者可能會支援這些運算子和函式。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]使用提供程式清單中聲明的特定于存儲的函數。 此外，實體框架允許您聲明要使用的內置和使用者定義的現有存儲函數[!INCLUDE[esql](../../../../../../includes/esql-md.md)]。  
  
 提示  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不提供查詢提示的機制。  
  
 批次處理查詢結果  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支援批次處理查詢結果。 例如，以下是有效的 Transact-SQL（作為批次處理發送）：  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 但是，同等的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 未受到支援：  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 在每個命令中只支援一個產生結果的查詢陳述式。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
- [不支援的運算式](unsupported-expressions-entity-sql.md)
