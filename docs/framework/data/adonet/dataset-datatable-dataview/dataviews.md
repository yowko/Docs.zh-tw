---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 75719e91daba189c1d93491a1db26acc80100bea
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409166"
---
# <a name="dataviews"></a><span data-ttu-id="0283b-102">DataView</span><span class="sxs-lookup"><span data-stu-id="0283b-102">DataViews</span></span>
<span data-ttu-id="0283b-103"><xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。</span><span class="sxs-lookup"><span data-stu-id="0283b-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="0283b-104">使用**DataView**可以公開資料表以不同排序順序中的資料，您可以依資料列狀態或根據篩選條件運算式來篩選資料。</span><span class="sxs-lookup"><span data-stu-id="0283b-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="0283b-105">A **DataView**提供動態檢視的資料在基礎**DataTable**： 內容、 順序和成員資格反映的變更發生時。</span><span class="sxs-lookup"><span data-stu-id="0283b-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="0283b-106">此行為不同於**選取 **方法**DataTable**，以傳回<xref:System.Data.DataRow>特定的篩選和/或排序順序為基礎的資料表中的陣列： thiscontent 反映的變更基礎資料表，但其成員資格和順序仍維持靜態。</span><span class="sxs-lookup"><span data-stu-id="0283b-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: thiscontent reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="0283b-107">動態功能**DataView**適合用來資料繫結的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0283b-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="0283b-108">A **DataView**您提供一組資料，很像資料庫檢視，您可以套用不同的排序和篩選準則的動態檢視。</span><span class="sxs-lookup"><span data-stu-id="0283b-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="0283b-109">與資料庫檢視，不過，不同**DataView**無法被視為資料表，而無法提供聯結資料表的檢視。</span><span class="sxs-lookup"><span data-stu-id="0283b-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="0283b-110">此外，您也不能排除來源資料表中的資料行，也不能附加來源資料表中不存在的資料行 (如計算資料行)。</span><span class="sxs-lookup"><span data-stu-id="0283b-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="0283b-111">您可以使用<xref:System.Data.DataView.DataViewManager%2A>管理中的所有資料表的檢視設定**資料集**。</span><span class="sxs-lookup"><span data-stu-id="0283b-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="0283b-112">**DataViewManager**提供便利的方式來管理每個資料表的預設檢視設定。</span><span class="sxs-lookup"><span data-stu-id="0283b-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="0283b-113">將控制項繫結至多個資料表時**資料集**繫結至**DataViewManager**是理想的選擇。</span><span class="sxs-lookup"><span data-stu-id="0283b-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0283b-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="0283b-114">In This Section</span></span>  
 [<span data-ttu-id="0283b-115">建立 DataView</span><span class="sxs-lookup"><span data-stu-id="0283b-115">Creating a DataView</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 <span data-ttu-id="0283b-116">描述如何建立**DataView** for **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="0283b-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="0283b-117">排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="0283b-117">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 <span data-ttu-id="0283b-118">描述如何設定的屬性**DataView**符合特定篩選準則，傳回的資料列的子集，或以特定的排序順序傳回資料。</span><span class="sxs-lookup"><span data-stu-id="0283b-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="0283b-119">DataRow 和 DataRowView</span><span class="sxs-lookup"><span data-stu-id="0283b-119">DataRows and DataRowViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 <span data-ttu-id="0283b-120">描述如何存取所公開的資料**DataView**。</span><span class="sxs-lookup"><span data-stu-id="0283b-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="0283b-121">尋找資料列</span><span class="sxs-lookup"><span data-stu-id="0283b-121">Finding Rows</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 <span data-ttu-id="0283b-122">描述如何尋找特定資料列**DataView**。</span><span class="sxs-lookup"><span data-stu-id="0283b-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="0283b-123">子檢視和關聯</span><span class="sxs-lookup"><span data-stu-id="0283b-123">ChildViews and Relations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 <span data-ttu-id="0283b-124">描述如何建立從父子式關聯性使用的資料檢視**DataView**。</span><span class="sxs-lookup"><span data-stu-id="0283b-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="0283b-125">修改 DataView</span><span class="sxs-lookup"><span data-stu-id="0283b-125">Modifying DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 <span data-ttu-id="0283b-126">描述如何修改的資料在基礎**DataTable**透過**DataView**，包括啟用或停用更新。</span><span class="sxs-lookup"><span data-stu-id="0283b-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="0283b-127">處理 DataView 事件</span><span class="sxs-lookup"><span data-stu-id="0283b-127">Handling DataView Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 <span data-ttu-id="0283b-128">描述如何使用**ListChanged**事件，以接收通知時的內容或順序**DataView**正在更新。</span><span class="sxs-lookup"><span data-stu-id="0283b-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="0283b-129">管理 DataView</span><span class="sxs-lookup"><span data-stu-id="0283b-129">Managing DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 <span data-ttu-id="0283b-130">描述如何使用**DataViewManager**來管理**DataView**設定中每個資料表**資料集**。</span><span class="sxs-lookup"><span data-stu-id="0283b-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0283b-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="0283b-131">Related Sections</span></span>  
 [<span data-ttu-id="0283b-132">ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="0283b-132">ASP.NET Web Applications</span></span>](https://msdn.microsoft.com/library/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 <span data-ttu-id="0283b-133">提供 ASP.NET 應用程式、Web Form 和 Web 服務的建立概觀和詳細的步驟程序。</span><span class="sxs-lookup"><span data-stu-id="0283b-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 [<span data-ttu-id="0283b-134">Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="0283b-134">Windows Applications</span></span>](https://msdn.microsoft.com/library/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 <span data-ttu-id="0283b-135">提供有關使用 Windows Form 和主控台應用程式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0283b-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 [<span data-ttu-id="0283b-136">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="0283b-136">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="0283b-137">描述**資料集**物件及如何使用它來管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="0283b-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="0283b-138">DataTable</span><span class="sxs-lookup"><span data-stu-id="0283b-138">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="0283b-139">描述**DataTable**物件，以及如何使用它來管理應用程式資料本身，或做為一部分**DataSet**。</span><span class="sxs-lookup"><span data-stu-id="0283b-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="0283b-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0283b-140">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="0283b-141">說明 ADO.NET 的架構和元件，以及如何使用 ADO.NET 來存取現有資料來源和管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="0283b-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0283b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0283b-142">See Also</span></span>  
 [<span data-ttu-id="0283b-143">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0283b-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
