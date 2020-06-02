---
title: 如何：直接執行 SQL 查詢
description: 瞭解如何使用 ExecuteQuery 來執行查詢，然後在 LINQ to SQL 查詢不足的情況下，將結果直接轉換成物件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 59bd404e41f6be1181d6a625c31ee23358db0df3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286361"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="00b44-103">如何：直接執行 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="00b44-103">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="00b44-104">會將您撰寫的查詢轉譯為參數型 SQL 查詢 (文字格式)，並將它們傳送給 SQL Server 進行處理。</span><span class="sxs-lookup"><span data-stu-id="00b44-104">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="00b44-105">SQL 無法執行您應用程式可以在本機使用的各種方法。</span><span class="sxs-lookup"><span data-stu-id="00b44-105">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="00b44-106">會嘗試將這些本機方法轉換為可以在 SQL 環境內進行的對等作業和函式。</span><span class="sxs-lookup"><span data-stu-id="00b44-106">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="00b44-107">.NET Framework 內建型別的大部分方法和運算子都可以直接轉譯為 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="00b44-107">Most methods and operators on .NET Framework built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="00b44-108">而有些方法和運算則可以透過可用的函式產生。</span><span class="sxs-lookup"><span data-stu-id="00b44-108">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="00b44-109">無法產生的部分則會產生執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="00b44-109">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="00b44-110">如需詳細資訊，請參閱[SQL-CLR 型別對應](sql-clr-type-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="00b44-110">For more information, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="00b44-111">如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢不足以進行特殊化工作，則可以使用 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法執行 SQL 查詢，然後將查詢結果直接轉換為物件。</span><span class="sxs-lookup"><span data-stu-id="00b44-111">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00b44-112">範例</span><span class="sxs-lookup"><span data-stu-id="00b44-112">Example</span></span>  
 <span data-ttu-id="00b44-113">在下列範例中，假設 `Customer` 類別的資料分佈於兩張資料表 (customer1 和 customer2)。</span><span class="sxs-lookup"><span data-stu-id="00b44-113">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="00b44-114">這個查詢會傳回 `Customer` 物件的序列。</span><span class="sxs-lookup"><span data-stu-id="00b44-114">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="00b44-115">只要表格式結果中的資料行名稱符合實體類別的資料行屬性，就會 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 從任何 SQL 查詢建立物件。</span><span class="sxs-lookup"><span data-stu-id="00b44-115">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00b44-116">範例</span><span class="sxs-lookup"><span data-stu-id="00b44-116">Example</span></span>  
 <span data-ttu-id="00b44-117"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法也允許使用參數。</span><span class="sxs-lookup"><span data-stu-id="00b44-117">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="00b44-118">使用下列程式碼，就可以執行參數型查詢。</span><span class="sxs-lookup"><span data-stu-id="00b44-118">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="00b44-119">查詢文字中的參數使用與 `Console.WriteLine()` 和 `String.Format()` 所用的相同大括號標記法來表示。</span><span class="sxs-lookup"><span data-stu-id="00b44-119">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="00b44-120">事實上， `String.Format()` 實際上是在您所提供的查詢字串上呼叫，並以產生的參數名稱（例如 @p0 ， @p1 ...、 @p （n））取代大括弧參數。</span><span class="sxs-lookup"><span data-stu-id="00b44-120">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b44-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00b44-121">See also</span></span>

- [<span data-ttu-id="00b44-122">背景資訊</span><span class="sxs-lookup"><span data-stu-id="00b44-122">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="00b44-123">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="00b44-123">Querying the Database</span></span>](querying-the-database.md)
