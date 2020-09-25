---
title: 查詢運算式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: ca6b79b4b3d3326a74780345decf58367596adb0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175599"
---
# <a name="query-expressions-entity-sql"></a>查詢運算式 (Entity SQL)

查詢運算式將許多不同的查詢運算子結合成單一語法。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供各種類型的運算式，包括下列各項： [常](literals-entity-sql.md)值、 [參數](parameters-entity-sql.md)、 [變數](variables-entity-sql.md)、運算子、 [函數](functions-entity-sql.md)、設定運算子等等。 如需詳細資訊，請參閱 [Entity SQL 參考](entity-sql-reference.md)。  
  
## <a name="clauses"></a>子句  

 查詢運算式是由一系列將後續運算套用到物件集合的子句組成。 它們是根據標準 SQL select 語句中所找到的相同子句： [select](select-entity-sql.md)、 [FROM](from-entity-sql.md)、 [WHERE](where-entity-sql.md)、 [GROUP BY](group-by-entity-sql.md)、 [HAVING](having-entity-sql.md)和 [ORDER BY](order-by-entity-sql.md)。  
  
## <a name="scope"></a>影響範圍  

 FROM 子句中定義的名稱會依出現的順序 (從左到右) 導入 FROM 範圍內。 在 JOIN 清單中，運算式可以參考之前定義在清單中的名稱。 FROM 子句中所識別項目的公用屬性不會加入到 FROM 範圍：它們一定要透過別名限定的名稱來參考。 一般而言，SELECT 運算式的所有部分都視為在 FROM 範圍中。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
