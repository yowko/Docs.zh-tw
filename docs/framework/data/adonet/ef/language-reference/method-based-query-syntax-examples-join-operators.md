---
title: 以方法為基礎的查詢語法範例：聯結運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 700c29222d10177774e118e53fb51f177b723679
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176900"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="f061f-102">以方法為基礎的查詢語法範例：聯結運算子</span><span class="sxs-lookup"><span data-stu-id="f061f-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="f061f-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Join%2A>並<xref:System.Linq.Enumerable.GroupJoin%2A>方法來查詢[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)使用以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="f061f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="f061f-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="f061f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f061f-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="f061f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="f061f-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="f061f-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="f061f-107">範例</span><span class="sxs-lookup"><span data-stu-id="f061f-107">Example</span></span>  
 <span data-ttu-id="f061f-108">下列範例會在 SalesOrderHeader 和 SalesOrderDetail 資料表上執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 來尋找每一客戶的定單數目。</span><span class="sxs-lookup"><span data-stu-id="f061f-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="f061f-109">群組聯結是左外部聯結的對等項目，它會傳回第一個 (左) 資料來源的每個項目，即使其他資料來源中沒有相互關聯的項目也一樣。</span><span class="sxs-lookup"><span data-stu-id="f061f-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="f061f-110">範例</span><span class="sxs-lookup"><span data-stu-id="f061f-110">Example</span></span>  
 <span data-ttu-id="f061f-111">下列範例會在 Contact 和 SalesOrderHeader 資料表上執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 來尋找每一連絡人的定單數目。</span><span class="sxs-lookup"><span data-stu-id="f061f-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="f061f-112">然後顯示每一連絡人的訂單數目和 ID。</span><span class="sxs-lookup"><span data-stu-id="f061f-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="f061f-113">Join</span><span class="sxs-lookup"><span data-stu-id="f061f-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="f061f-114">範例</span><span class="sxs-lookup"><span data-stu-id="f061f-114">Example</span></span>  
 <span data-ttu-id="f061f-115">下列範例會聯結 Contact 和 SalesOrderHeader 資料表。</span><span class="sxs-lookup"><span data-stu-id="f061f-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="f061f-116">範例</span><span class="sxs-lookup"><span data-stu-id="f061f-116">Example</span></span>  
 <span data-ttu-id="f061f-117">下列範例會聯結 Contact 和 SalesOrderHeader 資料表，根據連絡人識別碼為結果分組。</span><span class="sxs-lookup"><span data-stu-id="f061f-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f061f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f061f-118">See also</span></span>

- [<span data-ttu-id="f061f-119">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="f061f-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
