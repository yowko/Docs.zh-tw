---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 1907b8786622d3c8019c75916f997c830cc07cfb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180955"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)

WHERE 子句會直接套用於 [from](from-entity-sql.md) 子句之後。  
  
## <a name="syntax"></a>語法  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>引數  

 `expression`  
 布林型別。  
  
## <a name="remarks"></a>備註  

 WHERE 子句具有與 Transact-sql 所述相同的語義。 它會將來源集合的項目限制為能通過此條件者，利用這種方式來限制查詢運算式產生的物件。  
  
```sql  
select c from cs as c where e  
```  
  
 運算式 `e` 必須為布林型別。  
  
 WHERE 子句是直接套用在 FROM 子句之後，且在任何群組、排序或投影發生之前。 WHERE 子句的運算式可以看到 FROM 子句中定義的所有項目名稱。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [查詢運算式](query-expressions-entity-sql.md)
