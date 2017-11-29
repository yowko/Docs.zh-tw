---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d1222d3df30bf2b3de1761b8fa5c702dc687d0a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="datatables"></a><span data-ttu-id="3824a-102">DataTables</span><span class="sxs-lookup"><span data-stu-id="3824a-102">DataTables</span></span>
<span data-ttu-id="3824a-103"><xref:System.Data.DataSet> 是由資料表集合、關係和條件約束所組成。</span><span class="sxs-lookup"><span data-stu-id="3824a-103">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="3824a-104">在 ADO.NET 中，<xref:System.Data.DataTable>物件用來代表中的資料表**資料集**。</span><span class="sxs-lookup"><span data-stu-id="3824a-104">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="3824a-105">A **DataTable**表示一個資料表的記憶體中關聯式資料; 資料位於本機。網路架構應用程式它所在的但可以填入來自資料來源，例如 Microsoft SQL Server 使用**DataAdapter**如需詳細資訊，請參閱[填入資料集從 DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).</span><span class="sxs-lookup"><span data-stu-id="3824a-105">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="3824a-106">**DataTable**類別所屬的**System.Data** .NET Framework 類別庫中的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3824a-106">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="3824a-107">您可以建立並使用**DataTable**獨立或成員的身分**資料集**，和**DataTable**物件也可以用於搭配其他.NET Framework 物件包括<xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="3824a-107">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="3824a-108">存取集合中的資料表**資料集**透過**資料表**屬性**資料集**物件。</span><span class="sxs-lookup"><span data-stu-id="3824a-108">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="3824a-109">資料表的結構描述 (或稱為結構) 是由資料行或條件約束來表示。</span><span class="sxs-lookup"><span data-stu-id="3824a-109">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="3824a-110">您定義的結構描述**DataTable**使用<xref:System.Data.DataColumn>物件以及<xref:System.Data.ForeignKeyConstraint>和<xref:System.Data.UniqueConstraint>物件。</span><span class="sxs-lookup"><span data-stu-id="3824a-110">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="3824a-111">資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="3824a-111">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="3824a-112">結構描述時，除了**DataTable**也必須擁有包含和排列資料的資料列。</span><span class="sxs-lookup"><span data-stu-id="3824a-112">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="3824a-113"><xref:System.Data.DataRow> 類別 (Class) 代表資料表所包含的實際資料。</span><span class="sxs-lookup"><span data-stu-id="3824a-113">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="3824a-114">您使用**DataRow**和其屬性和方法以擷取、 評估及管理資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="3824a-114">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="3824a-115">當您存取和變更資料列中的資料**DataRow**物件會維護其目前和原始的狀態。</span><span class="sxs-lookup"><span data-stu-id="3824a-115">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="3824a-116">您可以使用一或多個資料表中的相關資料行，在資料表之間建立父子關係 (Parent-Child Relationship)。</span><span class="sxs-lookup"><span data-stu-id="3824a-116">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="3824a-117">您建立的關聯性**DataTable**物件，使用<xref:System.Data.DataRelation>。</span><span class="sxs-lookup"><span data-stu-id="3824a-117">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="3824a-118">**DataRelation**物件可以再用來傳回特定資料列相關的子系或父資料列。</span><span class="sxs-lookup"><span data-stu-id="3824a-118">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="3824a-119">如需詳細資訊，請參閱[加入 Datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="3824a-119">For more information, see [Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3824a-120">本章節內容</span><span class="sxs-lookup"><span data-stu-id="3824a-120">In This Section</span></span>  
 [<span data-ttu-id="3824a-121">建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="3824a-121">Creating a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 <span data-ttu-id="3824a-122">說明如何建立**DataTable**並將它加入**資料集**。</span><span class="sxs-lookup"><span data-stu-id="3824a-122">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="3824a-123">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="3824a-123">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 <span data-ttu-id="3824a-124">提供有關建立及使用資訊**DataColumn**物件和條件約束。</span><span class="sxs-lookup"><span data-stu-id="3824a-124">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="3824a-125">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="3824a-125">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="3824a-126">說明如何加入、修改和刪除資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="3824a-126">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="3824a-127">說明如何使用**DataTable**事件，以檢視資料表中資料的變更。</span><span class="sxs-lookup"><span data-stu-id="3824a-127">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="3824a-128">處理 DataTable 的事件</span><span class="sxs-lookup"><span data-stu-id="3824a-128">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 <span data-ttu-id="3824a-129">提供可用的事件資訊搭配**DataTable**，包括已修改資料行值，並加入或刪除資料列時的事件。</span><span class="sxs-lookup"><span data-stu-id="3824a-129">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3824a-130">相關章節</span><span class="sxs-lookup"><span data-stu-id="3824a-130">Related Sections</span></span>  
 [<span data-ttu-id="3824a-131">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3824a-131">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="3824a-132">描述 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="3824a-132">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="3824a-133">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="3824a-133">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="3824a-134">提供 ADO.NET 的相關資訊**資料集**包括如何建立資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="3824a-134">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="3824a-135">相關參考資訊提供**條件約束**物件。</span><span class="sxs-lookup"><span data-stu-id="3824a-135">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="3824a-136">相關參考資訊提供**DataColumn**物件。</span><span class="sxs-lookup"><span data-stu-id="3824a-136">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="3824a-137">相關參考資訊提供**資料集**物件。</span><span class="sxs-lookup"><span data-stu-id="3824a-137">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="3824a-138">相關參考資訊提供**DataTable**物件。</span><span class="sxs-lookup"><span data-stu-id="3824a-138">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="3824a-139">類別庫概觀</span><span class="sxs-lookup"><span data-stu-id="3824a-139">Class Library Overview</span></span>](../../../../../docs/standard/class-library-overview.md)  
 <span data-ttu-id="3824a-140">提供的.NET Framework 類別庫概觀包括**系統**命名空間以及它的第二層命名空間， **System.Data**。</span><span class="sxs-lookup"><span data-stu-id="3824a-140">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3824a-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3824a-141">See Also</span></span>  
 [<span data-ttu-id="3824a-142">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="3824a-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
