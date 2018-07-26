---
title: Entity SQL 參考
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: d6b40d0c1662e18ed83c58bfdde7b6dac65220dd
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39221045"
---
# <a name="entity-sql-reference"></a>Entity SQL 參考

本章節包含 Entity SQL 參考文件。 本文摘要說明，並依類別分組的 Entity SQL 運算子。

## <a name="arithmetic-operators"></a>算術運算子

算術運算子會針對一個或多個數值資料型別的兩個運算式執行數學運算。 下表列出 Entity SQL 的算術運算子：

|運算子|使用|
|--------------|---------|
|[+ (加)](add.md)|加法。|
|[/ (除)](divide-entity-sql.md)|除法。|
|[%（模數）](modulo-entity-sql.md)|傳回除法的餘數。|
|[* (乘)](multiply-entity-sql.md)|乘法。|
|[- (負)](negative-entity-sql.md)|否定。|
|[- (減)](subtract-entity-sql.md)|減法。|

## <a name="canonical-functions"></a>標準函式

所有資料提供者都支援標準函式，標準函式可以用於所有的查詢技術。 下表列出標準函式：

|功能|類型|
|--------------|----------|
|[彙總 Entity SQL 標準函式](aggregate-canonical-functions.md)|討論彙總的 Entity SQL 標準函式。|
|[數學標準函式](math-canonical-functions.md)|討論數學 Entity SQL 標準函式。|
|[字串標準函式](string-canonical-functions.md)|討論字串 Entity SQL 標準函式。|
|[日期和時間標準函式](date-and-time-canonical-functions.md)|討論日期和時間 Entity SQL 標準函式。|
|[位元標準函式](bitwise-canonical-functions.md)|討論位元的 Entity SQL 標準函式。|
|[其他標準函式](other-canonical-functions.md)|討論未分類為位元運算、日期/時間、字串、數學或彙總的函式。|

## <a name="comparison-operators"></a>比較運算子

針對下列型別定義比較運算子：`Byte`、`Int16`、`Int32`、`Int64`、`Double`、`Single`、`Decimal`、`String`、`DateTime`、`Date`、`Time` 和 `DateTimeOffset`。 套用比較運算子之前，系統會針對運算元進行隱含型別提升。 比較運算子一律會產生布林值。 至少其中一個運算元是 `null` 時，結果就是 `null`。

針對具有識別 (Identity) 的任何物件型別 (例如 `Boolean` 型別) 定義了相等和不等。 如果包含識別的非基本物件共用相同的識別，它們就會被視為相等。 下表列出的 Entity SQL 的比較運算子：

|運算子|描述|
|--------------|-----------------|
|[= (等於)](equals-entity-sql.md)|比較兩個運算式是否相等。|
|[> (大於)](greater-than-entity-sql.md)|比較兩個運算式來判斷左運算式的值是否大於右運算式。|
|[>= (大於或等於)](greater-than-or-equal-to-entity-sql.md)|比較兩個運算式來判斷左運算式的值是否大於或等於右運算式。|
|[已\[不\]NULL](isnull-entity-sql.md)|判斷查詢運算式是否為 null。|
|[< (小於)](less-than-entity-sql.md)|比較兩個運算式來判斷左運算式的值是否小於右運算式。|
|[<= (小於或等於)](less-than-or-equal-to-entity-sql.md)|比較兩個運算式來判斷左運算式的值是否小於或等於右運算式。|
|[\[不\]BETWEEN](between-entity-sql.md)|判斷運算式是否會產生所指定範圍內的值。|
|[\!= （不等於）](not-equal-to-entity-sql.md)|比較兩個運算式，以判斷左的運算式是否不等於右運算式。|
|[\[不\]等](like-entity-sql.md)|判斷特定字元字串是否符合指定的模式。|

## <a name="logical-and-case-expression-operators"></a>邏輯和 case 運算式運算子

邏輯運算子會測試某個條件是否成立。 CASE 運算式會評估一組布林運算式來得出結果。 下表列出的邏輯和 CASE 運算式運算子：

|運算子|描述|
|--------------|-----------------|
|[&& (邏輯 AND)](and-entity-sql.md)|邏輯 AND。|
|[\! (邏輯 NOT)](not-entity-sql.md)|邏輯 NOT。|
|[&#124;&#124;(邏輯 OR)](or-entity-sql.md)|邏輯 OR。|
|[CASE](case-entity-sql.md)|評估一組布林運算式來得出結果。|
|[THEN](then-entity-sql.md)|結果[當](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998)子句評估為 true 時。|

## <a name="query-operators"></a>查詢運算子

查詢運算子是用來定義傳回實體資料的查詢運算式。 下表列出查詢運算子：

|運算子|使用|
|--------------|---------|
|[FROM](from-entity-sql.md)|指定集合中使用[選取](select-entity-sql.md)陳述式。|
|[GROUP BY](group-by-entity-sql.md)|指定物件的查詢所傳回的群組 ([選取](select-entity-sql.md)) 運算式要放置。|
|[GroupPartition](grouppartition-entity-sql.md)|傳回引數值的集合，該集合將群組分割投影至其相關的彙總。|
|[HAVING](having-entity-sql.md)|指定群組或彙總的搜尋條件。|
|[LIMIT](limit-entity-sql.md)|搭配[ORDER BY](order-by-entity-sql.md)子句，以執行實際分頁。|
|[ORDER BY](order-by-entity-sql.md)|指定在傳回的物件使用的排序次序[選取](select-entity-sql.md)陳述式。|
|[SELECT](select-entity-sql.md)|指定查詢傳回的投影項目。|
|[SKIP](skip-entity-sql.md)|搭配[ORDER BY](order-by-entity-sql.md)子句，以執行實際分頁。|
|[TOP](top-entity-sql.md)|指定只從查詢結果傳回第一組資料列。|
|[WHERE](where-entity-sql.md)|條件式篩選查詢傳回的資料。|

## <a name="reference-operators"></a>參考運算子

參考是指向特定實體集中特定實體的邏輯指標 (外部索引鍵)。 Entity SQL 支援下列用來建構、 解構及巡覽參考的運算子：

|運算子|使用|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|建立實體集中某個實體的參考。|
|[DEREF](deref-entity-sql.md)|對參考值取值並且產生該取值的結果。|
|[KEY](key-entity-sql.md)|擷取參考的索引鍵，或實體運算式的索引鍵。|
|[NAVIGATE](navigate-entity-sql.md)|可讓您在關聯性上從一個實體類型巡覽到另一個實體類型|
|[REF](ref-entity-sql.md)|傳回實體執行個體的參考。|

## <a name="set-operators"></a>設定運算子

Entity SQL 可提供各種功能強大的設定作業。 這包括設定運算子類似於 TRANSACT-SQL 的運算子，例如 UNION、 INTERSECT、 EXCEPT 和 EXISTS。 Entity SQL 也支援重複的項目刪除 (SET)、 成員資格測試 (IN) 和聯結 (JOIN) 的運算子。 下表列出 Entity SQL 設定運算子：

|運算子|使用|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|從多重值集合中擷取元素。|
|[EXCEPT](except-entity-sql.md)|從查詢運算式傳回任何相異值的集合，也不從查詢運算式傳回 EXCEPT 運算元右側 EXCEPT 運算元左邊。|
|[\[不\]EXISTS](exists-entity-sql.md)|判斷集合是否為空。|
|[FLATTEN](flatten-entity-sql.md)|將集合轉換成扁平化集合。|
|[\[不\]IN](in-entity-sql.md)|判斷某個值是否與集合中的任何值相符。|
|[INTERSECT](intersect-entity-sql.md)|傳回 INTERSECT 運算元左右兩側之查詢運算式都會傳回的任何相異值集合。|
|[OVERLAPS](overlaps-entity-sql.md)|判斷兩個集合是否有共同項目。|
|[SET](set-entity-sql.md)|用來產生移除所有重複項目的新集合，利用這種方式將物件的集合 (collection) 轉換成集 (set)。|
|[UNION](union-entity-sql.md)|將二個或多個查詢的結果結合成單一集合。|

## <a name="type-operators"></a>型別運算子

Entity SQL 提供的型別可用於建構、 查詢及操作運算式 （值） 的作業。 下表列出用來與類型搭配使用的運算子：

|運算子|使用|
|--------------|---------|
|[CAST](cast-entity-sql.md)|將一種資料類型的運算式轉換成另一種。|
|[COLLECTION](collection-entity-sql.md)|用於[函式](function-entity-sql.md)作業，以宣告實體類型或複雜型別的集合。|
|[已\[不\]OF](isof-entity-sql.md)|判斷運算式的型別是否不屬於所指定的型別或它的其中一個子型別。|
|[OFTYPE](oftype-entity-sql.md)|從屬於特定型別的查詢運算式中傳回物件的集合。|
|[具名類型建構函式](named-type-constructor-entity-sql.md)|用來建立實體類型或複雜型別的執行個體。|
|[MULTISET](multiset-entity-sql.md)|從值清單建立多重集的執行個體。|
|[ROW](row-entity-sql.md)|從一個或多個值建構匿名、結構式型別的記錄。|
|[TREAT](treat-entity-sql.md)|將特定基底類型的物件視為所指定之衍生型別的物件。|

## <a name="other-operators"></a>其他運算子

下表列出其他 Entity SQL 運算子：

|運算子|使用|
|--------------|---------|
|[+ (字串串連)](string-concatenation-entity-sql.md)|用來串連字串的 Entity SQL。|
|[.(成員存取)](member-access-entity-sql.md)|用來存取結構化概念模型型別之執行個體的屬性或欄位值。|
|[-- (註解)](comment-entity-sql.md)|包含 Entity SQL 註解。|
|[FUNCTION](function-entity-sql.md)|定義可在 Entity SQL 查詢中執行的內嵌函式。|

## <a name="see-also"></a>另請參閱

[Entity SQL 語言](entity-sql-language.md)
