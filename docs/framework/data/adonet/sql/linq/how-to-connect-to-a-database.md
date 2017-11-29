---
title: "如何：連接至資料庫"
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
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f302e3f24b844bf0357b00bcd97ab074ac972bff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="2d60c-102">如何：連接至資料庫</span><span class="sxs-lookup"><span data-stu-id="2d60c-102">How to: Connect to a Database</span></span>
<span data-ttu-id="2d60c-103"><xref:System.Data.Linq.DataContext> 是主要管道，您可以透過該管道連接至資料庫、擷取資料庫中的物件，以及將變更送回給資料庫。</span><span class="sxs-lookup"><span data-stu-id="2d60c-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="2d60c-104">您使用<xref:System.Data.Linq.DataContext>就像您會使用[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>。</span><span class="sxs-lookup"><span data-stu-id="2d60c-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="2d60c-105">事實上，<xref:System.Data.Linq.DataContext> 是使用您所提供的連接或連接字串 (Connection String) 來初始化。</span><span class="sxs-lookup"><span data-stu-id="2d60c-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="2d60c-106">如需詳細資訊，請參閱[DataContext 方法 （O/R 設計工具）](/visualstudio/data-tools/datacontext-methods-o-r-designer)。</span><span class="sxs-lookup"><span data-stu-id="2d60c-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="2d60c-107"><xref:System.Data.Linq.DataContext> 的用途是將物件的要求轉譯為針對資料庫進行的 SQL 查詢，然後再從結果中組合物件。</span><span class="sxs-lookup"><span data-stu-id="2d60c-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="2d60c-108"><xref:System.Data.Linq.DataContext> 會實作與標準查詢運算子 (如 [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] 和 `Where`) 相同的運算子模式，來啟用 `Select`。</span><span class="sxs-lookup"><span data-stu-id="2d60c-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d60c-109">維護安全的連接是最重要的事。</span><span class="sxs-lookup"><span data-stu-id="2d60c-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="2d60c-110">如需詳細資訊，請參閱[LINQ to SQL 中的安全性](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="2d60c-110">For more information, see [Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d60c-111">範例</span><span class="sxs-lookup"><span data-stu-id="2d60c-111">Example</span></span>  
 <span data-ttu-id="2d60c-112">在下列範例中，<xref:System.Data.Linq.DataContext> 是用來連接至 Northwind 範例資料庫，以及擷取城市為倫敦 (London) 之客戶的資料列。</span><span class="sxs-lookup"><span data-stu-id="2d60c-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="2d60c-113">使用實體類別來識別每個資料庫資料表，這樣每個資料庫資料表會以透過 `Table` 方法取得的 <xref:System.Data.Linq.DataContext.GetTable%2A> 集合表示。</span><span class="sxs-lookup"><span data-stu-id="2d60c-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d60c-114">範例</span><span class="sxs-lookup"><span data-stu-id="2d60c-114">Example</span></span>  
 <span data-ttu-id="2d60c-115">最佳做法是宣告強型別 (Strongly Typed) <xref:System.Data.Linq.DataContext>，而不是依賴基本 <xref:System.Data.Linq.DataContext> 類別和 <xref:System.Data.Linq.DataContext.GetTable%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d60c-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="2d60c-116">強型別 <xref:System.Data.Linq.DataContext> 會將所有 `Table` 集合宣告為內容的成員 (如下列範例所示)。</span><span class="sxs-lookup"><span data-stu-id="2d60c-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="2d60c-117">接著，您可以用下列更簡單的方式表示針對倫敦 (London) 客戶的查詢：</span><span class="sxs-lookup"><span data-stu-id="2d60c-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2d60c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d60c-118">See Also</span></span>  
 [<span data-ttu-id="2d60c-119">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="2d60c-119">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
