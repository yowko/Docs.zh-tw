---
title: 在序列中排序項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 59384900226fbbcfc879650402b1a5df80b69cd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596419"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="67935-102">在序列中排序項目</span><span class="sxs-lookup"><span data-stu-id="67935-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="67935-103">使用 <xref:System.Linq.Enumerable.OrderBy%2A> 運算子，可以根據一個或多個索引鍵來排序序列。</span><span class="sxs-lookup"><span data-stu-id="67935-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="67935-104">設計來支援依據簡單的基本類型，例如排序`string`， `int`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="67935-104">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="67935-105">但不支援複雜多重值類別 (如匿名型別) 的排序，</span><span class="sxs-lookup"><span data-stu-id="67935-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="67935-106">也不支援 `byte` 資料型別。</span><span class="sxs-lookup"><span data-stu-id="67935-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67935-107">範例</span><span class="sxs-lookup"><span data-stu-id="67935-107">Example</span></span>  
 <span data-ttu-id="67935-108">下列範例會根據雇用日期來排序 `Employees`。</span><span class="sxs-lookup"><span data-stu-id="67935-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="67935-109">範例</span><span class="sxs-lookup"><span data-stu-id="67935-109">Example</span></span>  
 <span data-ttu-id="67935-110">下列範例使用 `where`，根據運費來排序運送至 `Orders` 的 `London`。</span><span class="sxs-lookup"><span data-stu-id="67935-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="67935-111">範例</span><span class="sxs-lookup"><span data-stu-id="67935-111">Example</span></span>  
 <span data-ttu-id="67935-112">下列範例會根據單價，從最高到最低來排序 `Products`。</span><span class="sxs-lookup"><span data-stu-id="67935-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="67935-113">範例</span><span class="sxs-lookup"><span data-stu-id="67935-113">Example</span></span>  
 <span data-ttu-id="67935-114">下列範例使用複合 `OrderBy`，先根據城市再根據連絡人名稱來排序 `Customers`。</span><span class="sxs-lookup"><span data-stu-id="67935-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="67935-115">範例</span><span class="sxs-lookup"><span data-stu-id="67935-115">Example</span></span>  
 <span data-ttu-id="67935-116">下列範例先根據送貨國家 (地區) 再根據最高到最低的運費，來排序 `EmployeeID 1` 的訂單。</span><span class="sxs-lookup"><span data-stu-id="67935-116">The following example sorts Orders from `EmployeeID 1` by ship-to country, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="67935-117">範例</span><span class="sxs-lookup"><span data-stu-id="67935-117">Example</span></span>  
 <span data-ttu-id="67935-118">下列範例合併 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Max%2A> 和 <xref:System.Linq.Enumerable.GroupBy%2A> 運算子，尋找每個分類中單價最高的 `Products`，然後再根據分類 ID 來排序群組。</span><span class="sxs-lookup"><span data-stu-id="67935-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="67935-119">如果您對 Northwind 範例資料庫執行前一個查詢，則結果會類似下列：</span><span class="sxs-lookup"><span data-stu-id="67935-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67935-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67935-120">See also</span></span>
- [<span data-ttu-id="67935-121">查詢範例</span><span class="sxs-lookup"><span data-stu-id="67935-121">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="67935-122">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="67935-122">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
