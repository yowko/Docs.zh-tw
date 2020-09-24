---
title: 制定聯結和交叉乘積查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 1527ad26524dbef3ac73b92e136cd22e33046483
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155883"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="0af97-102">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="0af97-102">Formulate Joins and Cross-Product Queries</span></span>

<span data-ttu-id="0af97-103">下列範例顯示如何合併多張資料表中的結果。</span><span class="sxs-lookup"><span data-stu-id="0af97-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0af97-104">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-104">Example</span></span>  

 <span data-ttu-id="0af97-105">下列範例會在 c ) # 中使用 Visual Basic (子句之子句中的外鍵導覽， `From` `from` 以選取倫敦客戶的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="0af97-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="0af97-106">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-106">Example</span></span>  

 <span data-ttu-id="0af97-107">下列範例會在 c ) # 中使用 Visual Basic (子句之子句中的外鍵導覽， `Where` `where` 以篩選 `Products` `Supplier` 位於美國的缺貨。</span><span class="sxs-lookup"><span data-stu-id="0af97-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="0af97-108">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-108">Example</span></span>  

 <span data-ttu-id="0af97-109">下列範例會在 c ) # 中使用 Visual Basic (子句之子句中的外鍵導覽 `From` `from` ，以篩選西雅圖的員工並列出其區域。</span><span class="sxs-lookup"><span data-stu-id="0af97-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="0af97-110">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-110">Example</span></span>  

 <span data-ttu-id="0af97-111">下列範例會在 c ) # 中使用 Visual Basic (子句子句中的外鍵導覽， `Select` `select` 以篩選一位員工向另一位員工報告，而且兩位員工都來自相同的員工 `City` 。</span><span class="sxs-lookup"><span data-stu-id="0af97-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="0af97-112">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-112">Example</span></span>  

 <span data-ttu-id="0af97-113">下列 Visual Basic 範例會尋找所有客戶和訂單、確定訂單與客戶相符，並保證該清單中的每個客戶都提供連絡人名稱。</span><span class="sxs-lookup"><span data-stu-id="0af97-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="0af97-114">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-114">Example</span></span>  

 <span data-ttu-id="0af97-115">下列範例明確聯結 (Join) 兩張資料表，並規劃來自這兩張資料表的結果。</span><span class="sxs-lookup"><span data-stu-id="0af97-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="0af97-116">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-116">Example</span></span>  

 <span data-ttu-id="0af97-117">下列範例明確聯結三張資料表，並規劃來自每張資料表的結果。</span><span class="sxs-lookup"><span data-stu-id="0af97-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="0af97-118">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-118">Example</span></span>  

 <span data-ttu-id="0af97-119">下列範例顯示如何使用 `LEFT OUTER JOIN` 來達成 `DefaultIfEmpty()`。</span><span class="sxs-lookup"><span data-stu-id="0af97-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="0af97-120">如果 `DefaultIfEmpty()` 沒有 `Order`，則 `Employee` 方法會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="0af97-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="0af97-121">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-121">Example</span></span>  

 <span data-ttu-id="0af97-122">下列範例會規劃透過聯結產生的 `let` 運算式。</span><span class="sxs-lookup"><span data-stu-id="0af97-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="0af97-123">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-123">Example</span></span>  

 <span data-ttu-id="0af97-124">下列範例顯示具有複合索引鍵的 `join`。</span><span class="sxs-lookup"><span data-stu-id="0af97-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="0af97-125">範例</span><span class="sxs-lookup"><span data-stu-id="0af97-125">Example</span></span>  

 <span data-ttu-id="0af97-126">下列範例顯示如何建構 `join`，其中另一端可以為 null，而另一端則不可以。</span><span class="sxs-lookup"><span data-stu-id="0af97-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="0af97-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0af97-127">See also</span></span>

- [<span data-ttu-id="0af97-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="0af97-128">Query Examples</span></span>](query-examples.md)
