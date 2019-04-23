---
title: 常數運算式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 10c74ede8d490bf96a9d0855889669bdc2628b01
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209199"
---
# <a name="constant-expressions"></a><span data-ttu-id="5df91-102">常數運算式</span><span class="sxs-lookup"><span data-stu-id="5df91-102">Constant Expressions</span></span>
<span data-ttu-id="5df91-103">常數運算式是由常數值所組成。</span><span class="sxs-lookup"><span data-stu-id="5df91-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="5df91-104">常數值會直接轉換成常數命令樹運算式，而不需在用戶端上進行任何轉譯。</span><span class="sxs-lookup"><span data-stu-id="5df91-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="5df91-105">其中包括產生常數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="5df91-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="5df91-106">因此，所有牽涉到常數的運算式應該都會有資料來源行為。</span><span class="sxs-lookup"><span data-stu-id="5df91-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="5df91-107">這樣可能會產生與 CLR 行為不同的行為。</span><span class="sxs-lookup"><span data-stu-id="5df91-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="5df91-108">下列範例會顯示在伺服器上評估的常數運算式。</span><span class="sxs-lookup"><span data-stu-id="5df91-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] <span data-ttu-id="5df91-109">不支援使用使用者類別當做常數。</span><span class="sxs-lookup"><span data-stu-id="5df91-109">does not support using a user class as a constant.</span></span> <span data-ttu-id="5df91-110">但是，使用者類別上的屬性參考會視為常數，而且將會轉換成命令樹常數運算式，並在資料來源上執行。</span><span class="sxs-lookup"><span data-stu-id="5df91-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df91-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5df91-111">See also</span></span>

- [<span data-ttu-id="5df91-112">LINQ to Entities 查詢中的運算式</span><span class="sxs-lookup"><span data-stu-id="5df91-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
