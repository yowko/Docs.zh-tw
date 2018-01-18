---
title: "DataSet、DataTable 和 DataView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fb8cf2c9f763ea32bb7c7907111fea80e542a7f7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="b6194-102">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="b6194-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="b6194-103">ADO.NET <xref:System.Data.DataSet> 是以常駐記憶體表示的資料，不論內含資料來源為何，都可提供一致的關聯式程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="b6194-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="b6194-104"><xref:System.Data.DataSet> 表示一組完整的資料，包括內含、排序和約束資料的資料表，以及資料表間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b6194-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="b6194-105"><xref:System.Data.DataSet> 的使用方式有幾種，可以獨立或組合套用。</span><span class="sxs-lookup"><span data-stu-id="b6194-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="b6194-106">您可以：</span><span class="sxs-lookup"><span data-stu-id="b6194-106">You can:</span></span>  
  
-   <span data-ttu-id="b6194-107">以程式設計方式在 <xref:System.Data.DataTable> 內建立 <xref:System.Data.DataRelation>、<xref:System.Data.Constraint> 和 <xref:System.Data.DataSet>，並填入資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="b6194-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="b6194-108">使用 <xref:System.Data.DataSet>，將來自現有關聯式資料來源之資料的資料表填入 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="b6194-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="b6194-109">使用 XML 載入並保存 <xref:System.Data.DataSet> 內容。</span><span class="sxs-lookup"><span data-stu-id="b6194-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="b6194-110">如需詳細資訊，請參閱[在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="b6194-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="b6194-111">也可以使用 XML Web Service 傳輸強型別的 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="b6194-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="b6194-112"><xref:System.Data.DataSet> 的設計非常適合使用 XML Web Service 來傳輸資料。</span><span class="sxs-lookup"><span data-stu-id="b6194-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="b6194-113">如需 XML Web Service 的概觀，請參閱 [XML Web Service 概觀](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)。</span><span class="sxs-lookup"><span data-stu-id="b6194-113">For an overview of XML Web services, see [XML Web Services Overview](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="b6194-114">如需使用來自 XML Web Service 之 <xref:System.Data.DataSet> 的範例，請參閱[從 XML Web Service 使用 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="b6194-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6194-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="b6194-115">In This Section</span></span>  
 [<span data-ttu-id="b6194-116">建立 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6194-116">Creating a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 <span data-ttu-id="b6194-117">說明建立 <xref:System.Data.DataSet> 執行個體的語法。</span><span class="sxs-lookup"><span data-stu-id="b6194-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="b6194-118">將 DataTable 新增至 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6194-118">Adding a DataTable to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="b6194-119">說明如何建立資料表和資料行，並將它們加入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="b6194-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="b6194-120">新增 DataRelation</span><span class="sxs-lookup"><span data-stu-id="b6194-120">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 <span data-ttu-id="b6194-121">說明如何在 <xref:System.Data.DataSet> 的資料表之間建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="b6194-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="b6194-122">巡覽 DataRelation</span><span class="sxs-lookup"><span data-stu-id="b6194-122">Navigating DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 <span data-ttu-id="b6194-123">說明如何使用 <xref:System.Data.DataSet> 之資料表間的關聯性，傳回父子關係的子資料列或父資料列。</span><span class="sxs-lookup"><span data-stu-id="b6194-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="b6194-124">合併 DataSet 內容</span><span class="sxs-lookup"><span data-stu-id="b6194-124">Merging DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 <span data-ttu-id="b6194-125">說明如何將一個 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 陣列的內容合併到另一個 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="b6194-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="b6194-126">複製 DataSet 內容</span><span class="sxs-lookup"><span data-stu-id="b6194-126">Copying DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 <span data-ttu-id="b6194-127">說明如何建立 <xref:System.Data.DataSet> 的複本，而此複本包含結構描述和指定的資料。</span><span class="sxs-lookup"><span data-stu-id="b6194-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="b6194-128">處理 DataSet 的事件</span><span class="sxs-lookup"><span data-stu-id="b6194-128">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 <span data-ttu-id="b6194-129">說明 <xref:System.Data.DataSet> 的事件和使用方式。</span><span class="sxs-lookup"><span data-stu-id="b6194-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="b6194-130">具類型的 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6194-130">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 <span data-ttu-id="b6194-131">說明何謂具型別的 <xref:System.Data.DataSet> 以及它們的建立和使用方式。</span><span class="sxs-lookup"><span data-stu-id="b6194-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="b6194-132">DataTable</span><span class="sxs-lookup"><span data-stu-id="b6194-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="b6194-133">說明如何建立 <xref:System.Data.DataTable>、定義結構描述，以及管理資料。</span><span class="sxs-lookup"><span data-stu-id="b6194-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="b6194-134">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="b6194-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="b6194-135">說明如何建立及使用 <xref:System.Data.DataTableReader>。</span><span class="sxs-lookup"><span data-stu-id="b6194-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="b6194-136">DataView</span><span class="sxs-lookup"><span data-stu-id="b6194-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="b6194-137">說明如何建立並使用 `DataViews`，以及使用 <xref:System.Data.DataView> 事件。</span><span class="sxs-lookup"><span data-stu-id="b6194-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="b6194-138">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="b6194-138">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="b6194-139">說明 <xref:System.Data.DataSet> 如何將 XML 當成資料來源進行互動，包括將 <xref:System.Data.DataSet> 的內容載入和保存為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="b6194-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="b6194-140">從 XML Web Service 使用 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6194-140">Consuming a DataSet from an XML Web Service</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="b6194-141">說明如何建立可透過 <xref:System.Data.DataSet> 傳輸資料的 XML Web Service。</span><span class="sxs-lookup"><span data-stu-id="b6194-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b6194-142">相關章節</span><span class="sxs-lookup"><span data-stu-id="b6194-142">Related Sections</span></span>  
 [<span data-ttu-id="b6194-143">ADO.NET 的新功能</span><span class="sxs-lookup"><span data-stu-id="b6194-143">What's New in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="b6194-144">簡介 ADO.NET 的新功能。</span><span class="sxs-lookup"><span data-stu-id="b6194-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="b6194-145">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="b6194-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="b6194-146">提供 ADO.NET 的設計和元件的簡介。</span><span class="sxs-lookup"><span data-stu-id="b6194-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="b6194-147">從 DataAdapter 填入 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6194-147">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="b6194-148">描述如何自資料來源載入具有資料的 **DataSet**。</span><span class="sxs-lookup"><span data-stu-id="b6194-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="b6194-149">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="b6194-149">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="b6194-150">描述如何將 **DataSet** 中的資料變更解析回資料來源。</span><span class="sxs-lookup"><span data-stu-id="b6194-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="b6194-151">將現有條件約束新增至 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6194-151">Adding Existing Constraints to a DataSet</span></span>](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="b6194-152">描述如何將來自資料來源的主索引鍵資訊填入 **DataSet**。</span><span class="sxs-lookup"><span data-stu-id="b6194-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6194-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6194-153">See Also</span></span>  
 [<span data-ttu-id="b6194-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6194-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="b6194-155">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b6194-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
