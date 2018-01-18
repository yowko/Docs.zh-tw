---
title: "制定聯結和交叉乘積查詢"
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
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f652f25d04480afb3df1f623347eee23d3ed258
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="c0f67-102">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="c0f67-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="c0f67-103">下列範例顯示如何合併多張資料表中的結果。</span><span class="sxs-lookup"><span data-stu-id="c0f67-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0f67-104">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-104">Example</span></span>  
 <span data-ttu-id="c0f67-105">下列範例會使用中的外部索引鍵巡覽`From`中的子句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`from`子句在 C# 中的) 來選取在倫敦 （london） 的所有客戶的訂單。</span><span class="sxs-lookup"><span data-stu-id="c0f67-105">The following example uses foreign key navigation in the `From` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-106">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-106">Example</span></span>  
 <span data-ttu-id="c0f67-107">下列範例會使用中的外部索引鍵巡覽`Where`子句中的[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`where`子句在 C# 中的) 來篩選出內建`Products`其`Supplier`位於美國。</span><span class="sxs-lookup"><span data-stu-id="c0f67-107">The following example uses foreign key navigation in the `Where` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-108">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-108">Example</span></span>  
 <span data-ttu-id="c0f67-109">下列範例在 `From` 的 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 子句 (在 C# 中是 `from` 子句) 中使用外部索引鍵巡覽，篩選位於西雅圖的員工並列出他們的領域。</span><span class="sxs-lookup"><span data-stu-id="c0f67-109">The following example uses foreign key navigation in the `From` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-110">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-110">Example</span></span>  
 <span data-ttu-id="c0f67-111">下列範例會使用中的外部索引鍵巡覽`Select`中的子句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`子句在 C# 中的) 來篩選員工配對，其中一位員工報告其他而且其中兩位員工都是來自相同`City`。</span><span class="sxs-lookup"><span data-stu-id="c0f67-111">The following example uses foreign key navigation in the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-112">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-112">Example</span></span>  
 <span data-ttu-id="c0f67-113">下列[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]範例會尋找所有客戶和訂單、 可確保訂單會對應到客戶，並確保該清單中每個客戶，都提供有連絡人名稱。</span><span class="sxs-lookup"><span data-stu-id="c0f67-113">The following [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-114">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-114">Example</span></span>  
 <span data-ttu-id="c0f67-115">下列範例明確聯結 (Join) 兩張資料表，並規劃來自這兩張資料表的結果。</span><span class="sxs-lookup"><span data-stu-id="c0f67-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-116">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-116">Example</span></span>  
 <span data-ttu-id="c0f67-117">下列範例明確聯結三張資料表，並規劃來自每張資料表的結果。</span><span class="sxs-lookup"><span data-stu-id="c0f67-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-118">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-118">Example</span></span>  
 <span data-ttu-id="c0f67-119">下列範例顯示如何使用 `LEFT OUTER JOIN` 來達成 `DefaultIfEmpty()`。</span><span class="sxs-lookup"><span data-stu-id="c0f67-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="c0f67-120">如果 `DefaultIfEmpty()` 沒有 `Order`，則 `Employee` 方法會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="c0f67-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-121">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-121">Example</span></span>  
 <span data-ttu-id="c0f67-122">下列範例會規劃透過聯結產生的 `let` 運算式。</span><span class="sxs-lookup"><span data-stu-id="c0f67-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-123">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-123">Example</span></span>  
 <span data-ttu-id="c0f67-124">下列範例顯示具有複合索引鍵的 `join`。</span><span class="sxs-lookup"><span data-stu-id="c0f67-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="c0f67-125">範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-125">Example</span></span>  
 <span data-ttu-id="c0f67-126">下列範例顯示如何建構 `join`，其中另一端可以為 null，而另一端則不可以。</span><span class="sxs-lookup"><span data-stu-id="c0f67-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="c0f67-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f67-127">See Also</span></span>  
 [<span data-ttu-id="c0f67-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="c0f67-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
