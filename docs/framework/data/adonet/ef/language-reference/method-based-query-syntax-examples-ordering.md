---
title: 以方法為基礎的查詢語法範例：排序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: e213046955c2c4e720c56adb96da29078ea3c48d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226854"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="2d8fa-102">以方法為基礎的查詢語法範例：排序</span><span class="sxs-lookup"><span data-stu-id="2d8fa-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="2d8fa-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.ThenBy%2A>方法來查詢[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)使用以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="2d8fa-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="2d8fa-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="2d8fa-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2d8fa-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="2d8fa-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="2d8fa-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="2d8fa-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="2d8fa-107">範例</span><span class="sxs-lookup"><span data-stu-id="2d8fa-107">Example</span></span>  
 <span data-ttu-id="2d8fa-108">下列以方法為基礎的查詢語法範例會使用 <xref:System.Linq.Queryable.OrderBy%2A> 和 <xref:System.Linq.Queryable.ThenBy%2A> 來傳回先依據姓氏再依據名字排序的連絡人清單。</span><span class="sxs-lookup"><span data-stu-id="2d8fa-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="2d8fa-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="2d8fa-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="2d8fa-110">範例</span><span class="sxs-lookup"><span data-stu-id="2d8fa-110">Example</span></span>  
 <span data-ttu-id="2d8fa-111">下列範例會使用 <xref:System.Linq.Queryable.OrderBy%2A> 和 <xref:System.Linq.Queryable.ThenByDescending%2A> 方法，先依據標價排序，然後再執行產品名稱的遞減排序。</span><span class="sxs-lookup"><span data-stu-id="2d8fa-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="2d8fa-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d8fa-112">See also</span></span>

- [<span data-ttu-id="2d8fa-113">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="2d8fa-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
