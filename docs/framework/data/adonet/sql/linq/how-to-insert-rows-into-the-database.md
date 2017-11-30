---
title: "如何：將資料列插入至資料庫"
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
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a96a0ab800076db16022f5b02c84d7a53ca99147
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="d69d6-102">如何：將資料列插入至資料庫</span><span class="sxs-lookup"><span data-stu-id="d69d6-102">How to: Insert Rows Into the Database</span></span>
<span data-ttu-id="d69d6-103">您將資料列插入資料庫將物件加入至相關聯[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Table%601>集合，然後將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d69d6-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d69d6-104">將轉譯成適當的 SQL 變更`INSERT`命令。</span><span class="sxs-lookup"><span data-stu-id="d69d6-104"> translates your changes into the appropriate SQL `INSERT` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d69d6-105">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="d69d6-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="d69d6-106">如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="d69d6-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="d69d6-107">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來開發預存程序，以達到相同的目的。</span><span class="sxs-lookup"><span data-stu-id="d69d6-107">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="d69d6-108">下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d69d6-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="d69d6-109">如需詳細資訊，請參閱[如何： 連接到資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="d69d6-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="d69d6-110">若要將資料列插入至資料庫</span><span class="sxs-lookup"><span data-stu-id="d69d6-110">To insert a row into the database</span></span>  
  
1.  <span data-ttu-id="d69d6-111">建立包含所要提交之資料欄資料的新物件。</span><span class="sxs-lookup"><span data-stu-id="d69d6-111">Create a new object that includes the column data to be submitted.</span></span>  
  
2.  <span data-ttu-id="d69d6-112">將新的物件加入[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]`Table`資料庫之目標資料表相關聯的集合。</span><span class="sxs-lookup"><span data-stu-id="d69d6-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>  
  
3.  <span data-ttu-id="d69d6-113">將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d69d6-113">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d69d6-114">範例</span><span class="sxs-lookup"><span data-stu-id="d69d6-114">Example</span></span>  
 <span data-ttu-id="d69d6-115">下列程式碼範例會建立 `Order` 型別的新物件，並且以適當的值填入 (Populate) 其中。</span><span class="sxs-lookup"><span data-stu-id="d69d6-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="d69d6-116">然後，將新物件加入至 `Order` 集合中。</span><span class="sxs-lookup"><span data-stu-id="d69d6-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="d69d6-117">最後，將變更當做 `Orders` 資料表中的新資料列，提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d69d6-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d69d6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d69d6-118">See Also</span></span>  
 [<span data-ttu-id="d69d6-119">如何： 管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="d69d6-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="d69d6-120">DataContext 方法 （O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="d69d6-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="d69d6-121">如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="d69d6-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="d69d6-122">建立和提交資料變更</span><span class="sxs-lookup"><span data-stu-id="d69d6-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
