---
title: 快速入門
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 17b014a5a56a2c60359f6fb0b60df29feb97f2a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529407"
---
# <a name="getting-started"></a><span data-ttu-id="842f5-102">快速入門</span><span class="sxs-lookup"><span data-stu-id="842f5-102">Getting Started</span></span>
<span data-ttu-id="842f5-103">藉由使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您可以使用[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]技術來存取 SQL 資料庫，就如同存取記憶體中的集合。</span><span class="sxs-lookup"><span data-stu-id="842f5-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="842f5-104">例如，下列程式碼會建立 `nw` 物件來表示 `Northwind` 資料庫、目標是設定為 `Customers` 資料表、篩選來自 `Customers` 的 `London` 的資料列，以及選取 `CompanyName` 的字串進行擷取。</span><span class="sxs-lookup"><span data-stu-id="842f5-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="842f5-105">執行迴圈 (Loop) 時，會擷取 `CompanyName` 值的集合。</span><span class="sxs-lookup"><span data-stu-id="842f5-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="842f5-106">後續步驟</span><span class="sxs-lookup"><span data-stu-id="842f5-106">Next Steps</span></span>  
 <span data-ttu-id="842f5-107">如需一些其他的範例，包括插入和更新，請參閱[項目您可以不要使用 LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="842f5-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="842f5-108">接下來，請嘗試一些逐步解說和教學課程，以獲取使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的實務經驗。</span><span class="sxs-lookup"><span data-stu-id="842f5-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="842f5-109">請參閱[依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)。</span><span class="sxs-lookup"><span data-stu-id="842f5-109">See [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="842f5-110">最後，了解如何開始使用您自己[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]專案，請閱讀[使用 LINQ to SQL 的典型步驟](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="842f5-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842f5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="842f5-111">See Also</span></span>  
 [<span data-ttu-id="842f5-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="842f5-112">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="842f5-113">LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="842f5-113">Introduction to LINQ</span></span>](https://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 [<span data-ttu-id="842f5-114">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="842f5-114">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
