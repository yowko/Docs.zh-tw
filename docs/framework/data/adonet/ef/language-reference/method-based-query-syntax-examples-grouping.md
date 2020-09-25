---
title: 以方法為基礎的查詢語法範例：群組
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 2d84e755217878bfa248add37a752224a20d3f84
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191979"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="8fa05-102">以方法為基礎的查詢語法範例：群組</span><span class="sxs-lookup"><span data-stu-id="8fa05-102">Method-Based Query Syntax Examples: Grouping</span></span>

<span data-ttu-id="8fa05-103">本主題中的範例將示範如何使用方法 `GroupBy` ，利用以方法為基礎的查詢語法來查詢 [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="8fa05-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="8fa05-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="8fa05-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8fa05-105">本主題中的範例使用下列 `using` / `Imports` 語句：</span><span class="sxs-lookup"><span data-stu-id="8fa05-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="8fa05-106">範例</span><span class="sxs-lookup"><span data-stu-id="8fa05-106">Example</span></span>  

 <span data-ttu-id="8fa05-107">以下範例使用 `GroupBy` 方法傳回依郵遞區號群組的 `Address` 物件。</span><span class="sxs-lookup"><span data-stu-id="8fa05-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="8fa05-108">這些結果會投影至匿名型別中。</span><span class="sxs-lookup"><span data-stu-id="8fa05-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="8fa05-109">範例</span><span class="sxs-lookup"><span data-stu-id="8fa05-109">Example</span></span>  

 <span data-ttu-id="8fa05-110">以下範例使用 `GroupBy` 方法傳回依連絡人姓氏的第一個字母群組的 `Contact` 物件。</span><span class="sxs-lookup"><span data-stu-id="8fa05-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="8fa05-111">結果也會依連絡人姓氏的第一個字母排序，並且會投影到匿名型別中。</span><span class="sxs-lookup"><span data-stu-id="8fa05-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="8fa05-112">範例</span><span class="sxs-lookup"><span data-stu-id="8fa05-112">Example</span></span>  

 <span data-ttu-id="8fa05-113">以下範例使用 `GroupBy` 方法傳回客戶 ID 群組的 `SalesOrderHeader` 物件。</span><span class="sxs-lookup"><span data-stu-id="8fa05-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="8fa05-114">也會傳回每一客戶的銷售數量。</span><span class="sxs-lookup"><span data-stu-id="8fa05-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8fa05-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fa05-115">See also</span></span>

- [<span data-ttu-id="8fa05-116">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="8fa05-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
