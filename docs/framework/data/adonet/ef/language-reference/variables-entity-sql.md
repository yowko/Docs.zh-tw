---
title: 變數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248695"
---
# <a name="variables-entity-sql"></a>變數 (Entity SQL)
## <a name="variable"></a>變數  
 變數運算式是目前範圍中所定義之具名運算式的參考。 變數參考必須是有效[!INCLUDE[esql](../../../../../../includes/esql-md.md)]的識別碼，如[識別碼](identifiers-entity-sql.md)中所定義。  
  
 下列範例示範如何在運算式中使用變數。 FROM 子句中的 `c` 是變數的定義。 SELECT 子句中的 `c` 使用代表變數參考。  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>另請參閱

- [識別項](identifiers-entity-sql.md)
- [參數](parameters-entity-sql.md)
- [Entity SQL 概觀](entity-sql-overview.md)
