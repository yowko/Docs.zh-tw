---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 02eeaeb8cfa335e5545b26d3d52b91c4e1614629
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230703"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
直接之後套用 WHERE 子句[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)子句。  
  
## <a name="syntax"></a>語法  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 布林型別。  
  
## <a name="remarks"></a>備註  
 WHERE 子句的語意與針對 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 所述者相同。 它會將來源集合的項目限制為能通過此條件者，利用這種方式來限制查詢運算式產生的物件。  
  
```  
select c from cs as c where e  
```  
  
 運算式 `e` 必須為布林型別。  
  
 WHERE 子句是直接套用在 FROM 子句之後，且在任何群組、排序或投影發生之前。 WHERE 子句的運算式可以看到 FROM 子句中定義的所有項目名稱。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [查詢運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
