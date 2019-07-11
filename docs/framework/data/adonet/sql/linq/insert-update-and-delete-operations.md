---
title: 插入、更新和刪除作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fa3690ae74869f5dc0fbaa8d824d4aebca8ce724
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743063"
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="3d7de-102">插入、更新和刪除作業</span><span class="sxs-lookup"><span data-stu-id="3d7de-102">Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="3d7de-103">您可以加入、變更和移除物件模型 (Object Model) 中的物件，以便在 `Insert` 中執行 `Update`、`Delete` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 作業。</span><span class="sxs-lookup"><span data-stu-id="3d7de-103">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="3d7de-104">根據預設，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您的動作轉譯成 SQL 並將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="3d7de-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3d7de-105">提供最大的彈性，操作和保存您對物件所做的變更。</span><span class="sxs-lookup"><span data-stu-id="3d7de-105">offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="3d7de-106">一旦取得實體物件 (透過查詢加以擷取或重新加以建構)，您就可以將它們變更為應用程式中的典型物件。</span><span class="sxs-lookup"><span data-stu-id="3d7de-106">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="3d7de-107">也就是您可以變更其值，您可以將它們加入集合中，和您可以移除您的集合。</span><span class="sxs-lookup"><span data-stu-id="3d7de-107">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3d7de-108">會追蹤這些變更，而且在您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時準備好將變更傳送回資料庫。</span><span class="sxs-lookup"><span data-stu-id="3d7de-108">tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3d7de-109">不支援或辨識串聯 (Cascade) 刪除作業。</span><span class="sxs-lookup"><span data-stu-id="3d7de-109">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="3d7de-110">如果您想要刪除有限制式之資料表中的資料列，您必須設定`ON DELETE CASCADE`在資料庫中，外部索引鍵條件約束中的規則，或使用您自己的程式碼先刪除使父物件被刪除的子物件。</span><span class="sxs-lookup"><span data-stu-id="3d7de-110">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="3d7de-111">否則，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3d7de-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="3d7de-112">如需詳細資訊，請參閱[如何：從資料庫刪除資料列](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)。</span><span class="sxs-lookup"><span data-stu-id="3d7de-112">For more information, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="3d7de-113">下列摘錄會使用 Northwind 範例資料庫中的 `Customer` 和 `Order` 類別。</span><span class="sxs-lookup"><span data-stu-id="3d7de-113">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="3d7de-114">為了簡單起見，並不會顯示類別定義。</span><span class="sxs-lookup"><span data-stu-id="3d7de-114">Class definitions are not shown for brevity.</span></span>  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 <span data-ttu-id="3d7de-115">當您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會自動產生及執行必要的 SQL 命令，以便將變更傳送回資料庫。</span><span class="sxs-lookup"><span data-stu-id="3d7de-115">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d7de-116">您通常可以透過預存程序 (Stored Procedure)，使用自訂邏輯來覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="3d7de-116">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="3d7de-117">如需詳細資訊，請參閱 <<c0> [ 開發人員在覆寫預設行為的責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="3d7de-117">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>  
>   
>  <span data-ttu-id="3d7de-118">使用 Visual Studio 的開發人員可以使用物件關聯式設計工具來開發預存程序，針對此目的。</span><span class="sxs-lookup"><span data-stu-id="3d7de-118">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for this purpose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d7de-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d7de-119">See also</span></span>

- [<span data-ttu-id="3d7de-120">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="3d7de-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="3d7de-121">自訂插入、更新和刪除作業</span><span class="sxs-lookup"><span data-stu-id="3d7de-121">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
