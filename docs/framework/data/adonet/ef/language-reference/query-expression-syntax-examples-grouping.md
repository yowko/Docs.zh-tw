---
title: "查詢運算式語法範例：群組"
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
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 313a218827122a8694ee314925408ec3526f01c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="64e73-102">查詢運算式語法範例：群組</span><span class="sxs-lookup"><span data-stu-id="64e73-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="64e73-103">本主題中的範例將示範如何使用`GroupBy`方法來查詢[AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)透過查詢運算式語法。</span><span class="sxs-lookup"><span data-stu-id="64e73-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="64e73-104">這些範例中使用的 AdventureWorks Sales Model 是根據 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="64e73-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="64e73-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="64e73-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="64e73-106">範例</span><span class="sxs-lookup"><span data-stu-id="64e73-106">Example</span></span>  
 <span data-ttu-id="64e73-107">下列範例會傳回依據郵遞區號分組的 `Address` 物件。</span><span class="sxs-lookup"><span data-stu-id="64e73-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="64e73-108">這些結果會投影至匿名型別中。</span><span class="sxs-lookup"><span data-stu-id="64e73-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="64e73-109">範例</span><span class="sxs-lookup"><span data-stu-id="64e73-109">Example</span></span>  
 <span data-ttu-id="64e73-110">下列範例會傳回依據連絡人姓氏第一個字母分組的 `Contact` 物件。</span><span class="sxs-lookup"><span data-stu-id="64e73-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="64e73-111">這些結果也會依據姓氏的第一個字母排序，然後投影至匿名型別中。</span><span class="sxs-lookup"><span data-stu-id="64e73-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="64e73-112">範例</span><span class="sxs-lookup"><span data-stu-id="64e73-112">Example</span></span>  
 <span data-ttu-id="64e73-113">下列範例會傳回依客戶 ID 群組的 `SalesOrderHeader` 物件。</span><span class="sxs-lookup"><span data-stu-id="64e73-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="64e73-114">也會傳回每一客戶的銷售數量。</span><span class="sxs-lookup"><span data-stu-id="64e73-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="64e73-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="64e73-115">See Also</span></span>  
 [<span data-ttu-id="64e73-116">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="64e73-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
