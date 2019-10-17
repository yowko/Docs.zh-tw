---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: b551d15d7de2cf07afc7455b7fd0a0faf6436ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319188"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
WHERE 子句會直接套用於[from](from-entity-sql.md)子句之後。  
  
## <a name="syntax"></a>語法  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 布林型別。  
  
## <a name="remarks"></a>備註  
 WHERE 子句的語義與 Transact-sql 所述的相同。 它會將來源集合的項目限制為能通過此條件者，利用這種方式來限制查詢運算式產生的物件。  
  
```sql  
select c from cs as c where e  
```  
  
 運算式 `e` 必須為布林型別。  
  
 WHERE 子句是直接套用在 FROM 子句之後，且在任何群組、排序或投影發生之前。 WHERE 子句的運算式可以看到 FROM 子句中定義的所有項目名稱。  
  
## <a name="see-also"></a>請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [查詢運算式](query-expressions-entity-sql.md)
