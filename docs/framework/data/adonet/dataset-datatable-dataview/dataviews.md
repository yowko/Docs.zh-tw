---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 1b202af052c05ed9dc671fa20c9c366f280ec5c7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774170"
---
# <a name="dataviews"></a><span data-ttu-id="416da-102">DataView</span><span class="sxs-lookup"><span data-stu-id="416da-102">DataViews</span></span>
<span data-ttu-id="416da-103"><xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。</span><span class="sxs-lookup"><span data-stu-id="416da-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="416da-104">您可以使用**DataView**，以不同的排序次序來公開資料表中的資料，而且您可以依資料列狀態或根據篩選運算式來篩選資料。</span><span class="sxs-lookup"><span data-stu-id="416da-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>

 <span data-ttu-id="416da-105">**DataView**提供基礎**DataTable**中資料的動態視圖：內容、排序和成員資格會反映發生的變更。</span><span class="sxs-lookup"><span data-stu-id="416da-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="416da-106">此行為不同于**DataTable**的**Select**方法，它會根據特定篩選和/或排序次序，從資料表傳回 <xref:System.Data.DataRow> 陣列：此內容反映基礎資料表的變更，但其成員資格和順序保持靜態。</span><span class="sxs-lookup"><span data-stu-id="416da-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: this content reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="416da-107">**DataView**的動態功能讓資料系結應用程式非常理想。</span><span class="sxs-lookup"><span data-stu-id="416da-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>

 <span data-ttu-id="416da-108">**DataView**提供您單一資料集的動態觀點，與資料庫的觀點相似，您可以套用不同的排序和篩選準則。</span><span class="sxs-lookup"><span data-stu-id="416da-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="416da-109">不過，不同于資料庫檢視， **DataView**無法被視為資料表，而且無法提供聯結資料表的觀點。</span><span class="sxs-lookup"><span data-stu-id="416da-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="416da-110">您也無法排除存在於來源資料表中的資料行，或附加不存在於來源資料表中的資料行，例如計算資料行。</span><span class="sxs-lookup"><span data-stu-id="416da-110">You also cannot exclude columns that exist in the source table or append columns that do not exist in the source table, such as computational columns.</span></span>

 <span data-ttu-id="416da-111">您可以使用 <xref:System.Data.DataView.DataViewManager%2A> 來管理**資料集中**所有資料表的視圖設定。</span><span class="sxs-lookup"><span data-stu-id="416da-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="416da-112">**DataViewManager**提供便利的方式來管理每個資料表的預設 view 設定。</span><span class="sxs-lookup"><span data-stu-id="416da-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="416da-113">將控制項系結至**資料集**的多個資料表時，系結至**DataViewManager**是理想的選擇。</span><span class="sxs-lookup"><span data-stu-id="416da-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="416da-114">本章節內容</span><span class="sxs-lookup"><span data-stu-id="416da-114">In This Section</span></span>
 <span data-ttu-id="416da-115">[建立 DataView](creating-a-dataview.md)描述如何建立**DataTable**的**DataView** 。</span><span class="sxs-lookup"><span data-stu-id="416da-115">[Creating a DataView](creating-a-dataview.md) Describes how to create a **DataView** for a **DataTable**.</span></span>

 <span data-ttu-id="416da-116">[排序和篩選資料](sorting-and-filtering-data.md)描述如何設定**DataView**的屬性，以傳回符合特定篩選準則的資料列子集，或傳回特定排序次序的資料。</span><span class="sxs-lookup"><span data-stu-id="416da-116">[Sorting and Filtering Data](sorting-and-filtering-data.md) Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>

 <span data-ttu-id="416da-117">[Datarow 和 datarowview](datarows-and-datarowviews.md)描述如何存取**DataView**所公開的資料。</span><span class="sxs-lookup"><span data-stu-id="416da-117">[DataRows and DataRowViews](datarows-and-datarowviews.md) Describes how to access the data exposed by the **DataView**.</span></span>

 <span data-ttu-id="416da-118">[尋找資料列](finding-rows.md)描述如何尋找**DataView**中的特定資料列。</span><span class="sxs-lookup"><span data-stu-id="416da-118">[Finding Rows](finding-rows.md) Describes how to find a particular row in a **DataView**.</span></span>

 <span data-ttu-id="416da-119">[子檢視和](childviews-and-relations.md)關聯描述如何使用**DataView**建立來自父子式關聯性的資料檢視。</span><span class="sxs-lookup"><span data-stu-id="416da-119">[ChildViews and Relations](childviews-and-relations.md) Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>

 <span data-ttu-id="416da-120">[修改 dataview](modifying-dataviews.md)描述如何透過**DataView**修改基礎**DataTable**中的資料，包括啟用或停用更新。</span><span class="sxs-lookup"><span data-stu-id="416da-120">[Modifying DataViews](modifying-dataviews.md) Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>

 <span data-ttu-id="416da-121">[處理 DataView 事件](handling-dataview-events.md)描述當**DataView**的內容或順序更新時，如何使用**ListChanged**事件來接收通知。</span><span class="sxs-lookup"><span data-stu-id="416da-121">[Handling DataView Events](handling-dataview-events.md) Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>

 <span data-ttu-id="416da-122">[管理 dataview](managing-dataviews.md)描述如何使用**DataViewManager**來管理**資料集**內每個資料表的**DataView**設定。</span><span class="sxs-lookup"><span data-stu-id="416da-122">[Managing DataViews](managing-dataviews.md) Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>

## <a name="related-sections"></a><span data-ttu-id="416da-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="416da-123">Related Sections</span></span>
 <span data-ttu-id="416da-124">[ASP.NET Web 應用程式](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))提供建立 ASP.NET 應用程式、Web form 和 Web 服務的概覽和詳細逐步程式。</span><span class="sxs-lookup"><span data-stu-id="416da-124">[ASP.NET Web Applications](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100)) Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>

 <span data-ttu-id="416da-125">[Windows 應用程式](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))提供有關使用 Windows Forms 和主控台應用程式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="416da-125">[Windows Applications](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100)) Provides detailed information about working with Windows Forms and console applications.</span></span>

 <span data-ttu-id="416da-126">[Dataset、datatable 和 dataview](index.md)描述**DataSet**物件，以及您可以如何使用它來管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="416da-126">[DataSets, DataTables, and DataViews](index.md) Describes the **DataSet** object and how you can use it to manage application data.</span></span>

 <span data-ttu-id="416da-127">[Datatable](datatables.md)描述**DataTable**物件，以及如何使用它來管理應用程式資料本身，或做為**資料集**的一部分。</span><span class="sxs-lookup"><span data-stu-id="416da-127">[DataTables](datatables.md) Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>

 <span data-ttu-id="416da-128">[ADO.NET](../index.md)描述 ADO.NET 架構和元件，以及如何使用 ADO.NET 來存取現有的資料來源和管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="416da-128">[ADO.NET](../index.md) Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>

## <a name="see-also"></a><span data-ttu-id="416da-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="416da-129">See also</span></span>

- [<span data-ttu-id="416da-130">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="416da-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
