---
title: 快速入門
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: bd82b7e83149aaa53cf1b240cb79f8747bccba47
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793909"
---
# <a name="getting-started"></a><span data-ttu-id="03488-102">快速入門</span><span class="sxs-lookup"><span data-stu-id="03488-102">Getting Started</span></span>
<span data-ttu-id="03488-103">藉由[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]使用，您可以[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]使用技術來存取 SQL 資料庫，就如同存取記憶體中的集合一樣。</span><span class="sxs-lookup"><span data-stu-id="03488-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="03488-104">例如，下列程式碼會建立 `nw` 物件來表示 `Northwind` 資料庫、目標是設定為 `Customers` 資料表、篩選來自 `Customers` 的 `London` 的資料列，以及選取 `CompanyName` 的字串進行擷取。</span><span class="sxs-lookup"><span data-stu-id="03488-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="03488-105">執行迴圈 (Loop) 時，會擷取 `CompanyName` 值的集合。</span><span class="sxs-lookup"><span data-stu-id="03488-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="03488-106">後續步驟</span><span class="sxs-lookup"><span data-stu-id="03488-106">Next Steps</span></span>  
 <span data-ttu-id="03488-107">如需其他範例，包括插入和更新，請參閱[您可以如何使用 LINQ to SQL](what-you-can-do-with-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="03488-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="03488-108">接下來，請嘗試一些逐步解說和教學課程，以獲取使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的實務經驗。</span><span class="sxs-lookup"><span data-stu-id="03488-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="03488-109">請參閱[依逐步解說學習](learning-by-walkthroughs.md)。</span><span class="sxs-lookup"><span data-stu-id="03488-109">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="03488-110">最後，閱讀[使用 LINQ to SQL 的一般步驟](typical-steps-for-using-linq-to-sql.md)，瞭解[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]如何開始著手您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="03488-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03488-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03488-111">See also</span></span>

- [<span data-ttu-id="03488-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="03488-112">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="03488-113">LINQ （C#）簡介</span><span class="sxs-lookup"><span data-stu-id="03488-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="03488-114">LINQ 簡介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03488-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="03488-115">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="03488-115">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
