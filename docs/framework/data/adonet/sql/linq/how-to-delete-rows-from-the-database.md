---
title: "如何：從資料庫刪除資料列"
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
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ac81e4e18c578f11a5c6f36203e15b5363c54e71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="29aa4-102">如何：從資料庫刪除資料列</span><span class="sxs-lookup"><span data-stu-id="29aa4-102">How to: Delete Rows From the Database</span></span>
<span data-ttu-id="29aa4-103">您可以刪除資料庫中的資料列移除對應[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]從其資料表相關集合的物件。</span><span class="sxs-lookup"><span data-stu-id="29aa4-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="29aa4-104">將轉譯成適當的 SQL 變更`DELETE`命令。</span><span class="sxs-lookup"><span data-stu-id="29aa4-104"> translates your changes to the appropriate SQL `DELETE` commands.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="29aa4-105"> 不支援或辨識串聯 (Cascade) 刪除作業。</span><span class="sxs-lookup"><span data-stu-id="29aa4-105"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="29aa4-106">如果您要刪除有條件約束之資料表中的資料列，必須完成下列其中一項工作：</span><span class="sxs-lookup"><span data-stu-id="29aa4-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>  
  
-   <span data-ttu-id="29aa4-107">在資料庫的外部索引鍵條件約束中設定 `ON DELETE CASCADE` 規則。</span><span class="sxs-lookup"><span data-stu-id="29aa4-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
-   <span data-ttu-id="29aa4-108">使用您自己的程式碼，先刪除使父物件無法刪除的子物件。</span><span class="sxs-lookup"><span data-stu-id="29aa4-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="29aa4-109">否則，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="29aa4-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="29aa4-110">請參閱本主題稍後的第二個程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="29aa4-110">See the second code example later in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29aa4-111">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="29aa4-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="29aa4-112">如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="29aa4-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="29aa4-113">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來開發預存程序，以達到相同的目的。</span><span class="sxs-lookup"><span data-stu-id="29aa4-113">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="29aa4-114">下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="29aa4-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="29aa4-115">如需詳細資訊，請參閱[如何： 連接到資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="29aa4-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="29aa4-116">若要從資料庫刪除資料列</span><span class="sxs-lookup"><span data-stu-id="29aa4-116">To delete a row in the database</span></span>  
  
1.  <span data-ttu-id="29aa4-117">查詢資料庫，以找出要刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="29aa4-117">Query the database for the row to be deleted.</span></span>  
  
2.  <span data-ttu-id="29aa4-118">呼叫 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="29aa4-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>  
  
3.  <span data-ttu-id="29aa4-119">將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="29aa4-119">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29aa4-120">範例</span><span class="sxs-lookup"><span data-stu-id="29aa4-120">Example</span></span>  
 <span data-ttu-id="29aa4-121">下列第一個程式碼範例會查詢資料庫中屬於訂單 #11000 的訂單明細、將這些訂單明細標示為刪除，然後將這些變更送出至資料庫。</span><span class="sxs-lookup"><span data-stu-id="29aa4-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="29aa4-122">範例</span><span class="sxs-lookup"><span data-stu-id="29aa4-122">Example</span></span>  
 <span data-ttu-id="29aa4-123">在下列第二個範例中，目標是要移除某張訂單 (#10250)。</span><span class="sxs-lookup"><span data-stu-id="29aa4-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="29aa4-124">這段程式碼會先檢查 `OrderDetails` 資料表，查看要移除的訂單是否在該處有子系。</span><span class="sxs-lookup"><span data-stu-id="29aa4-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="29aa4-125">如果訂單有子系，則會先將子系標示為移除，再將訂單標示為移除。</span><span class="sxs-lookup"><span data-stu-id="29aa4-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="29aa4-126"><xref:System.Data.Linq.DataContext> 會將實際的刪除放置在正確的訂單中，使傳送到資料庫的刪除命令得以遵守資料庫條件約束。</span><span class="sxs-lookup"><span data-stu-id="29aa4-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="29aa4-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="29aa4-127">See Also</span></span>  
 [<span data-ttu-id="29aa4-128">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="29aa4-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="29aa4-129">如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="29aa4-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="29aa4-130">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="29aa4-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
