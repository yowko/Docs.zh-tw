---
title: 如何：更新資料庫中的資料列
description: 瞭解如何藉由修改資料表相關集合中 LINQ to SQL 物件，來更新資料庫中的資料列。 LINQ to SQL 會將新增專案轉譯為 SQL UPDATE 命令。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286335"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="d8eb2-104">如何：更新資料庫中的資料列</span><span class="sxs-lookup"><span data-stu-id="d8eb2-104">How to: Update Rows in the Database</span></span>

<span data-ttu-id="d8eb2-105">您可以修改與集合相關聯之物件的成員值 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ，然後將變更提交至資料庫，藉以更新資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-105">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d8eb2-106">將您的變更轉譯成適當的 SQL `UPDATE` 命令。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-106">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="d8eb2-107">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="d8eb2-108">如需詳細資訊，請參閱[自訂插入、更新和刪除作業](customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="d8eb2-109">使用 Visual Studio 的開發人員可以使用物件關聯式設計工具，針對相同的目的來開發預存程式。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="d8eb2-110">下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="d8eb2-111">如需詳細資訊，請參閱[如何：連接到資料庫](how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="d8eb2-112">若要更新資料庫中的資料列</span><span class="sxs-lookup"><span data-stu-id="d8eb2-112">To update a row in the database</span></span>

1. <span data-ttu-id="d8eb2-113">查詢資料庫，以找出要更新的資料列。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-113">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="d8eb2-114">對結果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件中的成員值進行所需的變更。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-114">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="d8eb2-115">將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-115">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="d8eb2-116">範例</span><span class="sxs-lookup"><span data-stu-id="d8eb2-116">Example</span></span>

<span data-ttu-id="d8eb2-117">下列程式碼範例會查詢資料庫中的訂單編號 11000，然後變更結果 `ShipName` 物件中 `ShipVia` 和 `Order` 的值。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-117">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="d8eb2-118">最後，這些成員值的變更會提交至資料庫，成為 `ShipName` 和 `ShipVia` 資料行的變更。</span><span class="sxs-lookup"><span data-stu-id="d8eb2-118">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="d8eb2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8eb2-119">See also</span></span>

- [<span data-ttu-id="d8eb2-120">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="d8eb2-120">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="d8eb2-121">如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="d8eb2-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="d8eb2-122">變更資料和提交</span><span class="sxs-lookup"><span data-stu-id="d8eb2-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
