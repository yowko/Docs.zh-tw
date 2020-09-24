---
title: 計算序列中的項目數目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: d983bc14f4fda04bda0a6f363db4c11f062c4c48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164346"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="4a403-102">計算序列中的項目數目</span><span class="sxs-lookup"><span data-stu-id="4a403-102">Count the Number of Elements in a Sequence</span></span>

<span data-ttu-id="4a403-103">使用 <xref:System.Linq.Enumerable.Count%2A> 運算子計算序列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="4a403-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="4a403-104">如果對 Northwind 範例資料庫執行這個查詢，會產生輸出 `91`。</span><span class="sxs-lookup"><span data-stu-id="4a403-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a403-105">範例</span><span class="sxs-lookup"><span data-stu-id="4a403-105">Example</span></span>  

 <span data-ttu-id="4a403-106">下列範例會計算資料庫中的 `Customers` 數目。</span><span class="sxs-lookup"><span data-stu-id="4a403-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="4a403-107">範例</span><span class="sxs-lookup"><span data-stu-id="4a403-107">Example</span></span>  

 <span data-ttu-id="4a403-108">下列範例計算資料庫中未停產的產品項目。</span><span class="sxs-lookup"><span data-stu-id="4a403-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="4a403-109">如果對 Northwind 範例資料庫執行這個範例，會產生輸出 `69`。</span><span class="sxs-lookup"><span data-stu-id="4a403-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4a403-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a403-110">See also</span></span>

- [<span data-ttu-id="4a403-111">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="4a403-111">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="4a403-112">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="4a403-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
