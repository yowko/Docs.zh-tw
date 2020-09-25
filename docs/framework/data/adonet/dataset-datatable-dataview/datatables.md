---
title: DataTables
description: 深入瞭解 ADO.NET DataTable （代表記憶體中關聯式資料的一個資料表）。以 .NET 為基礎的應用程式。
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: d501096b4abe94653acdc5249c120abff94534d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202301"
---
# <a name="datatables"></a><span data-ttu-id="d3329-103">DataTables</span><span class="sxs-lookup"><span data-stu-id="d3329-103">DataTables</span></span>

<span data-ttu-id="d3329-104"><xref:System.Data.DataSet> 是由資料表集合、關係和條件約束所組成。</span><span class="sxs-lookup"><span data-stu-id="d3329-104">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="d3329-105">在 ADO.NET 中， <xref:System.Data.DataTable> 物件是用來代表 **資料集中**的資料表。</span><span class="sxs-lookup"><span data-stu-id="d3329-105">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="d3329-106">**DataTable**代表記憶體中關聯式資料的一個資料表;資料是的本機資料。以 .NET 為基礎的應用程式，但可以從資料來源（例如 Microsoft SQL Server 使用**DataAdapter**來填入）取得詳細資訊，請參閱[從 Dataadapter 填入資料集](../populating-a-dataset-from-a-dataadapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d3329-106">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="d3329-107">**DataTable**類別是 .NET Framework 類別庫內的**system.object**命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="d3329-107">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="d3329-108">您可以單獨建立和使用 **DataTable** ，或是當做 **資料集**的成員，而且 **datatable** 物件也可以與其他 .NET Framework 物件搭配使用，包括 <xref:System.Data.DataView> 。</span><span class="sxs-lookup"><span data-stu-id="d3329-108">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="d3329-109">您可以透過**dataset**物件的**Tables**屬性存取**dataset**中的資料表集合。</span><span class="sxs-lookup"><span data-stu-id="d3329-109">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="d3329-110">資料表的結構描述 (或稱為結構) 是由資料行或條件約束來表示。</span><span class="sxs-lookup"><span data-stu-id="d3329-110">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="d3329-111">您可以使用物件以及**DataTable** <xref:System.Data.DataColumn> <xref:System.Data.ForeignKeyConstraint> 和物件來定義 DataTable 的架構 <xref:System.Data.UniqueConstraint> 。</span><span class="sxs-lookup"><span data-stu-id="d3329-111">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="d3329-112">資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="d3329-112">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="d3329-113">除了架構以外， **DataTable** 也必須擁有資料列來包含和排序資料。</span><span class="sxs-lookup"><span data-stu-id="d3329-113">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="d3329-114"><xref:System.Data.DataRow> 類別 (Class) 代表資料表所包含的實際資料。</span><span class="sxs-lookup"><span data-stu-id="d3329-114">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="d3329-115">您可以使用 **DataRow** 及其屬性和方法，來取出、評估和運算元據表中的資料。</span><span class="sxs-lookup"><span data-stu-id="d3329-115">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="d3329-116">當您存取和變更資料列內的資料時， **DataRow** 物件會維持其目前和原始狀態。</span><span class="sxs-lookup"><span data-stu-id="d3329-116">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="d3329-117">您可以使用一或多個資料表中的相關資料行，在資料表之間建立父子關係 (Parent-Child Relationship)。</span><span class="sxs-lookup"><span data-stu-id="d3329-117">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="d3329-118">您可以使用建立 **DataTable** 物件之間的關聯性 <xref:System.Data.DataRelation> 。</span><span class="sxs-lookup"><span data-stu-id="d3329-118">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="d3329-119">然後可以使用**DataRelation**物件來傳回特定資料列的相關子資料列或父資料列。</span><span class="sxs-lookup"><span data-stu-id="d3329-119">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="d3329-120">如需詳細資訊，請參閱 [新增 datarelation](adding-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="d3329-120">For more information, see [Adding DataRelations](adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3329-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="d3329-121">In This Section</span></span>  

 [<span data-ttu-id="d3329-122">建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="d3329-122">Creating a DataTable</span></span>](creating-a-datatable.md)  
 <span data-ttu-id="d3329-123">說明如何建立 **DataTable** 並將它加入至 **資料集**。</span><span class="sxs-lookup"><span data-stu-id="d3329-123">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d3329-124">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="d3329-124">DataTable Schema Definition</span></span>](datatable-schema-definition.md)  
 <span data-ttu-id="d3329-125">提供有關建立及使用 **DataColumn** 物件和條件約束的資訊。</span><span class="sxs-lookup"><span data-stu-id="d3329-125">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="d3329-126">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="d3329-126">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="d3329-127">說明如何加入、修改和刪除資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="d3329-127">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="d3329-128">說明如何使用 **DataTable** 事件來檢查資料表中資料的變更。</span><span class="sxs-lookup"><span data-stu-id="d3329-128">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="d3329-129">處理 DataTable 的事件</span><span class="sxs-lookup"><span data-stu-id="d3329-129">Handling DataTable Events</span></span>](handling-datatable-events.md)  
 <span data-ttu-id="d3329-130">提供可與 **DataTable**搭配使用之事件的相關資訊，包括修改資料行值和加入或刪除資料列時的事件。</span><span class="sxs-lookup"><span data-stu-id="d3329-130">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d3329-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="d3329-131">Related Sections</span></span>  

 [<span data-ttu-id="d3329-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d3329-132">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="d3329-133">描述 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="d3329-133">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="d3329-134">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="d3329-134">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="d3329-135">提供 ADO.NET **資料集** 的相關資訊，包括如何建立資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="d3329-135">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="d3329-136">提供有關 **條件約束** 物件的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="d3329-136">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="d3329-137">提供 **DataColumn** 物件的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="d3329-137">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="d3329-138">提供有關 **DataSet** 物件的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="d3329-138">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="d3329-139">提供 **DataTable** 物件的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="d3329-139">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="d3329-140">類別庫總覽</span><span class="sxs-lookup"><span data-stu-id="d3329-140">Class Library Overview</span></span>](../../../../standard/class-library-overview.md)  
 <span data-ttu-id="d3329-141">提供 .NET Framework 類別庫的總覽，包括 **system** 命名空間以及其第二層命名空間、 **system.object**。</span><span class="sxs-lookup"><span data-stu-id="d3329-141">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3329-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3329-142">See also</span></span>

- <span data-ttu-id="d3329-143">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="d3329-143">[ADO.NET Overview](../ado-net-overview.md)</span></span>
