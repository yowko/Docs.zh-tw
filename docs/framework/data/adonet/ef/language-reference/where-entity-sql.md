---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 0b9cf9bdb211a74acd8fc229c53f3565b48e5ddd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670572"
---
# <a name="where-entity-sql"></a><span data-ttu-id="6dbb0-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6dbb0-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="6dbb0-103">直接之後套用 WHERE 子句[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)子句。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dbb0-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dbb0-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6dbb0-105">引數</span><span class="sxs-lookup"><span data-stu-id="6dbb0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6dbb0-106">布林型別。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dbb0-107">備註</span><span class="sxs-lookup"><span data-stu-id="6dbb0-107">Remarks</span></span>  
 <span data-ttu-id="6dbb0-108">WHERE 子句的語意與針對 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 所述者相同。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6dbb0-109">它會將來源集合的項目限制為能通過此條件者，利用這種方式來限制查詢運算式產生的物件。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="6dbb0-110">運算式 `e` 必須為布林型別。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="6dbb0-111">WHERE 子句是直接套用在 FROM 子句之後，且在任何群組、排序或投影發生之前。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="6dbb0-112">WHERE 子句的運算式可以看到 FROM 子句中定義的所有項目名稱。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbb0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dbb0-113">See also</span></span>
- [<span data-ttu-id="6dbb0-114">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="6dbb0-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="6dbb0-115">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="6dbb0-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
