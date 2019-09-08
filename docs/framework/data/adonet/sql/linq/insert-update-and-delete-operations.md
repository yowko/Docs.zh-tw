---
title: 插入、更新和刪除作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fac89f905b85493bc0ec36a85635f369bb354266
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793053"
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="ce2d7-102">插入、更新和刪除作業</span><span class="sxs-lookup"><span data-stu-id="ce2d7-102">Insert, Update, and Delete Operations</span></span>

<span data-ttu-id="ce2d7-103">您可以加入、變更和移除物件模型 (Object Model) 中的物件，以便在 `Insert` 中執行 `Update`、`Delete` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 作業。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-103">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="ce2d7-104">根據預設，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您的動作轉譯成 SQL 並將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ce2d7-105">提供操作和保存您對物件所做變更的最大彈性。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-105">offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="ce2d7-106">一旦取得實體物件 (透過查詢加以擷取或重新加以建構)，您就可以將它們變更為應用程式中的典型物件。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-106">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="ce2d7-107">也就是說，您可以變更它們的值，您可以將它們新增至您的集合，也可以從集合中移除它們。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-107">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ce2d7-108">會追蹤這些變更，而且在您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時準備好將變更傳送回資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-108">tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ce2d7-109">不支援或辨識串聯 (Cascade) 刪除作業。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-109">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="ce2d7-110">如果您想要刪除具有條件約束之資料表中的資料列，您必須在資料庫的外`ON DELETE CASCADE`鍵條件約束中設定規則，或者使用您自己的程式碼，先刪除導致父物件無法刪除的子物件。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-110">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="ce2d7-111">否則，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="ce2d7-112">如需詳細資訊，請參閱[如何：從資料庫刪除資料](how-to-delete-rows-from-the-database.md)列。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-112">For more information, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>

<span data-ttu-id="ce2d7-113">下列摘錄會使用 Northwind 範例資料庫中的 `Customer` 和 `Order` 類別。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-113">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="ce2d7-114">為了簡單起見，並不會顯示類別定義。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-114">Class definitions are not shown for brevity.</span></span>

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

<span data-ttu-id="ce2d7-115">當您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會自動產生及執行必要的 SQL 命令，以便將變更傳送回資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-115">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>

> [!NOTE]
> <span data-ttu-id="ce2d7-116">您通常可以透過預存程序 (Stored Procedure)，使用自訂邏輯來覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-116">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="ce2d7-117">如需詳細資訊，請參閱[開發人員覆寫預設行為的責任](responsibilities-of-the-developer-in-overriding-default-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-117">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>
>
> <span data-ttu-id="ce2d7-118">使用 Visual Studio 的開發人員可以使用物件關聯式設計工具來開發用於此用途的預存程式。</span><span class="sxs-lookup"><span data-stu-id="ce2d7-118">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for this purpose.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce2d7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce2d7-119">See also</span></span>

- [<span data-ttu-id="ce2d7-120">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="ce2d7-120">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="ce2d7-121">自訂插入、更新和刪除作業</span><span class="sxs-lookup"><span data-stu-id="ce2d7-121">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
