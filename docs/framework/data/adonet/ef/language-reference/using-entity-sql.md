---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: bdab81ed8acae5e757de0a669922dc79d0303ee4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203588"
---
# <a name="using-entity-sql"></a><span data-ttu-id="fe625-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fe625-102">USING (Entity SQL)</span></span>

<span data-ttu-id="fe625-103">指定查詢運算式中使用的命名空間 (Namespace)。</span><span class="sxs-lookup"><span data-stu-id="fe625-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe625-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe625-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="fe625-105">引數</span><span class="sxs-lookup"><span data-stu-id="fe625-105">Arguments</span></span>  

 `alias`  
 <span data-ttu-id="fe625-106">指定較短的別名 (Alias)，以便限定命名空間。</span><span class="sxs-lookup"><span data-stu-id="fe625-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="fe625-107">任何有效的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fe625-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe625-108">範例</span><span class="sxs-lookup"><span data-stu-id="fe625-108">Example</span></span>  

 <span data-ttu-id="fe625-109">下列 Entity SQL 查詢會使用 USING 運算子來指定查詢運算式中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fe625-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="fe625-110">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="fe625-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fe625-111">依照 how [to：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式操作。</span><span class="sxs-lookup"><span data-stu-id="fe625-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="fe625-112">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="fe625-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe625-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe625-113">See also</span></span>

- [<span data-ttu-id="fe625-114">命名空間</span><span class="sxs-lookup"><span data-stu-id="fe625-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="fe625-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="fe625-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
