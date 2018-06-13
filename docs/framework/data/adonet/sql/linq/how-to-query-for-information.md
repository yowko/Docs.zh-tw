---
title: 如何：查詢資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ae369cb6aaabfdf116f43629a0acb4ad9f7af8c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361248"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="d8624-102">如何：查詢資訊</span><span class="sxs-lookup"><span data-stu-id="d8624-102">How to: Query for Information</span></span>
<span data-ttu-id="d8624-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中之查詢使用的語法與 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中的查詢相同。</span><span class="sxs-lookup"><span data-stu-id="d8624-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="d8624-104">唯一的差別在於中參考的物件[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]查詢都會對應到資料庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="d8624-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="d8624-105">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="d8624-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d8624-106"> 會將您撰寫的查詢轉譯為對等 SQL 查詢，並將它們傳送給伺服器進行處理。</span><span class="sxs-lookup"><span data-stu-id="d8624-106"> translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="d8624-107">在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 應用程式中，可能需要特別注意 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的部分功能。</span><span class="sxs-lookup"><span data-stu-id="d8624-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="d8624-108">如需詳細資訊，請參閱[查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="d8624-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8624-109">範例</span><span class="sxs-lookup"><span data-stu-id="d8624-109">Example</span></span>  
 <span data-ttu-id="d8624-110">下列查詢會要求來自倫敦 (London) 的客戶名單。</span><span class="sxs-lookup"><span data-stu-id="d8624-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="d8624-111">在這個範例中，`Customers` 是 Northwind 範例資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="d8624-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d8624-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8624-112">See Also</span></span>  
 [<span data-ttu-id="d8624-113">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="d8624-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="d8624-114">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="d8624-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="d8624-115">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="d8624-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
