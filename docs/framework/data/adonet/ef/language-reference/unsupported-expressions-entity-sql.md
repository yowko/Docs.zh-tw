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
# <a name="unsupported-expressions"></a><span data-ttu-id="4b29c-102">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="4b29c-102">Unsupported expressions</span></span>

<span data-ttu-id="4b29c-103">本主題描述中不支援的 TRANSACT-SQL 運算式[!INCLUDE[esql](../../../../../../includes/esql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4b29c-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="4b29c-104">如需詳細資訊，請參閱 <<c0> [ 說明 Entity SQL 語法之間差異 TRANSACT-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="4b29c-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="4b29c-105">定量述詞</span><span class="sxs-lookup"><span data-stu-id="4b29c-105">Quantified predicates</span></span>

<span data-ttu-id="4b29c-106">TRANSACT-SQL 允許建構下列形式：</span><span class="sxs-lookup"><span data-stu-id="4b29c-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

<span data-ttu-id="4b29c-107">但是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 並不支援這類建構。</span><span class="sxs-lookup"><span data-stu-id="4b29c-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="4b29c-108">同等運算式可以使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 撰寫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b29c-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="4b29c-109">\* 運算子</span><span class="sxs-lookup"><span data-stu-id="4b29c-109">\* operator</span></span>

<span data-ttu-id="4b29c-110">TRANSACT-SQL 支援使用 \* 表示所有資料行都應該投影出來 SELECT 子句中的運算子。這在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中不支援。</span><span class="sxs-lookup"><span data-stu-id="4b29c-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="4b29c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b29c-111">See also</span></span>

- [<span data-ttu-id="4b29c-112">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="4b29c-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="4b29c-113">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="4b29c-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
