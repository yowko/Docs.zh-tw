---
title: 變更資料和提交
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 23dc45c990763e69b41608f6c3ec15a8db17bf23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743004"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="d76fa-102">變更資料和提交</span><span class="sxs-lookup"><span data-stu-id="d76fa-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="d76fa-103">本節中的主題描述如何變更資料庫以及將變更傳輸至資料庫，以及如何處理開放式並行存取 (Optimistic Concurrency) 衝突。</span><span class="sxs-lookup"><span data-stu-id="d76fa-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d76fa-104">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="d76fa-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="d76fa-105">如需詳細資訊，請參閱 <<c0> [ 自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="d76fa-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="d76fa-106">使用 Visual Studio 的開發人員可以使用物件關聯式設計工具來開發預存程序，針對相同目的。</span><span class="sxs-lookup"><span data-stu-id="d76fa-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d76fa-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="d76fa-107">In This Section</span></span>  
 [<span data-ttu-id="d76fa-108">如何：將資料列插入資料庫</span><span class="sxs-lookup"><span data-stu-id="d76fa-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="d76fa-109">描述如何將物件加入至物件模型，以在資料庫中插入資料列。</span><span class="sxs-lookup"><span data-stu-id="d76fa-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="d76fa-110">如何：更新資料庫中的資料列</span><span class="sxs-lookup"><span data-stu-id="d76fa-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="d76fa-111">描述如何更新物件模型中的物件，以更新資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="d76fa-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="d76fa-112">如何：從資料庫刪除資料列</span><span class="sxs-lookup"><span data-stu-id="d76fa-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="d76fa-113">描述如何刪除物件模型中的物件，以刪除資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="d76fa-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="d76fa-114">如何：將變更提交至資料庫</span><span class="sxs-lookup"><span data-stu-id="d76fa-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="d76fa-115">描述如何將物件模型變更傳送至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d76fa-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="d76fa-116">如何：使用異動括住資料提交內容</span><span class="sxs-lookup"><span data-stu-id="d76fa-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="d76fa-117">描述如何在異動中包括作業。</span><span class="sxs-lookup"><span data-stu-id="d76fa-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="d76fa-118">如何：動態建立資料庫</span><span class="sxs-lookup"><span data-stu-id="d76fa-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="d76fa-119">描述如何動態產生資料庫，以及這種方法的一般案例。</span><span class="sxs-lookup"><span data-stu-id="d76fa-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="d76fa-120">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="d76fa-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="d76fa-121">描述解決開放式並行存取 (Optimistic Concurrency) 問題的技術。</span><span class="sxs-lookup"><span data-stu-id="d76fa-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
