---
title: 計算序列中的項目數目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 74e24aeb64b0097cba3975e76475034e6bb9544d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247696"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="009af-102">計算序列中的項目數目</span><span class="sxs-lookup"><span data-stu-id="009af-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="009af-103">使用 <xref:System.Linq.Enumerable.Count%2A> 運算子計算序列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="009af-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="009af-104">如果對 Northwind 範例資料庫執行這個查詢，會產生輸出 `91`。</span><span class="sxs-lookup"><span data-stu-id="009af-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="009af-105">範例</span><span class="sxs-lookup"><span data-stu-id="009af-105">Example</span></span>  
 <span data-ttu-id="009af-106">下列範例會計算資料庫中的 `Customers` 數目。</span><span class="sxs-lookup"><span data-stu-id="009af-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="009af-107">範例</span><span class="sxs-lookup"><span data-stu-id="009af-107">Example</span></span>  
 <span data-ttu-id="009af-108">下列範例計算資料庫中未停產的產品項目。</span><span class="sxs-lookup"><span data-stu-id="009af-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="009af-109">如果對 Northwind 範例資料庫執行這個範例，會產生輸出 `69`。</span><span class="sxs-lookup"><span data-stu-id="009af-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="009af-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="009af-110">See also</span></span>

- [<span data-ttu-id="009af-111">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="009af-111">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="009af-112">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="009af-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
