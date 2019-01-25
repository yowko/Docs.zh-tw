---
title: 不支援的運算式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: a47ff46ca99a84500bc5dfecc19bb31652e9b4b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628011"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="27d91-102">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="27d91-102">Unsupported expressions</span></span>

<span data-ttu-id="27d91-103">本主題會描述 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中不支援的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="27d91-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="27d91-104">如需詳細資訊，請參閱 <<c0> [ 說明 Entity SQL 語法之間差異 TRANSACT-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="27d91-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="27d91-105">定量述詞</span><span class="sxs-lookup"><span data-stu-id="27d91-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="27d91-106">允許下列形式的建構：</span><span class="sxs-lookup"><span data-stu-id="27d91-106">allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

<span data-ttu-id="27d91-107">但是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 並不支援這類建構。</span><span class="sxs-lookup"><span data-stu-id="27d91-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="27d91-108">同等運算式可以使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 撰寫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="27d91-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="27d91-109">\* 運算子</span><span class="sxs-lookup"><span data-stu-id="27d91-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="27d91-110">支援在 SELECT 子句中使用 \* 運算子，以指示所有資料行都應該投影出來。這在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中不支援。</span><span class="sxs-lookup"><span data-stu-id="27d91-110">supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="27d91-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27d91-111">See also</span></span>

- [<span data-ttu-id="27d91-112">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="27d91-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="27d91-113">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="27d91-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
