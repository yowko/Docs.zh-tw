---
title: "變數 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 551b6d6feab6829c9a2f6f2e89e1918acf463411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="variables-entity-sql"></a><span data-ttu-id="8c2e3-102">變數 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8c2e3-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="8c2e3-103">變數</span><span class="sxs-lookup"><span data-stu-id="8c2e3-103">Variable</span></span>  
 <span data-ttu-id="8c2e3-104">變數運算式是目前範圍中所定義之具名運算式的參考。</span><span class="sxs-lookup"><span data-stu-id="8c2e3-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="8c2e3-105">變數的參考必須是有效[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別碼中所定義[識別碼](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8c2e3-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="8c2e3-106">下列範例示範如何在運算式中使用變數。</span><span class="sxs-lookup"><span data-stu-id="8c2e3-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="8c2e3-107">FROM 子句中的 `c` 是變數的定義。</span><span class="sxs-lookup"><span data-stu-id="8c2e3-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="8c2e3-108">SELECT 子句中的 `c` 使用代表變數參考。</span><span class="sxs-lookup"><span data-stu-id="8c2e3-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c2e3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c2e3-109">See Also</span></span>  
 [<span data-ttu-id="8c2e3-110">識別項</span><span class="sxs-lookup"><span data-stu-id="8c2e3-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="8c2e3-111">參數</span><span class="sxs-lookup"><span data-stu-id="8c2e3-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="8c2e3-112">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="8c2e3-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
