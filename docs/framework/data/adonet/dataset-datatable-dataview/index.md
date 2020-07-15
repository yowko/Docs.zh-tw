---
title: DataSet、DataTable 和 DataView
description: 瞭解使用 ADO.NET 資料集的數種方式，此為記憶體常駐的資料表示，可提供一致的關聯式程式設計模型。
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 53e12f701b9be1938d62f46bbeb6e63d95c03386
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374503"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="d16e1-103">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="d16e1-103">DataSets, DataTables, and DataViews</span></span>

<span data-ttu-id="d16e1-104">ADO.NET <xref:System.Data.DataSet> 是以常駐記憶體表示的資料，不論內含資料來源為何，都可提供一致的關聯式程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="d16e1-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="d16e1-105"><xref:System.Data.DataSet> 表示一組完整的資料，包括內含、排序和約束資料的資料表，以及資料表間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="d16e1-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
<span data-ttu-id="d16e1-106"><xref:System.Data.DataSet> 的使用方式有幾種，可以獨立或組合套用。</span><span class="sxs-lookup"><span data-stu-id="d16e1-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="d16e1-107">您可以：</span><span class="sxs-lookup"><span data-stu-id="d16e1-107">You can:</span></span>  
  
- <span data-ttu-id="d16e1-108">以程式設計方式在 <xref:System.Data.DataTable> 內建立 <xref:System.Data.DataRelation>、<xref:System.Data.Constraint> 和 <xref:System.Data.DataSet>，並填入資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="d16e1-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="d16e1-109">使用 <xref:System.Data.DataSet>，將來自現有關聯式資料來源之資料的資料表填入 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="d16e1-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="d16e1-110">使用 XML 載入並保存 <xref:System.Data.DataSet> 內容。</span><span class="sxs-lookup"><span data-stu-id="d16e1-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="d16e1-111">如需詳細資訊，請參閱[在 DataSet 中使用 XML](using-xml-in-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="d16e1-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
<span data-ttu-id="d16e1-112">也可以使用 XML Web Service 傳輸強型別的 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="d16e1-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="d16e1-113"><xref:System.Data.DataSet> 的設計非常適合使用 XML Web Service 來傳輸資料。</span><span class="sxs-lookup"><span data-stu-id="d16e1-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="d16e1-114">如需 XML Web Service 的概觀，請參閱 [XML Web Service 概觀](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d16e1-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="d16e1-115">如需使用來自 XML Web Service 之 <xref:System.Data.DataSet> 的範例，請參閱[從 XML Web Service 使用 DataSet](consuming-a-dataset-from-an-xml-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="d16e1-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d16e1-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="d16e1-116">In this section</span></span>

 [<span data-ttu-id="d16e1-117">安全性指導</span><span class="sxs-lookup"><span data-stu-id="d16e1-117">Security guidance</span></span>](security-guidance.md)  
 <span data-ttu-id="d16e1-118">提供和的安全性 <xref:System.Data.DataSet> 指引 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="d16e1-118">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="d16e1-119">建立資料集</span><span class="sxs-lookup"><span data-stu-id="d16e1-119">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="d16e1-120">說明建立 <xref:System.Data.DataSet> 執行個體的語法。</span><span class="sxs-lookup"><span data-stu-id="d16e1-120">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="d16e1-121">將 DataTable 加入至資料集</span><span class="sxs-lookup"><span data-stu-id="d16e1-121">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="d16e1-122">說明如何建立資料表和資料行，並將它們加入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="d16e1-122">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="d16e1-123">加入 DataRelation</span><span class="sxs-lookup"><span data-stu-id="d16e1-123">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="d16e1-124">說明如何在 <xref:System.Data.DataSet> 的資料表之間建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="d16e1-124">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="d16e1-125">導覽 DataRelation</span><span class="sxs-lookup"><span data-stu-id="d16e1-125">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="d16e1-126">說明如何使用 <xref:System.Data.DataSet> 之資料表間的關聯性，傳回父子關係的子資料列或父資料列。</span><span class="sxs-lookup"><span data-stu-id="d16e1-126">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="d16e1-127">合併 DataSet 內容</span><span class="sxs-lookup"><span data-stu-id="d16e1-127">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="d16e1-128">說明如何將一個 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 陣列的內容合併到另一個 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="d16e1-128">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="d16e1-129">複製資料集內容</span><span class="sxs-lookup"><span data-stu-id="d16e1-129">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="d16e1-130">說明如何建立 <xref:System.Data.DataSet> 的複本，而此複本包含結構描述和指定的資料。</span><span class="sxs-lookup"><span data-stu-id="d16e1-130">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="d16e1-131">處理 DataSet 的事件</span><span class="sxs-lookup"><span data-stu-id="d16e1-131">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="d16e1-132">說明 <xref:System.Data.DataSet> 的事件和使用方式。</span><span class="sxs-lookup"><span data-stu-id="d16e1-132">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="d16e1-133">具類型資料集</span><span class="sxs-lookup"><span data-stu-id="d16e1-133">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="d16e1-134">說明何謂具型別的 <xref:System.Data.DataSet> 以及它們的建立和使用方式。</span><span class="sxs-lookup"><span data-stu-id="d16e1-134">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="d16e1-135">DataTable</span><span class="sxs-lookup"><span data-stu-id="d16e1-135">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="d16e1-136">說明如何建立 <xref:System.Data.DataTable>、定義結構描述，以及管理資料。</span><span class="sxs-lookup"><span data-stu-id="d16e1-136">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="d16e1-137">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="d16e1-137">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="d16e1-138">說明如何建立及使用 <xref:System.Data.DataTableReader>。</span><span class="sxs-lookup"><span data-stu-id="d16e1-138">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="d16e1-139">DataView</span><span class="sxs-lookup"><span data-stu-id="d16e1-139">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="d16e1-140">說明如何建立並使用 `DataViews`，以及使用 <xref:System.Data.DataView> 事件。</span><span class="sxs-lookup"><span data-stu-id="d16e1-140">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="d16e1-141">在資料集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="d16e1-141">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="d16e1-142">說明 <xref:System.Data.DataSet> 如何將 XML 當成資料來源進行互動，包括將 <xref:System.Data.DataSet> 的內容載入和保存為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="d16e1-142">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="d16e1-143">從 XML Web Service 使用資料集</span><span class="sxs-lookup"><span data-stu-id="d16e1-143">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="d16e1-144">說明如何建立可透過 <xref:System.Data.DataSet> 傳輸資料的 XML Web Service。</span><span class="sxs-lookup"><span data-stu-id="d16e1-144">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d16e1-145">相關章節</span><span class="sxs-lookup"><span data-stu-id="d16e1-145">Related sections</span></span>

 [<span data-ttu-id="d16e1-146">ADO.NET 的新功能</span><span class="sxs-lookup"><span data-stu-id="d16e1-146">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="d16e1-147">簡介 ADO.NET 的新功能。</span><span class="sxs-lookup"><span data-stu-id="d16e1-147">Introduces features that are new in ADO.NET.</span></span>  
  
 <span data-ttu-id="d16e1-148">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="d16e1-148">[ADO.NET Overview](../ado-net-overview.md)</span></span>  
 <span data-ttu-id="d16e1-149">提供 ADO.NET 的設計和元件的簡介。</span><span class="sxs-lookup"><span data-stu-id="d16e1-149">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="d16e1-150">從 DataAdapter 填入資料集</span><span class="sxs-lookup"><span data-stu-id="d16e1-150">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="d16e1-151">描述如何自資料來源載入具有資料的 **DataSet**。</span><span class="sxs-lookup"><span data-stu-id="d16e1-151">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="d16e1-152">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="d16e1-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="d16e1-153">描述如何將 **DataSet** 中的資料變更解析回資料來源。</span><span class="sxs-lookup"><span data-stu-id="d16e1-153">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="d16e1-154">將現有條件約束加入至資料集</span><span class="sxs-lookup"><span data-stu-id="d16e1-154">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="d16e1-155">描述如何將來自資料來源的主索引鍵資訊填入 **DataSet**。</span><span class="sxs-lookup"><span data-stu-id="d16e1-155">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d16e1-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d16e1-156">See also</span></span>

- [<span data-ttu-id="d16e1-157">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d16e1-157">ADO.NET</span></span>](../index.md)
- <span data-ttu-id="d16e1-158">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="d16e1-158">[ADO.NET Overview](../ado-net-overview.md)</span></span>
