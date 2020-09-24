---
title: 作法：查詢資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: d45fdfa8b8976e3cdc86b905443bf7bcea578714
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166400"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="25ed2-102">作法：查詢資訊</span><span class="sxs-lookup"><span data-stu-id="25ed2-102">How to: Query for Information</span></span>

<span data-ttu-id="25ed2-103">中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的查詢使用的語法與 LINQ 中的查詢相同。</span><span class="sxs-lookup"><span data-stu-id="25ed2-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="25ed2-104">唯一的差別在於查詢中參考的物件 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會對應至資料庫中的元素。</span><span class="sxs-lookup"><span data-stu-id="25ed2-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="25ed2-105">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="25ed2-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="25ed2-106">會將您撰寫的查詢轉譯為對等 SQL 查詢，並將它們傳送給伺服器進行處理。</span><span class="sxs-lookup"><span data-stu-id="25ed2-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="25ed2-107">LINQ 查詢的某些功能在應用程式中可能需要特別注意 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="25ed2-107">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="25ed2-108">如需詳細資訊，請參閱 [查詢概念](query-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="25ed2-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25ed2-109">範例</span><span class="sxs-lookup"><span data-stu-id="25ed2-109">Example</span></span>  

 <span data-ttu-id="25ed2-110">下列查詢會要求來自倫敦 (London) 的客戶名單。</span><span class="sxs-lookup"><span data-stu-id="25ed2-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="25ed2-111">在這個範例中，`Customers` 是 Northwind 範例資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="25ed2-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="25ed2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25ed2-112">See also</span></span>

- [<span data-ttu-id="25ed2-113">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="25ed2-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="25ed2-114">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="25ed2-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="25ed2-115">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="25ed2-115">Querying the Database</span></span>](querying-the-database.md)
