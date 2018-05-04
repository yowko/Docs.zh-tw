---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 89306c8b4c317ebaba0d964869c4fe9e1028631a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="using-entity-sql"></a>USING (Entity SQL)
指定查詢運算式中使用的命名空間 (Namespace)。  
  
## <a name="syntax"></a>語法  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>引數  
 `alias`  
 指定較短的別名 (Alias)，以便限定命名空間。  
  
 `namespace`  
 任何有效的命名空間。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 USING 運算子來指定查詢運算式中使用的命名空間。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  請依照下列中的程序[如何： 執行查詢，傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2.  將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>另請參閱  
 [命名空間](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
