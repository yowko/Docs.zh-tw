---
title: WHERE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2ad170500770bc370eb67a04ab29d0c9f9dcaabd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="where-entity-sql"></a><span data-ttu-id="fe87f-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fe87f-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="fe87f-103">WHERE 子句直接之後套用[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)子句。</span><span class="sxs-lookup"><span data-stu-id="fe87f-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe87f-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe87f-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fe87f-105">引數</span><span class="sxs-lookup"><span data-stu-id="fe87f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fe87f-106">布林型別。</span><span class="sxs-lookup"><span data-stu-id="fe87f-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe87f-107">備註</span><span class="sxs-lookup"><span data-stu-id="fe87f-107">Remarks</span></span>  
 <span data-ttu-id="fe87f-108">WHERE 子句的語意與針對 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 所述者相同。</span><span class="sxs-lookup"><span data-stu-id="fe87f-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fe87f-109">它會將來源集合的項目限制為能通過此條件者，利用這種方式來限制查詢運算式產生的物件。</span><span class="sxs-lookup"><span data-stu-id="fe87f-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="fe87f-110">運算式 `e` 必須為布林型別。</span><span class="sxs-lookup"><span data-stu-id="fe87f-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="fe87f-111">WHERE 子句是直接套用在 FROM 子句之後，且在任何群組、排序或投影發生之前。</span><span class="sxs-lookup"><span data-stu-id="fe87f-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="fe87f-112">WHERE 子句的運算式可以看到 FROM 子句中定義的所有項目名稱。</span><span class="sxs-lookup"><span data-stu-id="fe87f-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe87f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe87f-113">See Also</span></span>  
 [<span data-ttu-id="fe87f-114">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="fe87f-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="fe87f-115">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="fe87f-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
