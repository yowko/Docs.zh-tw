---
title: "比較運算式"
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
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ec850636433c0c7ed2c61f4f97ba578952cac21
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-expressions"></a><span data-ttu-id="325a4-102">比較運算式</span><span class="sxs-lookup"><span data-stu-id="325a4-102">Comparison Expressions</span></span>
<span data-ttu-id="325a4-103">比較運算式會檢查常數值、屬性值或方法結果是否等於、不等於、大於或小於另一個值。</span><span class="sxs-lookup"><span data-stu-id="325a4-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="325a4-104">如果特定比較對於 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 無效，將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="325a4-104">If a particular comparison is not valid for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], an exception will be thrown.</span></span> <span data-ttu-id="325a4-105">所有的比較 (隱含和明確) 都會要求所有元件在資料來源內都是可以比較的。</span><span class="sxs-lookup"><span data-stu-id="325a4-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="325a4-106">`Where` 子句中經常會使用比較運算式來限制查詢結果。</span><span class="sxs-lookup"><span data-stu-id="325a4-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="325a4-107">下列查詢運算式語法範例顯示一個查詢，此查詢會傳回銷售訂單號碼等於 "SO43663" 的結果：</span><span class="sxs-lookup"><span data-stu-id="325a4-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="325a4-108">下列以方法為基礎的查詢語法範例顯示一個查詢，此查詢會傳回銷售訂單號碼等於 "SO43663" 的結果：</span><span class="sxs-lookup"><span data-stu-id="325a4-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="325a4-109">下列查詢運算式語法範例顯示一個查詢，此查詢會傳回出貨日期等於 2001 七月 8 日的銷售訂單資訊：</span><span class="sxs-lookup"><span data-stu-id="325a4-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="325a4-110">下列以方法為基礎的查詢語法範例顯示一個查詢，此查詢會傳回出貨日期等於 2001 七月 8 日的銷售訂單資訊：</span><span class="sxs-lookup"><span data-stu-id="325a4-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="325a4-111">產生常數的運算式會在伺服器上轉換，而且不會嘗試執行本機評估。</span><span class="sxs-lookup"><span data-stu-id="325a4-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="325a4-112">以下列範例在 `Where` 子句中使用了產生常數的運算式。</span><span class="sxs-lookup"><span data-stu-id="325a4-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="325a4-113"> 不支援使用使用者類別當做常數。</span><span class="sxs-lookup"><span data-stu-id="325a4-113"> does not support using a user class as a constant.</span></span> <span data-ttu-id="325a4-114">但是，使用者類別上的屬性參考會視為常數，而且將會轉換成命令樹常數運算式，並在資料來源上執行。</span><span class="sxs-lookup"><span data-stu-id="325a4-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="325a4-115">不支援傳回常數運算式的方法。</span><span class="sxs-lookup"><span data-stu-id="325a4-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="325a4-116">下列範例包含 `Where` 子句中傳回常數的方法。</span><span class="sxs-lookup"><span data-stu-id="325a4-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="325a4-117">此範例將會在執行階段擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="325a4-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="325a4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="325a4-118">See Also</span></span>  
 [<span data-ttu-id="325a4-119">LINQ to Entities 查詢中的運算式</span><span class="sxs-lookup"><span data-stu-id="325a4-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
