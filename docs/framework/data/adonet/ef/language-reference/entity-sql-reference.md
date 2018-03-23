---
title: Entity SQL 參考
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: ac05ec8a8732da383a4e33e84c669aa29660a0da
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="entity-sql-reference"></a>Entity SQL 參考
本節內容包括 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 參考主題。 本主題將摘要說明 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算子並將它們依分類群組。  
  
## <a name="arithmetic-operators"></a>算術運算子  
 算術運算子會針對一個或多個數值資料型別的兩個運算式執行數學運算。 下表列出 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 算術運算子。  
  
|運算子|使用|  
|--------------|---------|  
|[+ (加)](../../../../../../docs/framework/data/adonet/ef/language-reference/add.md)|加法。|  
|"/ （除法）"|除法。|  
|[%（模數）](../../../../../../docs/framework/data/adonet/ef/language-reference/modulo-entity-sql.md)|傳回除法的餘數。|  
|[* (乘)](../../../../../../docs/framework/data/adonet/ef/language-reference/multiply-entity-sql.md)|乘法。|  
|[- (負)](../../../../../../docs/framework/data/adonet/ef/language-reference/negative-entity-sql.md)|否定。|  
|[- (減)](../../../../../../docs/framework/data/adonet/ef/language-reference/subtract-entity-sql.md)|減法。|  
  
## <a name="canonical-functions"></a>標準函式  
 所有資料提供者都支援標準函式，標準函式可以用於所有的查詢技術。 以下資料表列出標準函式。  
  
|函式|類型|  
|--------------|----------|  
|[彙總 Entity SQL 標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|討論彙總 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。|  
|[數學標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|討論數學 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。|  
|[字串標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|討論字串 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。|  
|[日期和時間標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|討論日期和時間 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。|  
|[位元標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|討論位元運算 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。|  
|[其他標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)|討論未分類為位元運算、日期/時間、字串、數學或彙總的函式。|  
  
## <a name="comparison-operators"></a>比較運算子  
 針對下列型別定義比較運算子：`Byte`、`Int16`、`Int32`、`Int64`、`Double`、`Single`、`Decimal`、`String`、`DateTime`、`Date`、`Time` 和 `DateTimeOffset`。 套用比較運算子之前，系統會針對運算元進行隱含型別提升。 比較運算子一律會產生布林值。 至少其中一個運算元是 `null` 時，結果就是 `null`。  
  
 針對具有識別 (Identity) 的任何物件型別 (例如 `Boolean` 型別) 定義了相等和不等。 如果包含識別的非基本物件共用相同的識別，它們就會被視為相等。 以下資料表列出 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 比較運算子。  
  
|運算子|描述|  
|--------------|-----------------|  
|[= (等於)](../../../../../../docs/framework/data/adonet/ef/language-reference/equals-entity-sql.md)|比較兩個運算式是否相等。|  
|[> (大於)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-entity-sql.md)|比較兩個運算式來判斷左運算式的值是否大於右運算式。|  
|[>= (大於或等於)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-or-equal-to-entity-sql.md)|比較兩個運算式來判斷左運算式的值是否大於或等於右運算式。|  
|[是&AMP;#91;不&AMP;#93;NULL](../../../../../../docs/framework/data/adonet/ef/language-reference/isnull-entity-sql.md)|判斷查詢運算式是否為 null。|  
|[< (小於)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-entity-sql.md)|比較兩個運算式來判斷左運算式的值是否小於右運算式。|  
|[<= (小於或等於)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-or-equal-to-entity-sql.md)|比較兩個運算式來判斷左運算式的值是否小於或等於右運算式。|  
|[&#91;NOT&#93; BETWEEN](../../../../../../docs/framework/data/adonet/ef/language-reference/between-entity-sql.md)|判斷運算式是否會產生所指定範圍內的值。|  
|[!= (不等於)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-equal-to-entity-sql.md)|比較兩個運算式來判斷左運算式是否不等於右運算式。|  
|[&#91;NOT&#93; LIKE](../../../../../../docs/framework/data/adonet/ef/language-reference/like-entity-sql.md)|判斷特定字元字串是否符合指定的模式。|  
  
## <a name="logical-and-case-expression-operators"></a>邏輯和 Case 運算式運算子  
 邏輯運算子會測試某個條件是否成立。 CASE 運算式會評估一組布林運算式來得出結果。 以下資料表列出邏輯和 CASE 運算式運算子。  
  
|運算子|描述|  
|--------------|-----------------|  
|[& & (邏輯 AND)](../../../../../../docs/framework/data/adonet/ef/language-reference/and-entity-sql.md)|邏輯 AND。|  
|[!(邏輯 NOT)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-entity-sql.md)|邏輯 NOT。|  
|[&#124;&#124; (Logical OR)](../../../../../../docs/framework/data/adonet/ef/language-reference/or-entity-sql.md)|邏輯 OR。|  
|[CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)|評估一組布林運算式來得出結果。|  
|[THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)|結果[時](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998)子句時評估為 true。|  
  
## <a name="query-operators"></a>查詢運算子  
 查詢運算子是用來定義傳回實體資料的查詢運算式。 以下資料表列出查詢運算子。  
  
|運算子|使用|  
|--------------|---------|  
|[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)|指定集合中所使用[選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)陳述式。|  
|[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)|指定的物件，查詢所傳回的群組 ([選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) 運算式是要放置。|  
|[GroupPartition](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)|傳回引數值的集合，該集合將群組分割投影至其相關的彙總。|  
|[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)|指定群組或彙總的搜尋條件。|  
|[LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)|搭配[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)子句，以執行實際分頁。|  
|[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)|指定所傳回物件使用的排序次序[選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)陳述式。|  
|[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)|指定查詢傳回的投影項目。|  
|[SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)|搭配[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)子句，以執行實際分頁。|  
|[TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)|指定只從查詢結果傳回第一組資料列。|  
|[WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)|條件式篩選查詢傳回的資料。|  
  
## <a name="reference-operators"></a>參考運算子參考  
 參考是指向特定實體集中特定實體的邏輯指標 (外部索引鍵)。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援下列運算子來建構、 解構及巡覽參考。  
  
|運算子|使用|  
|--------------|---------|  
|[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)|建立實體集中某個實體的參考。|  
|[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)|對參考值取值並且產生該取值的結果。|  
|[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)|擷取參考的索引鍵，或實體運算式的索引鍵。|  
|[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)|可讓您在關聯性上從一個實體類型巡覽到另一個實體類型|  
|[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)|傳回實體執行個體的參考。|  
  
## <a name="set-operators"></a>集合運算子  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供許多功能強大的設定作業。 這包括設定運算子類似 TRANSACT-SQL 運算子，例如 UNION、 INTERSECT、 EXCEPT 和 EXISTS。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也支援重複項目刪除 (SET)、成員資格測試 (IN) 和聯結 (JOIN) 運算子。 以下資料表列出 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。  
  
|運算子|使用|  
|--------------|---------|  
|[ANYELEMENT](../../../../../../docs/framework/data/adonet/ef/language-reference/anyelement-entity-sql.md)|從多重值集合中擷取元素。|  
|[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)|從 EXCEPT 運算元左側的查詢運算式傳回任何相異值集合，這些相異值是 EXCEPT 運算元右側的查詢運算式沒有傳回的。|  
|[&#91;NOT&#93; EXISTS](../../../../../../docs/framework/data/adonet/ef/language-reference/exists-entity-sql.md)|判斷集合是否為空。|  
|[FLATTEN](../../../../../../docs/framework/data/adonet/ef/language-reference/flatten-entity-sql.md)|將集合轉換成扁平化集合。|  
|[&#91;NOT&#93; IN](../../../../../../docs/framework/data/adonet/ef/language-reference/in-entity-sql.md)|判斷某個值是否與集合中的任何值相符。|  
|[INTERSECT](../../../../../../docs/framework/data/adonet/ef/language-reference/intersect-entity-sql.md)|傳回 INTERSECT 運算元左右兩側之查詢運算式都會傳回的任何相異值集合。|  
|[OVERLAPS](../../../../../../docs/framework/data/adonet/ef/language-reference/overlaps-entity-sql.md)|判斷兩個集合是否有共同項目。|  
|[SET](../../../../../../docs/framework/data/adonet/ef/language-reference/set-entity-sql.md)|用來產生移除所有重複項目的新集合，利用這種方式將物件的集合 (collection) 轉換成集 (set)。|  
|[UNION](../../../../../../docs/framework/data/adonet/ef/language-reference/union-entity-sql.md)|將二個或多個查詢的結果結合成單一集合。|  
  
## <a name="type-operators"></a>運算子型別  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供建構、 查詢和操作運算式 （值） 的型別中的作業。 以下資料表列出可與型別一起使用的運算子。  
  
|運算子|使用|  
|--------------|---------|  
|[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)|將一種資料類型的運算式轉換成另一種。|  
|[COLLECTION](../../../../../../docs/framework/data/adonet/ef/language-reference/collection-entity-sql.md)|用於[函式](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)作業可宣告實體類型或複雜型別的集合。|  
|[IS &#91;NOT&#93; OF](../../../../../../docs/framework/data/adonet/ef/language-reference/isof-entity-sql.md)|判斷運算式的型別是否不屬於所指定的型別或它的其中一個子型別。|  
|[OFTYPE](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)|從屬於特定型別的查詢運算式中傳回物件的集合。|  
|[具名類型建構函式](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)|用來建立實體類型或複雜型別的執行個體。|  
|[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)|從值清單建立多重集的執行個體。|  
|[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)|從一個或多個值建構匿名、結構式型別的記錄。|  
|[TREAT](../../../../../../docs/framework/data/adonet/ef/language-reference/treat-entity-sql.md)|將特定基底類型的物件視為所指定之衍生型別的物件。|  
  
## <a name="other-operators"></a>其他運算子  
 下表列出其他[!INCLUDE[esql](../../../../../../includes/esql-md.md)]運算子。  
  
|運算子|使用|  
|--------------|---------|  
|[+ (字串串連)](../../../../../../docs/framework/data/adonet/ef/language-reference/string-concatenation-entity-sql.md)|用來串連 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的字串。|  
|[.(成員存取)](../../../../../../docs/framework/data/adonet/ef/language-reference/member-access-entity-sql.md)|用來存取結構化概念模型型別之執行個體的屬性或欄位值。|  
|[-- (註解)](../../../../../../docs/framework/data/adonet/ef/language-reference/comment-entity-sql.md)|包括 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 註解。|  
|[FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)|定義可在 Entity SQL 查詢中執行的內嵌函式。|  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 語言](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
