---
title: 查詢運算式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: d721f54486845847ec86253356e7a605f882722b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763549"
---
# <a name="query-expressions-entity-sql"></a>查詢運算式 (Entity SQL)
查詢運算式將許多不同的查詢運算子結合成單一語法。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供許多不同種類的運算式，包括下列：[常值](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)，[參數](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)，[變數](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)，運算子[函式](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)、 設定運算子，等等。 如需詳細資訊，請參閱[Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)。  
  
## <a name="clauses"></a>子句  
 查詢運算式是由一系列將後續運算套用到物件集合的子句組成。 它們所根據相同的子句中標準 SQL select 陳述式：[選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)， [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)，[其中](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)， [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)， [具有](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)，和[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)。  
  
## <a name="scope"></a>範圍  
 FROM 子句中定義的名稱會依出現的順序 (從左到右) 導入 FROM 範圍內。 在 JOIN 清單中，運算式可以參考之前定義在清單中的名稱。 FROM 子句中所識別項目的公用屬性不會加入到 FROM 範圍：它們一定要透過別名限定的名稱來參考。 一般而言，SELECT 運算式的所有部分都視為在 FROM 範圍中。  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
