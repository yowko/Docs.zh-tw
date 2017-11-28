---
title: "如何：更新資料庫中的資料列"
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
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ba7d6369b534edf5e8c61605b09823a36143a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="0e585-102">如何：更新資料庫中的資料列</span><span class="sxs-lookup"><span data-stu-id="0e585-102">How to: Update Rows in the Database</span></span>
<span data-ttu-id="0e585-103">您可以藉由修改與相關聯之物件的成員值來更新資料庫中的資料列[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Table%601>集合，然後將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="0e585-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0e585-104">將轉譯成適當的 SQL 變更`UPDATE`命令。</span><span class="sxs-lookup"><span data-stu-id="0e585-104"> translates your changes into the appropriate SQL `UPDATE` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e585-105">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="0e585-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="0e585-106">如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="0e585-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="0e585-107">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來開發預存程序，以達到相同的目的。</span><span class="sxs-lookup"><span data-stu-id="0e585-107">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="0e585-108">下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0e585-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="0e585-109">如需詳細資訊，請參閱[如何： 連接到資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="0e585-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="0e585-110">若要更新資料庫中的資料列</span><span class="sxs-lookup"><span data-stu-id="0e585-110">To update a row in the database</span></span>  
  
1.  <span data-ttu-id="0e585-111">查詢資料庫，以找出要更新的資料列。</span><span class="sxs-lookup"><span data-stu-id="0e585-111">Query the database for the row to be updated.</span></span>  
  
2.  <span data-ttu-id="0e585-112">對結果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件中的成員值進行所需的變更。</span><span class="sxs-lookup"><span data-stu-id="0e585-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>  
  
3.  <span data-ttu-id="0e585-113">將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="0e585-113">Submit the changes to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e585-114">範例</span><span class="sxs-lookup"><span data-stu-id="0e585-114">Example</span></span>  
 <span data-ttu-id="0e585-115">下列程式碼範例會查詢資料庫中的訂單編號 11000，然後變更結果 `ShipName` 物件中 `ShipVia` 和 `Order` 的值。</span><span class="sxs-lookup"><span data-stu-id="0e585-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="0e585-116">最後，這些成員值的變更會提交至資料庫，成為 `ShipName` 和 `ShipVia` 資料行的變更。</span><span class="sxs-lookup"><span data-stu-id="0e585-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0e585-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e585-117">See Also</span></span>  
 [<span data-ttu-id="0e585-118">如何： 管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="0e585-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="0e585-119">如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="0e585-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="0e585-120">建立和提交資料變更</span><span class="sxs-lookup"><span data-stu-id="0e585-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
