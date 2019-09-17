---
title: 查詢運算式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 4428286890f41573a02daf31a4593d0c8f9ad34b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249280"
---
# <a name="query-expressions-entity-sql"></a>查詢運算式 (Entity SQL)
查詢運算式將許多不同的查詢運算子結合成單一語法。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供各種類型的運算式，包括：[常值](literals-entity-sql.md)、[參數](parameters-entity-sql.md)、[變數](variables-entity-sql.md)、運算子、[函式](functions-entity-sql.md)、集合運算子等等。 如需詳細資訊，請參閱[Entity SQL 參考](entity-sql-reference.md)。  
  
## <a name="clauses"></a>子句  
 查詢運算式是由一系列將後續運算套用到物件集合的子句組成。 它們是以在標準 SQL select 語句中找到的相同子句為基礎：[SELECT](select-entity-sql.md)、 [FROM](from-entity-sql.md)、 [WHERE](where-entity-sql.md)、 [GROUP BY](group-by-entity-sql.md)、 [HAVING](having-entity-sql.md)和[ORDER by](order-by-entity-sql.md)。  
  
## <a name="scope"></a>`Scope`  
 FROM 子句中定義的名稱會依出現的順序 (從左到右) 導入 FROM 範圍內。 在 JOIN 清單中，運算式可以參考之前定義在清單中的名稱。 在 FROM 子句中識別之元素的公用屬性不會加入至 FROM 範圍：必須一律透過別名限定的名稱來參考它們。 一般而言，SELECT 運算式的所有部分都視為在 FROM 範圍中。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
