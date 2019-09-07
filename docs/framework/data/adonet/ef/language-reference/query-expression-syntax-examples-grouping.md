---
title: 查詢運算式語法範例：群組
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: c9876c72a03f7827ec4b28d78f06ed372460caff
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398457"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="fbe0b-102">查詢運算式語法範例：群組</span><span class="sxs-lookup"><span data-stu-id="fbe0b-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="fbe0b-103">本主題中的範例將示範如何使用`GroupBy`方法，利用查詢運算式語法來查詢[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="fbe0b-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="fbe0b-104">這些範例中使用的 AdventureWorks Sales Model 是根據 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="fbe0b-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fbe0b-105">本主題中的範例會使用下列`using` / `Imports`語句：</span><span class="sxs-lookup"><span data-stu-id="fbe0b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="fbe0b-106">範例</span><span class="sxs-lookup"><span data-stu-id="fbe0b-106">Example</span></span>  
 <span data-ttu-id="fbe0b-107">下列範例會傳回依據郵遞區號分組的 `Address` 物件。</span><span class="sxs-lookup"><span data-stu-id="fbe0b-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="fbe0b-108">這些結果會投影至匿名型別中。</span><span class="sxs-lookup"><span data-stu-id="fbe0b-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="fbe0b-109">範例</span><span class="sxs-lookup"><span data-stu-id="fbe0b-109">Example</span></span>  
 <span data-ttu-id="fbe0b-110">下列範例會傳回依據連絡人姓氏第一個字母分組的 `Contact` 物件。</span><span class="sxs-lookup"><span data-stu-id="fbe0b-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="fbe0b-111">這些結果也會依據姓氏的第一個字母排序，然後投影至匿名型別中。</span><span class="sxs-lookup"><span data-stu-id="fbe0b-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="fbe0b-112">範例</span><span class="sxs-lookup"><span data-stu-id="fbe0b-112">Example</span></span>  
 <span data-ttu-id="fbe0b-113">下列範例會傳回依客戶 ID 群組的 `SalesOrderHeader` 物件。</span><span class="sxs-lookup"><span data-stu-id="fbe0b-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="fbe0b-114">也會傳回每一客戶的銷售數量。</span><span class="sxs-lookup"><span data-stu-id="fbe0b-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="fbe0b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbe0b-115">See also</span></span>

- [<span data-ttu-id="fbe0b-116">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="fbe0b-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
