---
title: 作法：更新資料庫中的資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: 2819cd5d2533e8e289735c3df2b39df952968e66
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938725"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="439bb-102">作法：更新資料庫中的資料列</span><span class="sxs-lookup"><span data-stu-id="439bb-102">How to: Update Rows in the Database</span></span>
<span data-ttu-id="439bb-103">您可以修改與[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>集合相關聯之物件的成員值, 然後將變更提交至資料庫, 藉以更新資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="439bb-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="439bb-104">將您的變更轉譯成適當`UPDATE`的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="439bb-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="439bb-105">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="439bb-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="439bb-106">如需詳細資訊, 請參閱[自訂插入、更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="439bb-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="439bb-107">使用 Visual Studio 的開發人員可以使用物件關聯式設計工具, 針對相同的目的來開發預存程式。</span><span class="sxs-lookup"><span data-stu-id="439bb-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="439bb-108">下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="439bb-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="439bb-109">如需詳細資訊，請參閱[如何：連接到資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="439bb-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="439bb-110">若要更新資料庫中的資料列</span><span class="sxs-lookup"><span data-stu-id="439bb-110">To update a row in the database</span></span>  
  
1. <span data-ttu-id="439bb-111">查詢資料庫，以找出要更新的資料列。</span><span class="sxs-lookup"><span data-stu-id="439bb-111">Query the database for the row to be updated.</span></span>  
  
2. <span data-ttu-id="439bb-112">對結果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件中的成員值進行所需的變更。</span><span class="sxs-lookup"><span data-stu-id="439bb-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>  
  
3. <span data-ttu-id="439bb-113">將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="439bb-113">Submit the changes to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="439bb-114">範例</span><span class="sxs-lookup"><span data-stu-id="439bb-114">Example</span></span>  
 <span data-ttu-id="439bb-115">下列程式碼範例會查詢資料庫中的訂單編號 11000，然後變更結果 `ShipName` 物件中 `ShipVia` 和 `Order` 的值。</span><span class="sxs-lookup"><span data-stu-id="439bb-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="439bb-116">最後，這些成員值的變更會提交至資料庫，成為 `ShipName` 和 `ShipVia` 資料行的變更。</span><span class="sxs-lookup"><span data-stu-id="439bb-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="439bb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="439bb-117">See also</span></span>

- [<span data-ttu-id="439bb-118">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="439bb-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="439bb-119">如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="439bb-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="439bb-120">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="439bb-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
