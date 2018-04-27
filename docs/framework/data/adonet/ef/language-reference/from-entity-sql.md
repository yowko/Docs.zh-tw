---
title: FROM (Entity SQL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 64d41359ba8a4131acb38b128238065ee2545f80
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="from-entity-sql"></a>FROM (Entity SQL)
指定集合中使用[選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何有效的查詢運算式，該運算式可產生做為 `SELECT` 陳述式中之來源的集合。  
  
## <a name="remarks"></a>備註  
 `FROM` 子句是一個或多個 `FROM` 子句項目的逗號分隔清單。 `FROM` 子句可以用來為 `SELECT` 陳述式指定一個或多個來源。 `FROM` 子句最簡單的形式是單一查詢運算式，該運算式可識別做為 `SELECT` 陳述式中之來源的集合和別名 (Alias)，如下列範例所示：  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a>FROM 子句項目  
 每個 `FROM` 子句項目會參考 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢中的一個來源集合。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援下列 `FROM` 子句項目類別：簡單 `FROM` 子句項目、`JOIN FROM` 子句項目，以及 `APPLY FROM` 子句項目。 下列章節將更詳細說明這些 `FROM` 子句項目。  
  
### <a name="simple-from-clause-item"></a>簡單 FROM 子句項目  
 最簡單的 `FROM` 子句項目是可識別集合和別名的單一運算式。 運算式可以是實體集或子查詢，或是型別為集合的任何其他運算式。 以下是一個範例：  
  
```  
LOB.Customers as c  
```  
  
 別名規格是選擇性的。 上述 from 子句項目的替代規格可以是：  
  
```  
LOB.Customers  
```  
  
 如果未指定別名，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會嘗試依據集合運算式產生別名。  
  
### <a name="join-from-clause-item"></a>JOIN FROM 子句項目  
 `JOIN FROM` 子句項目代表介於兩個 `FROM` 子句項目之間的聯結。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援交叉聯結、內部聯結、左右外部連結，以及完整外部連結。 而支援這些聯結的方式與 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 支援的類似。 跟 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 一樣，`FROM` 所包含的兩個 `JOIN` 子句項目必須互為獨立， 也就是不能相互關聯。 `CROSS APPLY` 或 `OUTER APPLY` 適用於這些案例。  
  
#### <a name="cross-joins"></a>交叉聯結  
 `CROSS JOIN` 查詢運算式可產生兩個集合的笛卡兒乘積，如下列範例所示：  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a>內部聯結  
 `INNER JOIN` 查詢運算式可產生兩個集合的受限笛卡兒乘積，如下列範例所示：  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 前述查詢運算式可對照右集合的每個項目處理左集合的每個項目的組合，其中 `ON` 條件為 true。 如果未指定 `ON` 條件，`INNER JOIN` 會退化成 `CROSS JOIN`。  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a>左外部聯結和右外部聯結  
 `OUTER JOIN` 查詢運算式可產生兩個集合的受限笛卡兒乘積，如下列範例所示：  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 前述查詢運算式可對照右集合的每個項目處理左集合的每個項目的組合，其中 `ON` 條件為 true。 如果 `ON` 條件為 false，該運算式仍會對照右項目處理左項目的單一例項，但其結果值會是 null。  
  
 `RIGHT OUTER JOIN` 也可以用類似方式表示。  
  
#### <a name="full-outer-joins"></a>完整外部聯結  
 明確的 `FULL OUTER JOIN` 查詢運算式可產生兩個集合的受限笛卡兒乘積，如下列範例所示：  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 前述查詢運算式可對照右集合的每個項目處理左集合的每個項目的組合，其中 `ON` 條件為 true。 如果 `ON` 條件為 false，該運算式仍會對照右項目處理左項目的一個例項，但其結果值會是 null。 如果也對照左項目處理右項目的一個例項，其結果值會是 null。  
  
> [!NOTE]
>  為了維持與 SQL-92 的相容性，在 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中 OUTER 關鍵字是選擇性的。 因此，`LEFT JOIN`、`RIGHT JOIN` 和 `FULL JOIN` 是 `LEFT OUTER JOIN`、`RIGHT OUTER JOIN` 和 `FULL OUTER JOIN` 的同義字。  
  
### <a name="apply-clause-item"></a>APPLY Clause 子句項目  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 可支援兩種 `APPLY`：`CROSS APPLY` 和 `OUTER APPLY`。  
  
 `CROSS APPLY` 會以評估右運算式產生之集合的項目來產生左集合的每個項目的唯一配對。 使用 `CROSS APPLY`，右運算式的作用相依於左項目，如下列關聯的集合範例所示：  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 `CROSS APPLY` 和聯結清單類似。 如果右運算式評估為空集合，`CROSS APPLY` 不會為左項目的那個例項產生配對。  
  
 `OUTER APPLY` 除了即使在右運算式評估為空集合時還是會產生配對之外，都跟 `CROSS APPLY` 類似。 以下是 `OUTER APPLY` 的範例：  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  不同於在 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]，在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不需要明確的無巢狀步驟。  
  
> [!NOTE]
>  `CROSS` 已引入 `OUTER APPLY` 和 [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] 運算子。 在某些案例中，查詢管線可能產生含有 `CROSS APPLY` 和 (或) `OUTER APPLY` 運算子的 Transact-SQL。 因為有些後端提供者，包括 SQL Server 的版本早於[!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)]、 不支援這些運算子，這類查詢無法在執行這些後端提供者上。  
>   
>  下列一些典型的案例可能導致 `CROSS APPLY` 和 (或) `OUTER APPLY` 運算子出現在輸出查詢中：AnyElement 是在相互關聯的子查詢之上或是在導覽產生的集合之上；在 LINQ 查詢中使用的群組方法接受元素選擇器；在查詢中明確指定 `CROSS APPLY` 或 `OUTER APPLY`；在查詢中的 `DEREF` 建構是在 `REF` 建構之上。  
  
## <a name="multiple-collections-in-the-from-clause"></a>FROM 子句中的多個集合  
 `FROM` 子句可以包含一個以上的集合並用逗號分隔。 這些案例中假設集合聯結在一起。 請將這些集合視為 n 向 CROSS JOIN。  
  
 在下列範例中，`C`和`D`是獨立的集合，但`c.Names`相依於`C`。  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 上一個範例在邏輯上等同於下列範例：  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a>左方相互關聯  
 `FROM` 子句可以參考之前子句中指定的項目。 在下列範例中，`C` 和 `D` 是互為獨立的集合，但是 `c.Names` 相依於 `C`：  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 這在邏輯上等同於：  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a>語意  
 就邏輯而言，`FROM` 子句中的項目被假設為 `n` 向交叉聯結的一部分 (單向交叉聯結的案例除外)。 別名在 `FROM` 子句中的處理方向是由左至右，而且會被入至目前範圍，以供日後參考。 `FROM` 子句被假設為產生資料列的多重集 (Multiset)。 `FROM` 子句中的每個項目 (Item) 都會有一個欄位，其代表集合項目 (Item) 的單一項目 (Element)。  
  
 `FROM` 子句在邏輯上會產生型別為 Row(c, d, e) 之資料列的多重集，其中 c、d 和 e 被假設為是 `C`、`D` 和 `c.Names` 的項目型別。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 在範圍中會為每個簡單 `FROM` 子句引入別名。 例如，下列 FROM 子句程式碼片段中引入範圍內的名稱是 c、d 和 e。  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (不同於 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) 中，`FROM` 子句只會將別名引入範圍內。 對這些集合的資料行 (屬性) 的任何參考都必須以別名限定。  
  
## <a name="pulling-up-keys-from-nested-queries"></a>從巢狀查詢取出索引鍵  
 不支援某些需要從巢狀查詢取出索引鍵的查詢類型。 例如，以下是有效的查詢：  
  
```  
select c.Orders from Customers as c   
```  
  
 但是，以下是無效的查詢，因為巢狀查詢沒有索引鍵：  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [查詢運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [可為 Null 的結構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
