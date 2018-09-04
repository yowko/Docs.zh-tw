---
title: 在 DataTable 中操作資料
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: a09edc6ce3098ab135d8c27ba0f6ad56cceed159
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521304"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="dd0f9-102">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="dd0f9-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="dd0f9-103">當您在 <xref:System.Data.DataTable> 中建立 <xref:System.Data.DataSet> 後，您可以執行的活動會與在資料庫中使用資料表的活動相同。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="dd0f9-104">您可以加入、檢視、編輯和刪除資料表的資料、監視錯誤和事件，以及查詢資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="dd0f9-105">在修改資料時**DataTable**，您也可以確認變更是否正確，並判斷是否要以程式設計的方式接受或拒絕變更。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd0f9-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="dd0f9-106">In This Section</span></span>  
 [<span data-ttu-id="dd0f9-107">將資料新增至 DataTable</span><span class="sxs-lookup"><span data-stu-id="dd0f9-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="dd0f9-108">說明如何建立新資料列並將之加入到資料表。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="dd0f9-109">在 DataTable 中檢視資料</span><span class="sxs-lookup"><span data-stu-id="dd0f9-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="dd0f9-110">說明如何存取資料列的資料，包括原始和目前版本的資料。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="dd0f9-111">Load 方法</span><span class="sxs-lookup"><span data-stu-id="dd0f9-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="dd0f9-112">說明如何使用**負載**方法來填滿**DataTable**與資料列。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="dd0f9-113">DataTable 編輯</span><span class="sxs-lookup"><span data-stu-id="dd0f9-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="dd0f9-114">說明如何修改資料列中的資料，包括暫停資料列的變更，直到建議的變更已經過驗證並接受為止。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="dd0f9-115">資料列狀態和資料列版本</span><span class="sxs-lookup"><span data-stu-id="dd0f9-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="dd0f9-116">提供資料列之不同狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="dd0f9-117">刪除 DataRow</span><span class="sxs-lookup"><span data-stu-id="dd0f9-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="dd0f9-118">說明如何從資料表移除資料列。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="dd0f9-119">資料列錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="dd0f9-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="dd0f9-120">說明如何插入每個資料列的錯誤資訊，協助解決應用程式中的資料問題。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="dd0f9-121">AcceptChanges 和 RejectChanges</span><span class="sxs-lookup"><span data-stu-id="dd0f9-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="dd0f9-122">說明如何接受或拒絕資料列的變更。</span><span class="sxs-lookup"><span data-stu-id="dd0f9-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0f9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd0f9-123">See Also</span></span>  
 [<span data-ttu-id="dd0f9-124">DataTable</span><span class="sxs-lookup"><span data-stu-id="dd0f9-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="dd0f9-125">處理 DataTable 事件</span><span class="sxs-lookup"><span data-stu-id="dd0f9-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="dd0f9-126">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="dd0f9-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
