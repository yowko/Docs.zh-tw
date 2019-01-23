---
title: 在 LINQ to Entities 查詢中呼叫函式
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 012f55113cbea00c95c92712d640313a960ef8ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542714"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="2bec7-102">在 LINQ to Entities 查詢中呼叫函式</span><span class="sxs-lookup"><span data-stu-id="2bec7-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="2bec7-103">本章節的主題描述如何使用呼叫 LINQ to Entities 查詢中的函式。</span><span class="sxs-lookup"><span data-stu-id="2bec7-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="2bec7-104"><xref:System.Data.Objects.EntityFunctions> 與 <xref:System.Data.Objects.SqlClient.SqlFunctions> 類別可讓您存取標準函式與資料庫函式，這些函式是 Entity Framework 的一部分。</span><span class="sxs-lookup"><span data-stu-id="2bec7-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="2bec7-105">如需詳細資訊，請參閱[＜How to：呼叫標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)和[How to:呼叫資料庫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="2bec7-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="2bec7-106">呼叫自訂函式的程序需要三個基本步驟：</span><span class="sxs-lookup"><span data-stu-id="2bec7-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="2bec7-107">定義概念模型中的函式或宣告儲存模型中的函式。</span><span class="sxs-lookup"><span data-stu-id="2bec7-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="2bec7-108">使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 將方法加入至應用程式，並將它對應至模型中的函式。</span><span class="sxs-lookup"><span data-stu-id="2bec7-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="2bec7-109">呼叫 LINQ to Entities 查詢中的函式。</span><span class="sxs-lookup"><span data-stu-id="2bec7-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="2bec7-110">如需詳細資料，請參閱本節中的主題。</span><span class="sxs-lookup"><span data-stu-id="2bec7-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bec7-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="2bec7-111">In This Section</span></span>  
 [<span data-ttu-id="2bec7-112">如何：呼叫標準函式</span><span class="sxs-lookup"><span data-stu-id="2bec7-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="2bec7-113">如何：呼叫資料庫函式</span><span class="sxs-lookup"><span data-stu-id="2bec7-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="2bec7-114">如何：呼叫自訂資料庫函式</span><span class="sxs-lookup"><span data-stu-id="2bec7-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="2bec7-115">如何：在查詢中呼叫模型定義函式</span><span class="sxs-lookup"><span data-stu-id="2bec7-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="2bec7-116">如何：呼叫模型定義函式當做物件方法</span><span class="sxs-lookup"><span data-stu-id="2bec7-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="2bec7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bec7-117">See also</span></span>
- [<span data-ttu-id="2bec7-118">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="2bec7-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [<span data-ttu-id="2bec7-119">標準函式</span><span class="sxs-lookup"><span data-stu-id="2bec7-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
- [<span data-ttu-id="2bec7-120">.edmx 檔案概觀</span><span class="sxs-lookup"><span data-stu-id="2bec7-120">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)
- [<span data-ttu-id="2bec7-121">如何：概念模型中定義自訂函式</span><span class="sxs-lookup"><span data-stu-id="2bec7-121">How to: Define Custom Functions in the Conceptual Model</span></span>](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
