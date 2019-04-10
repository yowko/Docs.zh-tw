---
title: HOW TO：將資料列插入至資料庫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: cb2319d51e0518114a04eea2fc7ab6b5a836b7ff
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328591"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="38775-102">HOW TO：將資料列插入至資料庫</span><span class="sxs-lookup"><span data-stu-id="38775-102">How to: Insert Rows Into the Database</span></span>
<span data-ttu-id="38775-103">您將資料列插入資料庫將物件新增至相關聯[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Table%601>集合，然後將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="38775-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="38775-104">會轉譯成適當的 SQL 變更`INSERT`命令。</span><span class="sxs-lookup"><span data-stu-id="38775-104">translates your changes into the appropriate SQL `INSERT` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38775-105">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="38775-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="38775-106">如需詳細資訊，請參閱 <<c0> [ 自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="38775-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="38775-107">使用 Visual Studio 的開發人員可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]來開發預存程序，針對相同目的。</span><span class="sxs-lookup"><span data-stu-id="38775-107">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="38775-108">下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="38775-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="38775-109">如需詳細資訊，請參閱[如何：連接到資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="38775-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="38775-110">若要將資料列插入至資料庫</span><span class="sxs-lookup"><span data-stu-id="38775-110">To insert a row into the database</span></span>  
  
1. <span data-ttu-id="38775-111">建立包含所要提交之資料欄資料的新物件。</span><span class="sxs-lookup"><span data-stu-id="38775-111">Create a new object that includes the column data to be submitted.</span></span>  
  
2. <span data-ttu-id="38775-112">將新的物件加入[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]`Table`資料庫之目標資料表相關聯的集合。</span><span class="sxs-lookup"><span data-stu-id="38775-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>  
  
3. <span data-ttu-id="38775-113">將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="38775-113">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38775-114">範例</span><span class="sxs-lookup"><span data-stu-id="38775-114">Example</span></span>  
 <span data-ttu-id="38775-115">下列程式碼範例會建立 `Order` 型別的新物件，並且以適當的值填入 (Populate) 其中。</span><span class="sxs-lookup"><span data-stu-id="38775-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="38775-116">然後，將新物件加入至 `Order` 集合中。</span><span class="sxs-lookup"><span data-stu-id="38775-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="38775-117">最後，將變更當做 `Orders` 資料表中的新資料列，提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="38775-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="38775-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38775-118">See also</span></span>

- [<span data-ttu-id="38775-119">HOW TO：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="38775-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="38775-120">DataContext 方法 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="38775-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="38775-121">HOW TO：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="38775-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="38775-122">變更資料和提交</span><span class="sxs-lookup"><span data-stu-id="38775-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
