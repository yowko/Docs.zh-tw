---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 0bcd4a2140a04fa0ecbfa7eee450ed029f278286
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319210"
---
# <a name="using-entity-sql"></a><span data-ttu-id="63e69-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="63e69-102">USING (Entity SQL)</span></span>
<span data-ttu-id="63e69-103">指定查詢運算式中使用的命名空間 (Namespace)。</span><span class="sxs-lookup"><span data-stu-id="63e69-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63e69-104">語法</span><span class="sxs-lookup"><span data-stu-id="63e69-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="63e69-105">引數</span><span class="sxs-lookup"><span data-stu-id="63e69-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="63e69-106">指定較短的別名 (Alias)，以便限定命名空間。</span><span class="sxs-lookup"><span data-stu-id="63e69-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="63e69-107">任何有效的命名空間。</span><span class="sxs-lookup"><span data-stu-id="63e69-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63e69-108">範例</span><span class="sxs-lookup"><span data-stu-id="63e69-108">Example</span></span>  
 <span data-ttu-id="63e69-109">下列 Entity SQL 查詢會使用 USING 運算子來指定查詢運算式中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="63e69-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="63e69-110">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="63e69-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="63e69-111">依照[如何：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式進行。</span><span class="sxs-lookup"><span data-stu-id="63e69-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="63e69-112">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="63e69-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="63e69-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="63e69-113">See also</span></span>

- [<span data-ttu-id="63e69-114">命名空間</span><span class="sxs-lookup"><span data-stu-id="63e69-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="63e69-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="63e69-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
