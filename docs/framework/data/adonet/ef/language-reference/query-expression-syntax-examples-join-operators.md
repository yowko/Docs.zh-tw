---
title: 查詢運算式語法範例：聯結運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: e80c50daeb0de7f4a8477786f28441d1495033ea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249479"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="47fa6-102">查詢運算式語法範例：聯結運算子</span><span class="sxs-lookup"><span data-stu-id="47fa6-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="47fa6-103">在以彼此沒有可瀏覽關聯性之資料來源 (例如關聯式資料庫資料表) 為目標的查詢中，聯結 (Join) 是一項重要的作業。</span><span class="sxs-lookup"><span data-stu-id="47fa6-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="47fa6-104">兩個資料來源的聯結是指某個資料來源中的物件與另一個資料來源中共用相同屬性之物件的關聯。</span><span class="sxs-lookup"><span data-stu-id="47fa6-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="47fa6-105">如需詳細資訊, 請參閱[標準查詢運算子總覽](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="47fa6-105">For more information, see [Standard Query Operators Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="47fa6-106">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.GroupJoin%2A>和<xref:System.Linq.Enumerable.Join%2A>方法, 利用查詢運算式語法來查詢[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) 。</span><span class="sxs-lookup"><span data-stu-id="47fa6-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="47fa6-107">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="47fa6-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="47fa6-108">本主題中的範例會使用下列`using` / `Imports`語句:</span><span class="sxs-lookup"><span data-stu-id="47fa6-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="47fa6-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="47fa6-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="47fa6-110">範例</span><span class="sxs-lookup"><span data-stu-id="47fa6-110">Example</span></span>  
 <span data-ttu-id="47fa6-111">下列範例會在 SalesOrderHeader 和 SalesOrderDetail 資料表上執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 來尋找每一客戶的定單數目。</span><span class="sxs-lookup"><span data-stu-id="47fa6-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="47fa6-112">群組聯結是左外部聯結的對等項目，它會傳回第一個 (左) 資料來源的每個項目，即使其他資料來源中沒有相互關聯的項目也一樣。</span><span class="sxs-lookup"><span data-stu-id="47fa6-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="47fa6-113">範例</span><span class="sxs-lookup"><span data-stu-id="47fa6-113">Example</span></span>  
 <span data-ttu-id="47fa6-114">下列範例會在 Contact 和 SalesOrderHeader 資料表上執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 來尋找每一連絡人的定單數目。</span><span class="sxs-lookup"><span data-stu-id="47fa6-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="47fa6-115">然後顯示每一連絡人的訂單數目和 ID。</span><span class="sxs-lookup"><span data-stu-id="47fa6-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="47fa6-116">Join</span><span class="sxs-lookup"><span data-stu-id="47fa6-116">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="47fa6-117">範例</span><span class="sxs-lookup"><span data-stu-id="47fa6-117">Example</span></span>  
 <span data-ttu-id="47fa6-118">下列範例會針對 SalesOrderHeader 和 SalesOrderDetail 資料表執行聯結，以便取得八月的線上訂單資訊。</span><span class="sxs-lookup"><span data-stu-id="47fa6-118">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="47fa6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47fa6-119">See also</span></span>

- [<span data-ttu-id="47fa6-120">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="47fa6-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
