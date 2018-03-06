---
title: "不支援的運算式 (Entity SQL)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-ado
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
dev_langs:
- sql
ms.openlocfilehash: 075daf0e4f0477dda50231760fbb3d990a9f8468
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="unsupported-expressions"></a><span data-ttu-id="c8244-102">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="c8244-102">Unsupported expressions</span></span>

<span data-ttu-id="c8244-103">本主題會描述 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中不支援的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="c8244-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="c8244-104">如需詳細資訊，請參閱[如何 Entity SQL 與 TRANSACT-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="c8244-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="c8244-105">定量述詞</span><span class="sxs-lookup"><span data-stu-id="c8244-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="c8244-106">允許下列形式的建構：</span><span class="sxs-lookup"><span data-stu-id="c8244-106">allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c8244-107">不過，不支援這類建構。</span><span class="sxs-lookup"><span data-stu-id="c8244-107">, however, does not support such constructs.</span></span> <span data-ttu-id="c8244-108">同等運算式可以使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 撰寫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c8244-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal > e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="c8244-109">\* 運算子</span><span class="sxs-lookup"><span data-stu-id="c8244-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="c8244-110">支援使用 \* 表示所有資料行都應該投影出來 SELECT 子句中的運算子。這在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中不支援。</span><span class="sxs-lookup"><span data-stu-id="c8244-110">supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="c8244-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8244-111">See also</span></span>

[<span data-ttu-id="c8244-112">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="c8244-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[<span data-ttu-id="c8244-113">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="c8244-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
