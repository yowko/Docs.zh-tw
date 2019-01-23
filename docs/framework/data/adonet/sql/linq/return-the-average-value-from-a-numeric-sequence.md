---
title: 傳回數值序列的平均值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 38b1b3ba2bd2116621de820855bb4e4b2cd12915
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519151"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="76d35-102">傳回數值序列的平均值</span><span class="sxs-lookup"><span data-stu-id="76d35-102">Return the Average Value From a Numeric Sequence</span></span>
<span data-ttu-id="76d35-103"><xref:System.Linq.Enumerable.Average%2A> 運算子會計算數值序列的平均值。</span><span class="sxs-lookup"><span data-stu-id="76d35-103">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76d35-104">整數值 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 `Average` 轉譯會計算為整數，而不是雙精度浮點數 (Double)。</span><span class="sxs-lookup"><span data-stu-id="76d35-104">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76d35-105">範例</span><span class="sxs-lookup"><span data-stu-id="76d35-105">Example</span></span>  
 <span data-ttu-id="76d35-106">下列範例會傳回 `Freight` 資料表中 `Orders` 值的平均值。</span><span class="sxs-lookup"><span data-stu-id="76d35-106">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="76d35-107">Northwind 範例資料庫的結果會是 `78.2442`。</span><span class="sxs-lookup"><span data-stu-id="76d35-107">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="76d35-108">範例</span><span class="sxs-lookup"><span data-stu-id="76d35-108">Example</span></span>  
 <span data-ttu-id="76d35-109">下列範例會傳回 `Products` 資料表中所有 `Products` 的單價平均值。</span><span class="sxs-lookup"><span data-stu-id="76d35-109">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="76d35-110">Northwind 範例資料庫的結果會是 `28.8663`。</span><span class="sxs-lookup"><span data-stu-id="76d35-110">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="76d35-111">範例</span><span class="sxs-lookup"><span data-stu-id="76d35-111">Example</span></span>  
 <span data-ttu-id="76d35-112">下列範例使用 `Average` 運算子，尋找單價高於所屬分類之平均單價的 `Products`。</span><span class="sxs-lookup"><span data-stu-id="76d35-112">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="76d35-113">接著，這個範例會以群組顯示結果。</span><span class="sxs-lookup"><span data-stu-id="76d35-113">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="76d35-114">請注意，因為傳回型別是匿名，所以這個範例需要在 C# 中使用 `var` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="76d35-114">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="76d35-115">如果對 Northwind 範例資料庫執行這個查詢，則結果應該會與下列類似：</span><span class="sxs-lookup"><span data-stu-id="76d35-115">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a><span data-ttu-id="76d35-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76d35-116">See also</span></span>
- [<span data-ttu-id="76d35-117">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="76d35-117">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
