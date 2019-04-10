---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: e14b7857a65898683939647c872c48d0b3fe458a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297859"
---
# <a name="using-entity-sql"></a><span data-ttu-id="1584b-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1584b-102">USING (Entity SQL)</span></span>
<span data-ttu-id="1584b-103">指定查詢運算式中使用的命名空間 (Namespace)。</span><span class="sxs-lookup"><span data-stu-id="1584b-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1584b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1584b-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="1584b-105">引數</span><span class="sxs-lookup"><span data-stu-id="1584b-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="1584b-106">指定較短的別名 (Alias)，以便限定命名空間。</span><span class="sxs-lookup"><span data-stu-id="1584b-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="1584b-107">任何有效的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1584b-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1584b-108">範例</span><span class="sxs-lookup"><span data-stu-id="1584b-108">Example</span></span>  
 <span data-ttu-id="1584b-109">下列 Entity SQL 查詢會使用 USING 運算子來指定查詢運算式中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1584b-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="1584b-110">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="1584b-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1584b-111">請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="1584b-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="1584b-112">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="1584b-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="1584b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1584b-113">See also</span></span>

- [<span data-ttu-id="1584b-114">命名空間</span><span class="sxs-lookup"><span data-stu-id="1584b-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [<span data-ttu-id="1584b-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="1584b-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
