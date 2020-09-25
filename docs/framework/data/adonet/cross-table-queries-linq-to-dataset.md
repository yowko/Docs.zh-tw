---
title: 跨資料表查詢 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: a209cfe4142ad8ebdbce1d715a76ac27300f4e19
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202392"
---
# <a name="cross-table-queries-linq-to-dataset"></a><span data-ttu-id="4aa25-102">跨資料表查詢 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="4aa25-102">Cross-Table Queries (LINQ to DataSet)</span></span>

<span data-ttu-id="4aa25-103">除了查詢單一資料表以外，您也可以在 LINQ to DataSet 中執行跨資料表查詢。</span><span class="sxs-lookup"><span data-stu-id="4aa25-103">In addition to querying a single table, you can also perform cross-table queries in LINQ to DataSet.</span></span> <span data-ttu-id="4aa25-104">這是使用 *聯結*完成的。</span><span class="sxs-lookup"><span data-stu-id="4aa25-104">This is done by using a *join*.</span></span> <span data-ttu-id="4aa25-105">聯結是指某個資料來源中的物件與另一個資料來源中共用相同屬性之物件的關聯，例如產品或連絡人識別碼。</span><span class="sxs-lookup"><span data-stu-id="4aa25-105">A join is the association of objects in one data source with objects that share a common attribute in another data source, such as a product or contact ID.</span></span> <span data-ttu-id="4aa25-106">在物件導向的程式設計中，物件之間的關聯性相當容易瀏覽，因為每個物件都具有參考另一個物件的成員。</span><span class="sxs-lookup"><span data-stu-id="4aa25-106">In object-oriented programming, relationships between objects are relatively easy to navigate because each object has a member that references another object.</span></span> <span data-ttu-id="4aa25-107">不過，在外部資料庫資料表中，瀏覽關聯性就沒有這麼直接。</span><span class="sxs-lookup"><span data-stu-id="4aa25-107">In external database tables, however, navigating relationships is not as straightforward.</span></span> <span data-ttu-id="4aa25-108">資料庫資料表不包含內建關聯性。</span><span class="sxs-lookup"><span data-stu-id="4aa25-108">Database tables do not contain built-in relationships.</span></span> <span data-ttu-id="4aa25-109">在這些情況中，聯結作業可用來比對每個來源的項目。</span><span class="sxs-lookup"><span data-stu-id="4aa25-109">In these cases, the join operation can be used to match elements from each source.</span></span> <span data-ttu-id="4aa25-110">例如，假設有兩個包含產品資訊和銷售資訊的資料表。此時，您可能會使用聯結作業，針對相同銷售訂單比對銷售資訊和產品。</span><span class="sxs-lookup"><span data-stu-id="4aa25-110">For example, given two tables that contain product information and sales information, you could use a join operation to match sales information and products for the same sales order.</span></span>  
  
 <span data-ttu-id="4aa25-111"> (LINQ) framework 的語言整合式查詢提供兩個聯結運算子： <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A> 。</span><span class="sxs-lookup"><span data-stu-id="4aa25-111">The Language-Integrated Query (LINQ) framework provides two join operators, <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="4aa25-112">這些運算子會執行等聯結：也就是，只有當索引鍵相等時，才會符合兩個數據 *源的聯結*。</span><span class="sxs-lookup"><span data-stu-id="4aa25-112">These operators perform *equi-joins*: that is, joins that match two data sources only when their keys are equal.</span></span> <span data-ttu-id="4aa25-113"> (相反地，Transact-sql 支援以外的聯結運算子 `equals` ，例如 `less than` 運算子。 ) </span><span class="sxs-lookup"><span data-stu-id="4aa25-113">(By contrast, Transact-SQL supports join operators other than `equals`, such as the `less than` operator.)</span></span>  
  
 <span data-ttu-id="4aa25-114">在關聯式資料庫詞彙中，<xref:System.Linq.Enumerable.Join%2A> 會實作內部聯結 (Inner Join)。</span><span class="sxs-lookup"><span data-stu-id="4aa25-114">In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join.</span></span> <span data-ttu-id="4aa25-115">內部聯結是一種聯結類型，而這種聯結只會傳回在相對資料集內部具有相符項目的物件。</span><span class="sxs-lookup"><span data-stu-id="4aa25-115">An inner join is a type of join in which only those objects that have a match in the opposite data set are returned.</span></span>  
  
 <span data-ttu-id="4aa25-116">在 <xref:System.Linq.Enumerable.GroupJoin%2A> 關係資料庫詞彙中，運算子沒有直接對等專案，它們會實作為內部聯結和左方外部聯結的超集合。</span><span class="sxs-lookup"><span data-stu-id="4aa25-116">The <xref:System.Linq.Enumerable.GroupJoin%2A> operators have no direct equivalent in relational database terms; they implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="4aa25-117">左方外部聯結是一種聯結，會傳回第一個 (左) 集合中的每個專案，即使它在第二個集合中沒有相互關聯的元素。</span><span class="sxs-lookup"><span data-stu-id="4aa25-117">A left outer join is a join that returns each element of the first (left) collection, even if it has no correlated elements in the second collection.</span></span>  
  
 <span data-ttu-id="4aa25-118">如需聯結的詳細資訊，請參閱 [聯結作業](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="4aa25-118">For more information about joins, see [Join Operations](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4aa25-119">範例</span><span class="sxs-lookup"><span data-stu-id="4aa25-119">Example</span></span>  

 <span data-ttu-id="4aa25-120">下列範例會針對 AdventureWorks 範例資料庫的 `SalesOrderHeader` 和 `SalesOrderDetail` 資料表執行傳統聯結，以便取得八月份的線上訂單。</span><span class="sxs-lookup"><span data-stu-id="4aa25-120">The following example performs a traditional join of the `SalesOrderHeader` and `SalesOrderDetail` tables from the AdventureWorks sample database to obtain online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="4aa25-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4aa25-121">See also</span></span>

- [<span data-ttu-id="4aa25-122">查詢 DataSet</span><span class="sxs-lookup"><span data-stu-id="4aa25-122">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="4aa25-123">單一資料表查詢</span><span class="sxs-lookup"><span data-stu-id="4aa25-123">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="4aa25-124">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="4aa25-124">Querying Typed DataSets</span></span>](querying-typed-datasets.md)
- <span data-ttu-id="4aa25-125">[聯結作業](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="4aa25-125">[Join Operations](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))</span></span>
- [<span data-ttu-id="4aa25-126">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="4aa25-126">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
