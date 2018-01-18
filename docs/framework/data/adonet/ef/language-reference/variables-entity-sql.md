---
title: "變數 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d035f8d5616f2eb4c5a4db31857da2be0cd3d930
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="variables-entity-sql"></a>變數 (Entity SQL)
## <a name="variable"></a>變數  
 變數運算式是目前範圍中所定義之具名運算式的參考。 變數的參考必須是有效[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別碼中所定義[識別碼](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)。  
  
 下列範例示範如何在運算式中使用變數。 FROM 子句中的 `c` 是變數的定義。 SELECT 子句中的 `c` 使用代表變數參考。  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>請參閱  
 [識別項](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [參數](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
