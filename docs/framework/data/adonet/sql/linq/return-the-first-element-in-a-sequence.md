---
title: 傳回序列的第一個項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 39cf9270b08fce64590fef418bb428c5a781b0e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963802"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="c6ff7-102">傳回序列的第一個項目</span><span class="sxs-lookup"><span data-stu-id="c6ff7-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="c6ff7-103">使用 <xref:System.Linq.Enumerable.First%2A> 運算子傳回序列中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="c6ff7-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="c6ff7-104">使用 <xref:System.Linq.Enumerable.First%2A> 的查詢會立即執行。</span><span class="sxs-lookup"><span data-stu-id="c6ff7-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c6ff7-105">不支援 <xref:System.Linq.Enumerable.Last%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="c6ff7-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6ff7-106">範例</span><span class="sxs-lookup"><span data-stu-id="c6ff7-106">Example</span></span>  
 <span data-ttu-id="c6ff7-107">下列程式碼會尋找資料表中的第一個 `Shipper`：</span><span class="sxs-lookup"><span data-stu-id="c6ff7-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="c6ff7-108">如果您對 Northwind 範例資料庫執行這個查詢，則結果為：</span><span class="sxs-lookup"><span data-stu-id="c6ff7-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="c6ff7-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="c6ff7-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="c6ff7-110">範例</span><span class="sxs-lookup"><span data-stu-id="c6ff7-110">Example</span></span>  
 <span data-ttu-id="c6ff7-111">下列程式碼會尋找具有 `Customer` BONAP 的單一 `CustomerID`。</span><span class="sxs-lookup"><span data-stu-id="c6ff7-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="c6ff7-112">如果您對 Northwind 範例資料庫執行這個查詢，則結果為 `ID = BONAP, Contact = Laurence Lebihan`。</span><span class="sxs-lookup"><span data-stu-id="c6ff7-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="c6ff7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6ff7-113">See also</span></span>

- [<span data-ttu-id="c6ff7-114">查詢範例</span><span class="sxs-lookup"><span data-stu-id="c6ff7-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="c6ff7-115">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="c6ff7-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
