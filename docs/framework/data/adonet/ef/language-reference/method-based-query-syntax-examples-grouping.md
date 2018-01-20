---
title: "以方法為基礎的查詢語法範例：群組"
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
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3443b86eec1bd7f86060c09dd5d153e6f1d7a4ab
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="1f2c0-102">以方法為基礎的查詢語法範例：群組</span><span class="sxs-lookup"><span data-stu-id="1f2c0-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="1f2c0-103">本主題中的範例會示範如何使用`GroupBy`方法來查詢[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)使用以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="1f2c0-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="1f2c0-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="1f2c0-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1f2c0-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="1f2c0-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="1f2c0-106">範例</span><span class="sxs-lookup"><span data-stu-id="1f2c0-106">Example</span></span>  
 <span data-ttu-id="1f2c0-107">以下範例使用 `GroupBy` 方法傳回依郵遞區號群組的 `Address` 物件。</span><span class="sxs-lookup"><span data-stu-id="1f2c0-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="1f2c0-108">這些結果會投影至匿名型別中。</span><span class="sxs-lookup"><span data-stu-id="1f2c0-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="1f2c0-109">範例</span><span class="sxs-lookup"><span data-stu-id="1f2c0-109">Example</span></span>  
 <span data-ttu-id="1f2c0-110">以下範例使用 `GroupBy` 方法傳回依連絡人姓氏的第一個字母群組的 `Contact` 物件。</span><span class="sxs-lookup"><span data-stu-id="1f2c0-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="1f2c0-111">結果也會依連絡人姓氏的第一個字母排序，並且會投影到匿名型別中。</span><span class="sxs-lookup"><span data-stu-id="1f2c0-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="1f2c0-112">範例</span><span class="sxs-lookup"><span data-stu-id="1f2c0-112">Example</span></span>  
 <span data-ttu-id="1f2c0-113">以下範例使用 `GroupBy` 方法傳回客戶 ID 群組的 `SalesOrderHeader` 物件。</span><span class="sxs-lookup"><span data-stu-id="1f2c0-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="1f2c0-114">也會傳回每一客戶的銷售數量。</span><span class="sxs-lookup"><span data-stu-id="1f2c0-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1f2c0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="1f2c0-115">See Also</span></span>  
 [<span data-ttu-id="1f2c0-116">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="1f2c0-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
