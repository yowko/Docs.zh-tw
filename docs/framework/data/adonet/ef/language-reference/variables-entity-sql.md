---
title: 變數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bf6fa95e38d1eb5817fd67165b6993cbb0755fd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153578"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="89b6a-102">變數 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="89b6a-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="89b6a-103">變數</span><span class="sxs-lookup"><span data-stu-id="89b6a-103">Variable</span></span>  
 <span data-ttu-id="89b6a-104">變數運算式是目前範圍中所定義之具名運算式的參考。</span><span class="sxs-lookup"><span data-stu-id="89b6a-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="89b6a-105">變數參考必須是有效[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別碼，如同[識別碼](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="89b6a-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="89b6a-106">下列範例示範如何在運算式中使用變數。</span><span class="sxs-lookup"><span data-stu-id="89b6a-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="89b6a-107">FROM 子句中的 `c` 是變數的定義。</span><span class="sxs-lookup"><span data-stu-id="89b6a-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="89b6a-108">SELECT 子句中的 `c` 使用代表變數參考。</span><span class="sxs-lookup"><span data-stu-id="89b6a-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="89b6a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89b6a-109">See also</span></span>

- [<span data-ttu-id="89b6a-110">識別項</span><span class="sxs-lookup"><span data-stu-id="89b6a-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [<span data-ttu-id="89b6a-111">參數</span><span class="sxs-lookup"><span data-stu-id="89b6a-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [<span data-ttu-id="89b6a-112">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="89b6a-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
