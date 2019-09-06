---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 9495e5daf88326c5a682172d835c3349fe79e571
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248752"
---
# <a name="using-entity-sql"></a><span data-ttu-id="4b689-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4b689-102">USING (Entity SQL)</span></span>
<span data-ttu-id="4b689-103">指定查詢運算式中使用的命名空間 (Namespace)。</span><span class="sxs-lookup"><span data-stu-id="4b689-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b689-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b689-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b689-105">引數</span><span class="sxs-lookup"><span data-stu-id="4b689-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="4b689-106">指定較短的別名 (Alias)，以便限定命名空間。</span><span class="sxs-lookup"><span data-stu-id="4b689-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="4b689-107">任何有效的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4b689-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b689-108">範例</span><span class="sxs-lookup"><span data-stu-id="4b689-108">Example</span></span>  
 <span data-ttu-id="4b689-109">下列 Entity SQL 查詢會使用 USING 運算子來指定查詢運算式中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4b689-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="4b689-110">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="4b689-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4b689-111">[遵循 how to：執行可傳回 PrimitiveType 結果](../how-to-execute-a-query-that-returns-primitivetype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="4b689-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="4b689-112">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="4b689-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b689-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b689-113">See also</span></span>

- [<span data-ttu-id="4b689-114">命名空間</span><span class="sxs-lookup"><span data-stu-id="4b689-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="4b689-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="4b689-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
