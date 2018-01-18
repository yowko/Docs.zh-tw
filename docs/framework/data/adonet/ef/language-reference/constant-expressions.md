---
title: "常數運算式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 328284ce07a0361dbfd25b0d765000b497156ff7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="constant-expressions"></a><span data-ttu-id="9130b-102">常數運算式</span><span class="sxs-lookup"><span data-stu-id="9130b-102">Constant Expressions</span></span>
<span data-ttu-id="9130b-103">常數運算式是由常數值所組成。</span><span class="sxs-lookup"><span data-stu-id="9130b-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="9130b-104">常數值會直接轉換成常數命令樹運算式，而不需在用戶端上進行任何轉譯。</span><span class="sxs-lookup"><span data-stu-id="9130b-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="9130b-105">其中包括產生常數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="9130b-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="9130b-106">因此，所有牽涉到常數的運算式應該都會有資料來源行為。</span><span class="sxs-lookup"><span data-stu-id="9130b-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="9130b-107">這樣可能會產生與 CLR 行為不同的行為。</span><span class="sxs-lookup"><span data-stu-id="9130b-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="9130b-108">下列範例會顯示在伺服器上評估的常數運算式。</span><span class="sxs-lookup"><span data-stu-id="9130b-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="9130b-109"> 不支援使用使用者類別當做常數。</span><span class="sxs-lookup"><span data-stu-id="9130b-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="9130b-110">但是，使用者類別上的屬性參考會視為常數，而且將會轉換成命令樹常數運算式，並在資料來源上執行。</span><span class="sxs-lookup"><span data-stu-id="9130b-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9130b-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="9130b-111">See Also</span></span>  
 [<span data-ttu-id="9130b-112">LINQ to Entities 查詢中的運算式</span><span class="sxs-lookup"><span data-stu-id="9130b-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
