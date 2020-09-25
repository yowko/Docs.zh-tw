---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 1907b8786622d3c8019c75916f997c830cc07cfb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180955"
---
# <a name="where-entity-sql"></a><span data-ttu-id="9f9c3-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9f9c3-102">WHERE (Entity SQL)</span></span>

<span data-ttu-id="9f9c3-103">WHERE 子句會直接套用於 [from](from-entity-sql.md) 子句之後。</span><span class="sxs-lookup"><span data-stu-id="9f9c3-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f9c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f9c3-104">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f9c3-105">引數</span><span class="sxs-lookup"><span data-stu-id="9f9c3-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="9f9c3-106">布林型別。</span><span class="sxs-lookup"><span data-stu-id="9f9c3-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f9c3-107">備註</span><span class="sxs-lookup"><span data-stu-id="9f9c3-107">Remarks</span></span>  

 <span data-ttu-id="9f9c3-108">WHERE 子句具有與 Transact-sql 所述相同的語義。</span><span class="sxs-lookup"><span data-stu-id="9f9c3-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="9f9c3-109">它會將來源集合的項目限制為能通過此條件者，利用這種方式來限制查詢運算式產生的物件。</span><span class="sxs-lookup"><span data-stu-id="9f9c3-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="9f9c3-110">運算式 `e` 必須為布林型別。</span><span class="sxs-lookup"><span data-stu-id="9f9c3-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="9f9c3-111">WHERE 子句是直接套用在 FROM 子句之後，且在任何群組、排序或投影發生之前。</span><span class="sxs-lookup"><span data-stu-id="9f9c3-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="9f9c3-112">WHERE 子句的運算式可以看到 FROM 子句中定義的所有項目名稱。</span><span class="sxs-lookup"><span data-stu-id="9f9c3-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f9c3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f9c3-113">See also</span></span>

- [<span data-ttu-id="9f9c3-114">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9f9c3-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="9f9c3-115">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="9f9c3-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
