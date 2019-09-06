---
title: 不支援的運算式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: 956fe117eb0c59392c3999046bc70deaed268ac6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248787"
---
# <a name="unsupported-expressions"></a>不支援的運算式

本主題描述中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]不支援的 transact-sql 運算式。 如需詳細資訊, 請參閱[Entity SQL 與 transact-sql 的差異](how-entity-sql-differs-from-transact-sql.md)。

## <a name="quantified-predicates"></a>量化述詞

Transact-sql 允許下列形式的結構:

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

Transact-sql 支援在 SELECT 子句中使用 * 運算子, 以表示應該投射出所有資料行。這在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中不支援。

## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
- [Entity SQL 與 Transact-SQL 的相異之處](how-entity-sql-differs-from-transact-sql.md)
