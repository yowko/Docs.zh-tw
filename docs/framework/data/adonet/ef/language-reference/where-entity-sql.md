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
ms.openlocfilehash: 38d1b7e2b7662ef3b2fedbcce6ac23ce55a5468f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="where-entity-sql"></a><span data-ttu-id="039fc-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="039fc-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="039fc-103">WHERE 子句直接之後套用[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)子句。</span><span class="sxs-lookup"><span data-stu-id="039fc-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="039fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="039fc-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="039fc-105">引數</span><span class="sxs-lookup"><span data-stu-id="039fc-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="039fc-106">布林型別。</span><span class="sxs-lookup"><span data-stu-id="039fc-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="039fc-107">備註</span><span class="sxs-lookup"><span data-stu-id="039fc-107">Remarks</span></span>  
 <span data-ttu-id="039fc-108">WHERE 子句的語意與針對 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 所述者相同。</span><span class="sxs-lookup"><span data-stu-id="039fc-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="039fc-109">它會將來源集合的項目限制為能通過此條件者，利用這種方式來限制查詢運算式產生的物件。</span><span class="sxs-lookup"><span data-stu-id="039fc-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="039fc-110">運算式 `e` 必須為布林型別。</span><span class="sxs-lookup"><span data-stu-id="039fc-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="039fc-111">WHERE 子句是直接套用在 FROM 子句之後，且在任何群組、排序或投影發生之前。</span><span class="sxs-lookup"><span data-stu-id="039fc-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="039fc-112">WHERE 子句的運算式可以看到 FROM 子句中定義的所有項目名稱。</span><span class="sxs-lookup"><span data-stu-id="039fc-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039fc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="039fc-113">See Also</span></span>  
 [<span data-ttu-id="039fc-114">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="039fc-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="039fc-115">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="039fc-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
