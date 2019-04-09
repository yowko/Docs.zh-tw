---
title: 制定聯結和交叉乘積查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: b0037f56947a86627ee9ea84369527aec859a0f8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180501"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="9793a-102">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="9793a-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="9793a-103">下列範例顯示如何合併多張資料表中的結果。</span><span class="sxs-lookup"><span data-stu-id="9793a-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9793a-104">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-104">Example</span></span>  
 <span data-ttu-id="9793a-105">下列範例會使用中的外部索引鍵巡覽`From`在 Visual Basic 中的子句 (`from`子句C#) 來選取在倫敦的客戶的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="9793a-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="9793a-106">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-106">Example</span></span>  
 <span data-ttu-id="9793a-107">下列範例會使用中的外部索引鍵巡覽`Where`在 Visual Basic 中的子句 (`where`子句中的C#) 來篩選出缺貨`Products`其`Supplier`是在美國境內。</span><span class="sxs-lookup"><span data-stu-id="9793a-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="9793a-108">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-108">Example</span></span>  
 <span data-ttu-id="9793a-109">下列範例會使用中的外部索引鍵巡覽`From`在 Visual Basic 中的子句 (`from`子句C#) 來篩選位於西雅圖的員工，並列出他們的領域。</span><span class="sxs-lookup"><span data-stu-id="9793a-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="9793a-110">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-110">Example</span></span>  
 <span data-ttu-id="9793a-111">下列範例會使用中的外部索引鍵巡覽`Select`在 Visual Basic 中的子句 (`select`子句C#) 來篩選員工配對，到另一位員工報告的位置，以及兩位員工的來自相同的位置`City`。</span><span class="sxs-lookup"><span data-stu-id="9793a-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="9793a-112">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-112">Example</span></span>  
 <span data-ttu-id="9793a-113">下列 Visual Basic 範例會尋找所有客戶和訂單、 可確保訂單會比對，為客戶和保證，該清單中每位客戶，提供連絡人的名稱。</span><span class="sxs-lookup"><span data-stu-id="9793a-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="9793a-114">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-114">Example</span></span>  
 <span data-ttu-id="9793a-115">下列範例明確聯結 (Join) 兩張資料表，並規劃來自這兩張資料表的結果。</span><span class="sxs-lookup"><span data-stu-id="9793a-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="9793a-116">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-116">Example</span></span>  
 <span data-ttu-id="9793a-117">下列範例明確聯結三張資料表，並規劃來自每張資料表的結果。</span><span class="sxs-lookup"><span data-stu-id="9793a-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="9793a-118">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-118">Example</span></span>  
 <span data-ttu-id="9793a-119">下列範例顯示如何使用 `LEFT OUTER JOIN` 來達成 `DefaultIfEmpty()`。</span><span class="sxs-lookup"><span data-stu-id="9793a-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="9793a-120">如果 `DefaultIfEmpty()` 沒有 `Order`，則 `Employee` 方法會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="9793a-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="9793a-121">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-121">Example</span></span>  
 <span data-ttu-id="9793a-122">下列範例會規劃透過聯結產生的 `let` 運算式。</span><span class="sxs-lookup"><span data-stu-id="9793a-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="9793a-123">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-123">Example</span></span>  
 <span data-ttu-id="9793a-124">下列範例顯示具有複合索引鍵的 `join`。</span><span class="sxs-lookup"><span data-stu-id="9793a-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="9793a-125">範例</span><span class="sxs-lookup"><span data-stu-id="9793a-125">Example</span></span>  
 <span data-ttu-id="9793a-126">下列範例顯示如何建構 `join`，其中另一端可以為 null，而另一端則不可以。</span><span class="sxs-lookup"><span data-stu-id="9793a-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="9793a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9793a-127">See also</span></span>

- [<span data-ttu-id="9793a-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="9793a-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
