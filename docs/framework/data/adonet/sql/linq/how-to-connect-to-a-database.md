---
title: 如何：連接至資料庫
description: 瞭解如何使用 DataCoNtext 連接到 LINQ to SQL 中的資料庫。 請參閱這些範例，使用 DataCoNtext 連接到資料庫並取得資料列。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: c3320a598cb8407ab584530c615c2e5ef0de53c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286400"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="7b298-104">如何：連接至資料庫</span><span class="sxs-lookup"><span data-stu-id="7b298-104">How to: Connect to a Database</span></span>
<span data-ttu-id="7b298-105"><xref:System.Data.Linq.DataContext> 是主要管道，您可以透過該管道連接至資料庫、擷取資料庫中的物件，以及將變更送回給資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b298-105">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="7b298-106">您可以使用， <xref:System.Data.Linq.DataContext> 就像使用 ADO.NET 一樣 <xref:System.Data.SqlClient.SqlConnection> 。</span><span class="sxs-lookup"><span data-stu-id="7b298-106">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="7b298-107">事實上，<xref:System.Data.Linq.DataContext> 是使用您所提供的連接或連接字串 (Connection String) 來初始化。</span><span class="sxs-lookup"><span data-stu-id="7b298-107">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="7b298-108">如需詳細資訊，請參閱[DataCoNtext 方法（O/R 設計工具）](/visualstudio/data-tools/datacontext-methods-o-r-designer)。</span><span class="sxs-lookup"><span data-stu-id="7b298-108">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="7b298-109"><xref:System.Data.Linq.DataContext> 的用途是將物件的要求轉譯為針對資料庫進行的 SQL 查詢，然後再從結果中組合物件。</span><span class="sxs-lookup"><span data-stu-id="7b298-109">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="7b298-110">會藉 <xref:System.Data.Linq.DataContext> 由實作為標準查詢運算子（例如和），來啟用語言整合式查詢（LINQ） `Where` `Select` 。</span><span class="sxs-lookup"><span data-stu-id="7b298-110">The <xref:System.Data.Linq.DataContext> enables Language-Integrated Query (LINQ) by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b298-111">維護安全的連接是最重要的事。</span><span class="sxs-lookup"><span data-stu-id="7b298-111">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="7b298-112">如需詳細資訊，請參閱[LINQ to SQL 中的安全性](security-in-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="7b298-112">For more information, see [Security in LINQ to SQL](security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b298-113">範例</span><span class="sxs-lookup"><span data-stu-id="7b298-113">Example</span></span>  
 <span data-ttu-id="7b298-114">在下列範例中，<xref:System.Data.Linq.DataContext> 是用來連接至 Northwind 範例資料庫，以及擷取城市為倫敦 (London) 之客戶的資料列。</span><span class="sxs-lookup"><span data-stu-id="7b298-114">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="7b298-115">使用實體類別來識別每個資料庫資料表，這樣每個資料庫資料表會以透過 `Table` 方法取得的 <xref:System.Data.Linq.DataContext.GetTable%2A> 集合表示。</span><span class="sxs-lookup"><span data-stu-id="7b298-115">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b298-116">範例</span><span class="sxs-lookup"><span data-stu-id="7b298-116">Example</span></span>  
 <span data-ttu-id="7b298-117">最佳做法是宣告強型別 (Strongly Typed) <xref:System.Data.Linq.DataContext>，而不是依賴基本 <xref:System.Data.Linq.DataContext> 類別和 <xref:System.Data.Linq.DataContext.GetTable%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7b298-117">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="7b298-118">強型別 <xref:System.Data.Linq.DataContext> 會將所有 `Table` 集合宣告為內容的成員 (如下列範例所示)。</span><span class="sxs-lookup"><span data-stu-id="7b298-118">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="7b298-119">接著，您可以用下列更簡單的方式表示針對倫敦 (London) 客戶的查詢：</span><span class="sxs-lookup"><span data-stu-id="7b298-119">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="7b298-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b298-120">See also</span></span>

- [<span data-ttu-id="7b298-121">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="7b298-121">Communicating with the Database</span></span>](communicating-with-the-database.md)
