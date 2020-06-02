---
title: DataTables
description: 深入瞭解 ADO.NET DataTable，其代表記憶體中關聯式資料的一個資料表（本機）。其所在的網路應用程式。
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: da6c9201951a6c7916067011c0a4f01ef9fdeffd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286904"
---
# <a name="datatables"></a><span data-ttu-id="5dc7b-103">DataTables</span><span class="sxs-lookup"><span data-stu-id="5dc7b-103">DataTables</span></span>
<span data-ttu-id="5dc7b-104"><xref:System.Data.DataSet> 是由資料表集合、關係和條件約束所組成。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-104">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="5dc7b-105">在 ADO.NET 中， <xref:System.Data.DataTable> 物件是用來表示**資料集中**的資料表。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-105">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="5dc7b-106">**DataTable**代表記憶體中關聯式資料的其中一個資料表;資料位於的本機。其所在的網路應用程式，但可以使用**dataadapter**從資料來源（例如 Microsoft SQL Server）填入，如需詳細資訊，請參閱[從 Dataadapter 填入資料集](../populating-a-dataset-from-a-dataadapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-106">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="5dc7b-107">**DataTable**類別是 .NET Framework Class Library 內的**system.web**命名空間成員。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-107">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="5dc7b-108">您可以單獨建立和使用**datatable** ，或做為**資料集**的成員，而**datatable**物件也可以與其他 .NET Framework 物件搭配使用，包括 <xref:System.Data.DataView> 。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-108">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="5dc7b-109">您可以透過**dataset**物件的**tables**屬性來存取**資料集中**的資料表集合。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-109">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="5dc7b-110">資料表的結構描述 (或稱為結構) 是由資料行或條件約束來表示。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-110">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="5dc7b-111">您可以使用物件以及**DataTable** <xref:System.Data.DataColumn> <xref:System.Data.ForeignKeyConstraint> 和物件來定義 DataTable 的架構 <xref:System.Data.UniqueConstraint> 。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-111">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="5dc7b-112">資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-112">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="5dc7b-113">除了架構之外， **DataTable**也必須有資料列來包含和排序資料。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-113">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="5dc7b-114"><xref:System.Data.DataRow> 類別 (Class) 代表資料表所包含的實際資料。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-114">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="5dc7b-115">您可以使用**DataRow**及其屬性和方法來取出、評估和運算元據表中的資料。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-115">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="5dc7b-116">當您存取和變更資料列內的資料時， **DataRow**物件會同時維護其目前和原始狀態。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-116">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="5dc7b-117">您可以使用一或多個資料表中的相關資料行，在資料表之間建立父子關係 (Parent-Child Relationship)。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-117">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="5dc7b-118">您可以使用，在**DataTable**物件之間建立關聯性 <xref:System.Data.DataRelation> 。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-118">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="5dc7b-119">然後可以使用**DataRelation**物件傳回特定資料列的相關子系或父資料列。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-119">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="5dc7b-120">如需詳細資訊，請參閱[新增 datarelation](adding-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-120">For more information, see [Adding DataRelations](adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5dc7b-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="5dc7b-121">In This Section</span></span>  
 [<span data-ttu-id="5dc7b-122">建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="5dc7b-122">Creating a DataTable</span></span>](creating-a-datatable.md)  
 <span data-ttu-id="5dc7b-123">說明如何建立**DataTable**並將它加入至**資料集**。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-123">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="5dc7b-124">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="5dc7b-124">DataTable Schema Definition</span></span>](datatable-schema-definition.md)  
 <span data-ttu-id="5dc7b-125">提供建立和使用**DataColumn**物件和條件約束的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-125">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="5dc7b-126">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="5dc7b-126">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="5dc7b-127">說明如何加入、修改和刪除資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-127">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="5dc7b-128">說明如何使用**DataTable**事件來檢查資料表中資料的變更。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-128">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="5dc7b-129">處理 DataTable 事件</span><span class="sxs-lookup"><span data-stu-id="5dc7b-129">Handling DataTable Events</span></span>](handling-datatable-events.md)  
 <span data-ttu-id="5dc7b-130">提供可搭配**DataTable**使用之事件的相關資訊，包括當資料行值已修改且資料列已加入或刪除時的事件。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-130">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5dc7b-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="5dc7b-131">Related Sections</span></span>  
 [<span data-ttu-id="5dc7b-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5dc7b-132">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="5dc7b-133">描述 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-133">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="5dc7b-134">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="5dc7b-134">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="5dc7b-135">提供 ADO.NET**資料集**的相關資訊，包括如何建立資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-135">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="5dc7b-136">提供有關**條件約束**物件的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-136">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="5dc7b-137">提供**DataColumn**物件的相關參考資訊。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-137">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="5dc7b-138">提供有關**DataSet**物件的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-138">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="5dc7b-139">提供有關**DataTable**物件的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-139">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="5dc7b-140">類別庫總覽</span><span class="sxs-lookup"><span data-stu-id="5dc7b-140">Class Library Overview</span></span>](../../../../standard/class-library-overview.md)  
 <span data-ttu-id="5dc7b-141">提供 .NET Framework Class Library 的總覽，包括**系統**命名空間以及其第二層命名空間、 **system.web**。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-141">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc7b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dc7b-142">See also</span></span>

- <span data-ttu-id="5dc7b-143">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="5dc7b-143">[ADO.NET Overview](../ado-net-overview.md)</span></span>
