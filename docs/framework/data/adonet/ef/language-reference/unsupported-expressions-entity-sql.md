---
title: 不支援的運算式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: af0e00f470584883b6a65b63f2650c1c359b404c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489866"
---
# <a name="unsupported-expressions"></a>不支援的運算式

本主題描述中不支援的 TRANSACT-SQL 運算式[!INCLUDE[esql](../../../../../../includes/esql-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 說明 Entity SQL 語法之間差異 TRANSACT-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)。

## <a name="quantified-predicates"></a>定量述詞

TRANSACT-SQL 允許建構下列形式：

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

TRANSACT-SQL 支援使用 * 表示所有資料行都應該投影出來 SELECT 子句中的運算子。這在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中不支援。

## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Entity SQL 與 Transact-SQL 的相異之處](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
