---
title: "變更資料和提交"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d4f1a2a3f64302e1ef65bb341d56832a5fd93e82
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="2b044-102">變更資料和提交</span><span class="sxs-lookup"><span data-stu-id="2b044-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="2b044-103">本節中的主題描述如何變更資料庫以及將變更傳輸至資料庫，以及如何處理開放式並行存取 (Optimistic Concurrency) 衝突。</span><span class="sxs-lookup"><span data-stu-id="2b044-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b044-104">您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="2b044-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="2b044-105">如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="2b044-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="2b044-106">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來開發預存程序，以達到相同的目的。</span><span class="sxs-lookup"><span data-stu-id="2b044-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b044-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="2b044-107">In This Section</span></span>  
 [<span data-ttu-id="2b044-108">如何：將資料列插入至資料庫</span><span class="sxs-lookup"><span data-stu-id="2b044-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="2b044-109">描述如何將物件加入至物件模型，以在資料庫中插入資料列。</span><span class="sxs-lookup"><span data-stu-id="2b044-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="2b044-110">如何：更新資料庫中的資料列</span><span class="sxs-lookup"><span data-stu-id="2b044-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="2b044-111">描述如何更新物件模型中的物件，以更新資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="2b044-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="2b044-112">如何：從資料庫刪除資料列</span><span class="sxs-lookup"><span data-stu-id="2b044-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="2b044-113">描述如何刪除物件模型中的物件，以刪除資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="2b044-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="2b044-114">如何：將變更提交至資料庫</span><span class="sxs-lookup"><span data-stu-id="2b044-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="2b044-115">描述如何將物件模型變更傳送至資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b044-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="2b044-116">如何：使用異動括住提交的資料</span><span class="sxs-lookup"><span data-stu-id="2b044-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="2b044-117">描述如何在異動中包括作業。</span><span class="sxs-lookup"><span data-stu-id="2b044-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="2b044-118">如何：動態建立資料庫</span><span class="sxs-lookup"><span data-stu-id="2b044-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="2b044-119">描述如何動態產生資料庫，以及這種方法的一般案例。</span><span class="sxs-lookup"><span data-stu-id="2b044-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="2b044-120">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="2b044-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="2b044-121">描述解決開放式並行存取 (Optimistic Concurrency) 問題的技術。</span><span class="sxs-lookup"><span data-stu-id="2b044-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
