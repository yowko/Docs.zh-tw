---
title: "如何：查詢資訊"
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
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 527c2c1a84126bc2012779345fdd98ad832c9ceb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="499c2-102">如何：查詢資訊</span><span class="sxs-lookup"><span data-stu-id="499c2-102">How to: Query for Information</span></span>
<span data-ttu-id="499c2-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中之查詢使用的語法與 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中的查詢相同。</span><span class="sxs-lookup"><span data-stu-id="499c2-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="499c2-104">唯一的差別在於中參考的物件[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]查詢都會對應到資料庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="499c2-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="499c2-105">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="499c2-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="499c2-106"> 會將您撰寫的查詢轉譯為對等 SQL 查詢，並將它們傳送給伺服器進行處理。</span><span class="sxs-lookup"><span data-stu-id="499c2-106"> translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="499c2-107">在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 應用程式中，可能需要特別注意 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的部分功能。</span><span class="sxs-lookup"><span data-stu-id="499c2-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="499c2-108">如需詳細資訊，請參閱[查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="499c2-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="499c2-109">範例</span><span class="sxs-lookup"><span data-stu-id="499c2-109">Example</span></span>  
 <span data-ttu-id="499c2-110">下列查詢會要求來自倫敦 (London) 的客戶名單。</span><span class="sxs-lookup"><span data-stu-id="499c2-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="499c2-111">在這個範例中，`Customers` 是 Northwind 範例資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="499c2-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="499c2-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="499c2-112">See Also</span></span>  
 [<span data-ttu-id="499c2-113">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="499c2-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="499c2-114">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="499c2-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="499c2-115">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="499c2-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
