---
title: 作法：將資料列插入至資料庫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: cb62522a951afd3a7159114d3b6575f1d83278bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743327"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="d65ee-102">HOW TO：將資料列插入至資料庫</span><span class="sxs-lookup"><span data-stu-id="d65ee-102">How to: Insert Rows Into the Database</span></span>
<span data-ttu-id="d65ee-103">您將資料列插入資料庫將物件新增至相關聯[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Table%601>集合，然後將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d65ee-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="d65ee-104">會轉譯成適當的 SQL 變更`INSERT`命令。</span><span class="sxs-lookup"><span data-stu-id="d65ee-104">translates your changes into the appropriate SQL `INSERT` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d65ee-105">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="d65ee-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="d65ee-106">如需詳細資訊，請參閱 <<c0> [ 自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="d65ee-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="d65ee-107">使用 Visual Studio 的開發人員可以使用物件關聯式設計工具來開發預存程序，針對相同目的。</span><span class="sxs-lookup"><span data-stu-id="d65ee-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="d65ee-108">下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d65ee-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="d65ee-109">如需詳細資訊，請參閱[如何：連接到資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="d65ee-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="d65ee-110">若要將資料列插入至資料庫</span><span class="sxs-lookup"><span data-stu-id="d65ee-110">To insert a row into the database</span></span>  
  
1. <span data-ttu-id="d65ee-111">建立包含所要提交之資料欄資料的新物件。</span><span class="sxs-lookup"><span data-stu-id="d65ee-111">Create a new object that includes the column data to be submitted.</span></span>  
  
2. <span data-ttu-id="d65ee-112">將新的物件加入[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]`Table`資料庫之目標資料表相關聯的集合。</span><span class="sxs-lookup"><span data-stu-id="d65ee-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>  
  
3. <span data-ttu-id="d65ee-113">將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d65ee-113">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d65ee-114">範例</span><span class="sxs-lookup"><span data-stu-id="d65ee-114">Example</span></span>  
 <span data-ttu-id="d65ee-115">下列程式碼範例會建立 `Order` 型別的新物件，並且以適當的值填入 (Populate) 其中。</span><span class="sxs-lookup"><span data-stu-id="d65ee-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="d65ee-116">然後，將新物件加入至 `Order` 集合中。</span><span class="sxs-lookup"><span data-stu-id="d65ee-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="d65ee-117">最後，將變更當做 `Orders` 資料表中的新資料列，提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d65ee-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d65ee-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d65ee-118">See also</span></span>

- [<span data-ttu-id="d65ee-119">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="d65ee-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="d65ee-120">DataContext 方法 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="d65ee-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="d65ee-121">如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="d65ee-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="d65ee-122">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="d65ee-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
