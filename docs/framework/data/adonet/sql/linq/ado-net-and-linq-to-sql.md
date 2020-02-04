---
title: ADO.NET 和 LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 4d2376a2e32ff099497a5dbcd6cb68d8ed526884
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979998"
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="7fe1d-102">ADO.NET 和 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7fe1d-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7fe1d-103">是 ADO.NET 系列技術的一部分。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-103">is part of the ADO.NET family of technologies.</span></span> <span data-ttu-id="7fe1d-104">它是以 ADO.NET 提供者模型所提供的服務為基礎。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-104">It is based on services provided by the ADO.NET provider model.</span></span> <span data-ttu-id="7fe1d-105">因此，您可以混用現有 ADO.NET 應用程式的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 程式碼，並將目前的 ADO.NET 解決方案遷移至 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="7fe1d-106">下圖提供關聯性 (Relationship) 的高層級檢視。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="7fe1d-107">![LINQ to SQL 和 ADO.NET](./media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="7fe1d-107">![LINQ to SQL and ADO.NET](./media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="7fe1d-108">連線</span><span class="sxs-lookup"><span data-stu-id="7fe1d-108">Connections</span></span>  
 <span data-ttu-id="7fe1d-109">當您建立 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>時，可以提供現有的 ADO.NET 連接。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-109">You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="7fe1d-110">針對 <xref:System.Data.Linq.DataContext> 的所有作業（包括查詢）都會使用此提供的連接。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="7fe1d-111">如果連接已開啟，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 將其保留為已完成。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="7fe1d-112">您可以一直存取此連接，並且使用 <xref:System.Data.Linq.DataContext.Connection%2A> 屬性自行將它關閉，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="7fe1d-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="7fe1d-113">異動</span><span class="sxs-lookup"><span data-stu-id="7fe1d-113">Transactions</span></span>  
 <span data-ttu-id="7fe1d-114">當您的應用程式已經啟始異動而且您希望您的 <xref:System.Data.Linq.DataContext> 參與其中時，您可以提供您的 <xref:System.Data.Linq.DataContext> 與自己的資料庫異動。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="7fe1d-115">使用 .NET Framework 來執行交易的慣用方法是使用 <xref:System.Transactions.TransactionScope> 物件。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-115">The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="7fe1d-116">使用這個方法，您可以進行適用於所有資料庫和其他常駐記憶體資源管理員的分散式異動。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="7fe1d-117">交易範圍需要少數資源即可開始。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="7fe1d-118">當交易範圍內有多個連線時，才會自行升級至分散式交易。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="7fe1d-119">您無法將此方法用於所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="7fe1d-120">例如，當 SqlClient 連接針對 SQL Server 2000 伺服器運作時，無法升級系統交易。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-120">For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server.</span></span> <span data-ttu-id="7fe1d-121">反而，每當它看見正在使用的異動範圍時，就會自動參與完整的分散式異動。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="7fe1d-122">直接 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="7fe1d-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="7fe1d-123">您偶而會碰到 <xref:System.Data.Linq.DataContext> 查詢或提交變更的能力不足以因應您想執行之特殊工作的情況。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="7fe1d-124">在這些情況下，您可以使用 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法將 SQL 命令發出至資料庫，並將查詢結果轉換為物件。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="7fe1d-125">例如，假設 `Customer` 類別的資料會分布於兩個資料表 (customer1 和 customer2)。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="7fe1d-126">下列查詢會傳回 `Customer` 物件的序列：</span><span class="sxs-lookup"><span data-stu-id="7fe1d-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="7fe1d-127">只要表格式結果中的資料行名稱符合實體類別的資料行屬性，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 就會從任何 SQL 查詢建立物件。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="7fe1d-128">參數</span><span class="sxs-lookup"><span data-stu-id="7fe1d-128">Parameters</span></span>  
 <span data-ttu-id="7fe1d-129"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法可接受參數。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="7fe1d-130">下列程式碼會執行參數型查詢：</span><span class="sxs-lookup"><span data-stu-id="7fe1d-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="7fe1d-131">查詢文字中的參數會使用與 `Console.WriteLine()` 和 `String.Format()` 所用的相同大括號標記法加以表示。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="7fe1d-132">`String.Format()` 會採用您提供的查詢字串，並且以產生的參數名稱 (例如 `@p0`、`@p1` ...、`@p(n)`) 替代大括號內的參數。</span><span class="sxs-lookup"><span data-stu-id="7fe1d-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe1d-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="7fe1d-133">See also</span></span>

- [<span data-ttu-id="7fe1d-134">背景資訊</span><span class="sxs-lookup"><span data-stu-id="7fe1d-134">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="7fe1d-135">如何：重複使用 ADO.NET 命令和 DataContext 之間的連線</span><span class="sxs-lookup"><span data-stu-id="7fe1d-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
