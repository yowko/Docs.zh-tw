---
title: "不支援的運算式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a7dde3d88b5b21df99be64cedc92d6aa06b00d3b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="unsupported-expressions-entity-sql"></a>不支援的運算式 (Entity SQL)
本主題會描述 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中不支援的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式。 如需詳細資訊，請參閱[如何 Entity SQL 與 TRANSACT-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)。  
  
## <a name="quantified-predicates"></a>數量化的述詞  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 允許下列形式的建構：  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 但是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 並不支援這類建構。 同等運算式可以使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 撰寫，如下所示：  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## <a name="-operator"></a>* 運算子  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 支援在 SELECT 子句中使用 * 運算子，以指示所有資料行都應該投影出來。這在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中不支援。  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Entity SQL 與 Transact-SQL 的相異之處](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
