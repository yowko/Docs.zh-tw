---
title: 作法：查詢資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ed32bbe7d27357cbed7d77dd235b698a65c0e29e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793531"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="cd185-102">作法：查詢資訊</span><span class="sxs-lookup"><span data-stu-id="cd185-102">How to: Query for Information</span></span>
<span data-ttu-id="cd185-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中之查詢使用的語法與 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中的查詢相同。</span><span class="sxs-lookup"><span data-stu-id="cd185-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="cd185-104">唯一的差異在於查詢中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]參考的物件會對應至資料庫中的元素。</span><span class="sxs-lookup"><span data-stu-id="cd185-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="cd185-105">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="cd185-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="cd185-106">會將您撰寫的查詢轉譯為對等 SQL 查詢，並將它們傳送給伺服器進行處理。</span><span class="sxs-lookup"><span data-stu-id="cd185-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="cd185-107">在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 應用程式中，可能需要特別注意 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的部分功能。</span><span class="sxs-lookup"><span data-stu-id="cd185-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="cd185-108">如需詳細資訊，請參閱[查詢概念](query-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="cd185-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd185-109">範例</span><span class="sxs-lookup"><span data-stu-id="cd185-109">Example</span></span>  
 <span data-ttu-id="cd185-110">下列查詢會要求來自倫敦 (London) 的客戶名單。</span><span class="sxs-lookup"><span data-stu-id="cd185-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="cd185-111">在這個範例中，`Customers` 是 Northwind 範例資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="cd185-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cd185-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd185-112">See also</span></span>

- [<span data-ttu-id="cd185-113">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="cd185-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="cd185-114">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="cd185-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="cd185-115">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="cd185-115">Querying the Database</span></span>](querying-the-database.md)
