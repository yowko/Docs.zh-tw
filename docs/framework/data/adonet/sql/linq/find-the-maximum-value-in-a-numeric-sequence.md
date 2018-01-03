---
title: "尋找數值序列中的最大值"
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
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 387fe8db55da337b970bbac0e6e046b43433b482
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="4083c-102">尋找數值序列中的最大值</span><span class="sxs-lookup"><span data-stu-id="4083c-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="4083c-103">使用 <xref:System.Linq.Enumerable.Max%2A> 運算子可尋找數值序列中的最高值。</span><span class="sxs-lookup"><span data-stu-id="4083c-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4083c-104">範例</span><span class="sxs-lookup"><span data-stu-id="4083c-104">Example</span></span>  
 <span data-ttu-id="4083c-105">下列範例可尋找任何員工的最近雇用日期。</span><span class="sxs-lookup"><span data-stu-id="4083c-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="4083c-106">如果您對 Northwind 範例資料庫執行這個查詢，則輸出為：`11/15/1994 12:00:00 AM`。</span><span class="sxs-lookup"><span data-stu-id="4083c-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="4083c-107">範例</span><span class="sxs-lookup"><span data-stu-id="4083c-107">Example</span></span>  
 <span data-ttu-id="4083c-108">下列範例可尋找任何產品的最多庫存單位。</span><span class="sxs-lookup"><span data-stu-id="4083c-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="4083c-109">如果您對 Northwind 範例資料庫執行這個範例，則輸出為：`125`。</span><span class="sxs-lookup"><span data-stu-id="4083c-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="4083c-110">範例</span><span class="sxs-lookup"><span data-stu-id="4083c-110">Example</span></span>  
 <span data-ttu-id="4083c-111">下列範例會使用 Max 來尋找各分類中具有最高單價的 `Products`。</span><span class="sxs-lookup"><span data-stu-id="4083c-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="4083c-112">接著，輸出會依照分類列出結果。</span><span class="sxs-lookup"><span data-stu-id="4083c-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="4083c-113">如果您對 Northwind 範例資料庫執行前一個查詢，則結果會類似下列：</span><span class="sxs-lookup"><span data-stu-id="4083c-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="4083c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="4083c-114">See Also</span></span>  
 [<span data-ttu-id="4083c-115">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="4083c-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="4083c-116">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="4083c-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
