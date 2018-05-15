---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: f3e5d047496785c34c1fe242853829ae0110dc2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="dataviews"></a><span data-ttu-id="476aa-102">DataView</span><span class="sxs-lookup"><span data-stu-id="476aa-102">DataViews</span></span>
<span data-ttu-id="476aa-103"><xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。</span><span class="sxs-lookup"><span data-stu-id="476aa-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="476aa-104">使用**DataView**可以公開資料表以不同排序順序中的資料，您可以依資料列狀態或根據篩選條件運算式來篩選資料。</span><span class="sxs-lookup"><span data-stu-id="476aa-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="476aa-105">A **DataView**提供在基礎資料的動態檢視**DataTable**： 內容、 排序和成員資格反映變更發生時。</span><span class="sxs-lookup"><span data-stu-id="476aa-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="476aa-106">此行為不同於**選取**方法**DataTable**，它會傳回<xref:System.Data.DataRow>陣列從一個資料表會根據特定篩選器和 （或） 排序順序： thiscontent 反映變更基礎資料表，但其成員資格和順序仍維持靜態。</span><span class="sxs-lookup"><span data-stu-id="476aa-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: thiscontent reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="476aa-107">動態功能**DataView**讓適用於資料繫結應用程式。</span><span class="sxs-lookup"><span data-stu-id="476aa-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="476aa-108">A **DataView**您提供一組資料，很像資料庫檢視，您可以套用不同的排序和篩選準則的動態檢視。</span><span class="sxs-lookup"><span data-stu-id="476aa-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="476aa-109">與資料庫檢視，不過，不同**DataView**無法視為資料表，也無法提供聯結資料表的檢視。</span><span class="sxs-lookup"><span data-stu-id="476aa-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="476aa-110">此外，您也不能排除來源資料表中的資料行，也不能附加來源資料表中不存在的資料行 (如計算資料行)。</span><span class="sxs-lookup"><span data-stu-id="476aa-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="476aa-111">您可以使用<xref:System.Data.DataView.DataViewManager%2A>管理中的所有資料表的檢視設定**資料集**。</span><span class="sxs-lookup"><span data-stu-id="476aa-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="476aa-112">**DataViewManager**您提供便於管理每個資料表的預設檢視設定的方式。</span><span class="sxs-lookup"><span data-stu-id="476aa-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="476aa-113">當控制項繫結至一個以上的資料表**資料集**繫結至**DataViewManager**是理想的選擇。</span><span class="sxs-lookup"><span data-stu-id="476aa-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="476aa-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="476aa-114">In This Section</span></span>  
 [<span data-ttu-id="476aa-115">建立 DataView</span><span class="sxs-lookup"><span data-stu-id="476aa-115">Creating a DataView</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 <span data-ttu-id="476aa-116">描述如何建立**DataView**如**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="476aa-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="476aa-117">排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="476aa-117">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 <span data-ttu-id="476aa-118">描述如何設定的屬性**DataView**符合特定篩選準則，傳回的資料列子集，或在特定排序順序傳回資料。</span><span class="sxs-lookup"><span data-stu-id="476aa-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="476aa-119">DataRow 和 DataRowView</span><span class="sxs-lookup"><span data-stu-id="476aa-119">DataRows and DataRowViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 <span data-ttu-id="476aa-120">描述如何存取資料所公開**DataView**。</span><span class="sxs-lookup"><span data-stu-id="476aa-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="476aa-121">尋找資料列</span><span class="sxs-lookup"><span data-stu-id="476aa-121">Finding Rows</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 <span data-ttu-id="476aa-122">描述如何尋找特定的資料列中**DataView**。</span><span class="sxs-lookup"><span data-stu-id="476aa-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="476aa-123">子檢視和關聯</span><span class="sxs-lookup"><span data-stu-id="476aa-123">ChildViews and Relations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 <span data-ttu-id="476aa-124">描述如何建立資料的檢視，從父子式關聯性，使用**DataView**。</span><span class="sxs-lookup"><span data-stu-id="476aa-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="476aa-125">修改 DataView</span><span class="sxs-lookup"><span data-stu-id="476aa-125">Modifying DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 <span data-ttu-id="476aa-126">描述如何修改在基礎資料**DataTable**透過**DataView**，包括啟用或停用更新。</span><span class="sxs-lookup"><span data-stu-id="476aa-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="476aa-127">處理 DataView 事件</span><span class="sxs-lookup"><span data-stu-id="476aa-127">Handling DataView Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 <span data-ttu-id="476aa-128">描述如何使用**ListChanged**接收通知的事件時的內容或順序**DataView**正在更新。</span><span class="sxs-lookup"><span data-stu-id="476aa-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="476aa-129">管理 DataView</span><span class="sxs-lookup"><span data-stu-id="476aa-129">Managing DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 <span data-ttu-id="476aa-130">描述如何使用**DataViewManager**管理**DataView**設定中每個資料表**資料集**。</span><span class="sxs-lookup"><span data-stu-id="476aa-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="476aa-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="476aa-131">Related Sections</span></span>  
 [<span data-ttu-id="476aa-132">ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="476aa-132">ASP.NET Web Applications</span></span>](http://msdn.microsoft.com/library/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 <span data-ttu-id="476aa-133">提供 ASP.NET 應用程式、Web Form 和 Web 服務的建立概觀和詳細的步驟程序。</span><span class="sxs-lookup"><span data-stu-id="476aa-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 [<span data-ttu-id="476aa-134">Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="476aa-134">Windows Applications</span></span>](http://msdn.microsoft.com/library/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 <span data-ttu-id="476aa-135">提供有關使用 Windows Form 和主控台應用程式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="476aa-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 [<span data-ttu-id="476aa-136">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="476aa-136">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="476aa-137">描述**資料集**物件及如何使用它來管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="476aa-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="476aa-138">DataTable</span><span class="sxs-lookup"><span data-stu-id="476aa-138">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="476aa-139">描述**DataTable**物件及如何使用它來管理應用程式資料，單獨使用或一部分**資料集**。</span><span class="sxs-lookup"><span data-stu-id="476aa-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="476aa-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="476aa-140">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="476aa-141">說明 ADO.NET 的架構和元件，以及如何使用 ADO.NET 來存取現有資料來源和管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="476aa-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476aa-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="476aa-142">See Also</span></span>  
 [<span data-ttu-id="476aa-143">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="476aa-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
