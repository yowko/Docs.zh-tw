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
# <a name="unsupported-expressions"></a><span data-ttu-id="07a05-102">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="07a05-102">Unsupported expressions</span></span>

<span data-ttu-id="07a05-103">本主題描述中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]不支援的 transact-sql 運算式。</span><span class="sxs-lookup"><span data-stu-id="07a05-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="07a05-104">如需詳細資訊, 請參閱[Entity SQL 與 transact-sql 的差異](how-entity-sql-differs-from-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="07a05-104">For more information, see [How Entity SQL Differs from Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="07a05-105">量化述詞</span><span class="sxs-lookup"><span data-stu-id="07a05-105">Quantified predicates</span></span>

<span data-ttu-id="07a05-106">Transact-sql 允許下列形式的結構:</span><span class="sxs-lookup"><span data-stu-id="07a05-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

<span data-ttu-id="07a05-107">但是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 並不支援這類建構。</span><span class="sxs-lookup"><span data-stu-id="07a05-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="07a05-108">同等運算式可以使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 撰寫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="07a05-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="07a05-109">\* 運算子</span><span class="sxs-lookup"><span data-stu-id="07a05-109">\* operator</span></span>

<span data-ttu-id="07a05-110">Transact-sql 支援在 SELECT 子句中使用 \* 運算子, 以表示應該投射出所有資料行。這在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中不支援。</span><span class="sxs-lookup"><span data-stu-id="07a05-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="07a05-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07a05-111">See also</span></span>

- [<span data-ttu-id="07a05-112">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="07a05-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="07a05-113">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="07a05-113">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)
