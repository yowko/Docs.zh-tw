---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 8dd0e34a6669b2147052befb17b8f4ff8395aabc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248476"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
WHERE 子句會直接套用於[from](from-entity-sql.md)子句之後。  
  
## <a name="syntax"></a>語法  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 布林型別。  
  
## <a name="remarks"></a>備註  
 WHERE 子句的語義與 Transact-sql 所述的相同。 它會將來源集合的項目限制為能通過此條件者，利用這種方式來限制查詢運算式產生的物件。  
  
```  
select c from cs as c where e  
```  
  
 運算式 `e` 必須為布林型別。  
  
 WHERE 子句是直接套用在 FROM 子句之後，且在任何群組、排序或投影發生之前。 WHERE 子句的運算式可以看到 FROM 子句中定義的所有項目名稱。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [查詢運算式](query-expressions-entity-sql.md)
