---
title: 不支援的運算式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: bf20bb92010d5031e973cb1cc004b6b8f13d0091
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="unsupported-expressions"></a>不支援的運算式

本主題會描述 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中不支援的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式。 如需詳細資訊，請參閱[如何 Entity SQL 與 TRANSACT-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)。

## <a name="quantified-predicates"></a>定量述詞

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 允許下列形式的建構：

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

但是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 並不支援這類建構。 同等運算式可以使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 撰寫，如下所示：

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* 運算子

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 支援在 SELECT 子句中使用 * 運算子，以指示所有資料行都應該投影出來。這在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中不支援。

## <a name="see-also"></a>另請參閱

[Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[Entity SQL 與 Transact-SQL 的相異之處](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
