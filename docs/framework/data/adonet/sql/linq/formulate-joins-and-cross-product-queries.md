---
title: 制定聯結和交叉乘積查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 002a644ff5d48b25351228dcd74330707491d6c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782089"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="d4b9e-102">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="d4b9e-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="d4b9e-103">下列範例顯示如何合併多張資料表中的結果。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4b9e-104">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-104">Example</span></span>  
 <span data-ttu-id="d4b9e-105">下列範例會在的 Visual Basic （ `From` `from`子句C#）中使用子句中的外鍵導覽，以選取倫敦客戶的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-106">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-106">Example</span></span>  
 <span data-ttu-id="d4b9e-107">`Where`下列範例`Supplier`會在的 Visual Basic （`where`子句C#）中使用子句中的外鍵導覽，以篩選位於美國的缺貨`Products` 。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-108">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-108">Example</span></span>  
 <span data-ttu-id="d4b9e-109">下列範例會在中 Visual Basic （ `From` `from`子句C#）中的子句內使用外鍵導覽，以篩選西雅圖的員工並列出其地區。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-110">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-110">Example</span></span>  
 <span data-ttu-id="d4b9e-111">下列範例會`Select`在的 Visual Basic （`select`子句C#）中使用子句中的外鍵導覽，篩選一位員工向另一個員工報告的員工，以及兩個員工是否來自相同`City`的。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-112">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-112">Example</span></span>  
 <span data-ttu-id="d4b9e-113">下列 Visual Basic 範例會尋找所有客戶和訂單、確定訂單與客戶相符，並保證會針對該清單中的每位客戶提供連絡人名稱。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-114">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-114">Example</span></span>  
 <span data-ttu-id="d4b9e-115">下列範例明確聯結 (Join) 兩張資料表，並規劃來自這兩張資料表的結果。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-116">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-116">Example</span></span>  
 <span data-ttu-id="d4b9e-117">下列範例明確聯結三張資料表，並規劃來自每張資料表的結果。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-118">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-118">Example</span></span>  
 <span data-ttu-id="d4b9e-119">下列範例顯示如何使用 `LEFT OUTER JOIN` 來達成 `DefaultIfEmpty()`。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="d4b9e-120">如果 `DefaultIfEmpty()` 沒有 `Order`，則 `Employee` 方法會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-121">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-121">Example</span></span>  
 <span data-ttu-id="d4b9e-122">下列範例會規劃透過聯結產生的 `let` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-123">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-123">Example</span></span>  
 <span data-ttu-id="d4b9e-124">下列範例顯示具有複合索引鍵的 `join`。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="d4b9e-125">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-125">Example</span></span>  
 <span data-ttu-id="d4b9e-126">下列範例顯示如何建構 `join`，其中另一端可以為 null，而另一端則不可以。</span><span class="sxs-lookup"><span data-stu-id="d4b9e-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="d4b9e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4b9e-127">See also</span></span>

- [<span data-ttu-id="d4b9e-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="d4b9e-128">Query Examples</span></span>](query-examples.md)
