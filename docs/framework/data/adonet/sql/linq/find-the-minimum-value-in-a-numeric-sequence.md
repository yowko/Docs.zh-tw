---
title: 尋找數值序列中的最小值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: d8aee43f13ec92f649b4df20505ac56c336fe07a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793842"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="2a9ac-102">尋找數值序列中的最小值</span><span class="sxs-lookup"><span data-stu-id="2a9ac-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="2a9ac-103">使用 <xref:System.Linq.Enumerable.Min%2A> 運算子可傳回數值序列中的最小值。</span><span class="sxs-lookup"><span data-stu-id="2a9ac-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a9ac-104">範例</span><span class="sxs-lookup"><span data-stu-id="2a9ac-104">Example</span></span>  
 <span data-ttu-id="2a9ac-105">下列範例會尋找任何產品的最低單價。</span><span class="sxs-lookup"><span data-stu-id="2a9ac-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="2a9ac-106">如果您對 Northwind 範例資料庫執行這個查詢，則輸出為：`2.5000`。</span><span class="sxs-lookup"><span data-stu-id="2a9ac-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="2a9ac-107">範例</span><span class="sxs-lookup"><span data-stu-id="2a9ac-107">Example</span></span>  
 <span data-ttu-id="2a9ac-108">下列範例會尋找任何訂單的最低運費金額。</span><span class="sxs-lookup"><span data-stu-id="2a9ac-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="2a9ac-109">如果您對 Northwind 範例資料庫執行這個查詢，則輸出為：`0.0200`。</span><span class="sxs-lookup"><span data-stu-id="2a9ac-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="2a9ac-110">範例</span><span class="sxs-lookup"><span data-stu-id="2a9ac-110">Example</span></span>  
 <span data-ttu-id="2a9ac-111">下列範例會使用 Min 來尋找各分類中具有最低單價的 `Products`。</span><span class="sxs-lookup"><span data-stu-id="2a9ac-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="2a9ac-112">輸出會按照分類排列。</span><span class="sxs-lookup"><span data-stu-id="2a9ac-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="2a9ac-113">如果您對 Northwind 範例資料庫執行前一個查詢，則結果會類似下列：</span><span class="sxs-lookup"><span data-stu-id="2a9ac-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="2a9ac-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a9ac-114">See also</span></span>

- [<span data-ttu-id="2a9ac-115">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="2a9ac-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="2a9ac-116">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="2a9ac-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
