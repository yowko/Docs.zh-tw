---
title: 變數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: af6d586a22f14a04bfc7ec339d0aa8e9ba7c66c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180994"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="b27d7-102">變數 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b27d7-102">Variables (Entity SQL)</span></span>

## <a name="variable"></a><span data-ttu-id="b27d7-103">變數</span><span class="sxs-lookup"><span data-stu-id="b27d7-103">Variable</span></span>  

 <span data-ttu-id="b27d7-104">變數運算式是目前範圍中所定義之具名運算式的參考。</span><span class="sxs-lookup"><span data-stu-id="b27d7-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="b27d7-105">變數參考必須是有效的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 識別碼，如 [識別碼](identifiers-entity-sql.md)中所定義。</span><span class="sxs-lookup"><span data-stu-id="b27d7-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="b27d7-106">下列範例示範如何在運算式中使用變數。</span><span class="sxs-lookup"><span data-stu-id="b27d7-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="b27d7-107">FROM 子句中的 `c` 是變數的定義。</span><span class="sxs-lookup"><span data-stu-id="b27d7-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="b27d7-108">SELECT 子句中的 `c` 使用代表變數參考。</span><span class="sxs-lookup"><span data-stu-id="b27d7-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="b27d7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b27d7-109">See also</span></span>

- [<span data-ttu-id="b27d7-110">識別碼</span><span class="sxs-lookup"><span data-stu-id="b27d7-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="b27d7-111">參數</span><span class="sxs-lookup"><span data-stu-id="b27d7-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="b27d7-112">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="b27d7-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
