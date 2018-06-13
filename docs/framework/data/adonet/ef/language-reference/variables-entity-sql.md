---
title: 變數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: f271ffc31875e7d94a27f4752b71bfe508fcb620
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765512"
---
# <a name="variables-entity-sql"></a>變數 (Entity SQL)
## <a name="variable"></a>變數  
 變數運算式是目前範圍中所定義之具名運算式的參考。 變數的參考必須是有效[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別碼中所定義[識別碼](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)。  
  
 下列範例示範如何在運算式中使用變數。 FROM 子句中的 `c` 是變數的定義。 SELECT 子句中的 `c` 使用代表變數參考。  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>另請參閱  
 [識別項](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [參數](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
