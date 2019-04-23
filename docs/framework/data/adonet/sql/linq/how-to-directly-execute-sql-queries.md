---
title: HOW TO：直接執行 SQL 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 6423959ed5036cc8ab2a88bb7273ef7aa95c8958
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101532"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="f3db0-102">HOW TO：直接執行 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="f3db0-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f3db0-103">會將您撰寫的查詢轉譯為參數型 SQL 查詢 (文字格式)，並將它們傳送給 SQL Server 進行處理。</span><span class="sxs-lookup"><span data-stu-id="f3db0-103">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="f3db0-104">SQL 無法執行您應用程式可以在本機使用的各種方法。</span><span class="sxs-lookup"><span data-stu-id="f3db0-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f3db0-105">會嘗試將這些本機方法轉換為可以在 SQL 環境內進行的對等作業和函式。</span><span class="sxs-lookup"><span data-stu-id="f3db0-105">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="f3db0-106">[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 內建型別的大部分方法和運算子都可以直接轉譯為 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="f3db0-106">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="f3db0-107">而有些方法和運算則可以透過可用的函式產生。</span><span class="sxs-lookup"><span data-stu-id="f3db0-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="f3db0-108">無法產生的部分則會產生執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f3db0-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="f3db0-109">如需詳細資訊，請參閱 < [SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="f3db0-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="f3db0-110">如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢不足以進行特殊化工作，則可以使用 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法執行 SQL 查詢，然後將查詢結果直接轉換為物件。</span><span class="sxs-lookup"><span data-stu-id="f3db0-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3db0-111">範例</span><span class="sxs-lookup"><span data-stu-id="f3db0-111">Example</span></span>  
 <span data-ttu-id="f3db0-112">在下列範例中，假設 `Customer` 類別的資料分佈於兩張資料表 (customer1 和 customer2)。</span><span class="sxs-lookup"><span data-stu-id="f3db0-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="f3db0-113">這個查詢會傳回 `Customer` 物件的序列。</span><span class="sxs-lookup"><span data-stu-id="f3db0-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="f3db0-114">只要表格式結果中的資料行名稱符合您的實體類別中的資料行屬性[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]建立您的物件，從任何 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="f3db0-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3db0-115">範例</span><span class="sxs-lookup"><span data-stu-id="f3db0-115">Example</span></span>  
 <span data-ttu-id="f3db0-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法也允許使用參數。</span><span class="sxs-lookup"><span data-stu-id="f3db0-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="f3db0-117">使用下列程式碼，就可以執行參數型查詢。</span><span class="sxs-lookup"><span data-stu-id="f3db0-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="f3db0-118">查詢文字中的參數使用與 `Console.WriteLine()` 和 `String.Format()` 所用的相同大括號標記法來表示。</span><span class="sxs-lookup"><span data-stu-id="f3db0-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="f3db0-119">事實上，`String.Format()`提供，例如取代以大括號的參數產生參數名稱的查詢字串稱為實際@p0， @p1 ...， @p(n)。</span><span class="sxs-lookup"><span data-stu-id="f3db0-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3db0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3db0-120">See also</span></span>

- [<span data-ttu-id="f3db0-121">背景資訊</span><span class="sxs-lookup"><span data-stu-id="f3db0-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="f3db0-122">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="f3db0-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
