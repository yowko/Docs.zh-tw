---
title: 快速入門
description: 使用此範例程式碼，開始使用 LINQ to SQL 使用 LINQ 技術來存取 SQL 資料庫，就如同存取記憶體中的集合一樣。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: b886518d4cff687a18f363c3e3ba43b40631a22f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194371"
---
# <a name="getting-started"></a><span data-ttu-id="41c32-103">快速入門</span><span class="sxs-lookup"><span data-stu-id="41c32-103">Getting Started</span></span>

<span data-ttu-id="41c32-104">藉由使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ，您可以使用 LINQ 技術來存取 SQL 資料庫，就如同存取記憶體中的集合一樣。</span><span class="sxs-lookup"><span data-stu-id="41c32-104">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="41c32-105">例如，下列程式碼會建立 `nw` 物件來表示 `Northwind` 資料庫、目標是設定為 `Customers` 資料表、篩選來自 `Customers` 的 `London` 的資料列，以及選取 `CompanyName` 的字串進行擷取。</span><span class="sxs-lookup"><span data-stu-id="41c32-105">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="41c32-106">執行迴圈 (Loop) 時，會擷取 `CompanyName` 值的集合。</span><span class="sxs-lookup"><span data-stu-id="41c32-106">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="41c32-107">後續步驟</span><span class="sxs-lookup"><span data-stu-id="41c32-107">Next Steps</span></span>  

 <span data-ttu-id="41c32-108">如需其他範例，包括插入和更新，請參閱 [LINQ to SQL](what-you-can-do-with-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="41c32-108">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="41c32-109">接下來，請嘗試一些逐步解說和教學課程，以獲取使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的實務經驗。</span><span class="sxs-lookup"><span data-stu-id="41c32-109">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="41c32-110">請參閱 [依逐步解說學習](learning-by-walkthroughs.md)。</span><span class="sxs-lookup"><span data-stu-id="41c32-110">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="41c32-111">最後，藉 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 由閱讀 [使用 LINQ to SQL 的一般步驟](typical-steps-for-using-linq-to-sql.md)，瞭解如何開始使用您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="41c32-111">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c32-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41c32-112">See also</span></span>

- [<span data-ttu-id="41c32-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="41c32-113">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="41c32-114">LINQ 簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="41c32-114">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="41c32-115">LINQ 簡介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41c32-115">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="41c32-116">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="41c32-116">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
