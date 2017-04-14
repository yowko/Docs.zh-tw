---
title: "DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable
<xref:System.Data.DataSet> 是由資料表集合、關係和條件約束所組成。  在 ADO.NET 中，<xref:System.Data.DataTable> 物件是用於表示 **DataSet** 中的資料表。  **DataTable** 代表一個記憶體中關聯式資料的資料表；這個資料為它所在的 .NET 應用程式的區域資料，但是您可以使用 **DataAdapter**，從 Microsoft SQL Server 之類的資料來源中填入資料。如需詳細資訊，請參閱[從 DataAdapter 填入資料集](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)。  
  
 **DataTable** 類別是 .NET Framework 類別庫 \(Class Library\) 中 **System.Data** 命名空間 \(Namespace\) 的成員。  您可以單獨建立和使用 **DataTable**，或是將它當做 **DataSet** 的成員，而 **DataTable** 物件也可以與其他 .NET Framework 物件一起使用，包括 <xref:System.Data.DataView>。  您可以透過 **DataSet** 物件的 **Tables** 屬性存取 **DataSet** 中的資料表集合。  
  
 資料表的結構描述 \(或稱為結構\) 是由資料行或條件約束來表示。  您可以使用 <xref:System.Data.DataColumn> 物件以及 <xref:System.Data.ForeignKeyConstraint> 和 <xref:System.Data.UniqueConstraint> 等物件來定義 **DataTable** 的結構描述。  資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。  
  
 除了結構描述，**DataTable** 也必須擁有資料列來包含和排列資料。  <xref:System.Data.DataRow> 類別 \(Class\) 代表資料表所包含的實際資料。  您可以使用 **DataRow** 及其屬性和方法以擷取、評估和管理資料表中的資料。  當您存取和變更資料列中的資料時，**DataRow** 物件會維護其目前和原始的狀態。  
  
 您可以使用一或多個資料表中的相關資料行，在資料表之間建立父子關係 \(Parent\-Child Relationship\)。  您可以使用 <xref:System.Data.DataRelation>，在 **DataTable** 物件之間建立關係。  然後您可以使用 **DataRelation** 物件傳回特定資料列的相關子資料列或父資料列。  如需詳細資訊，請參閱[加入 DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)。  
  
## 在本節中  
 [建立 DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 說明如何建立 **DataTable**，以及如何將它加入至 **DataSet**。  
  
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 提供建立和使用 **DataColumn** 物件和條件約束的相關資訊。  
  
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 說明如何加入、修改和刪除資料表中的資料。  說明如何使用 **DataTable** 事件，以檢視資料表中的資料變更。  
  
 [處理 DataTable 事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 提供 **DataTable** 可使用之事件的相關資訊，包括修改資料行之值以及加入或刪除資料列時的事件。  
  
## 相關章節  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 描述 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。  
  
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 提供 ADO.NET **DataSet** 的相關資訊，包括如何建立資料表之間的關係。  
  
 [Constraint 類別](frlrfSystemDataConstraintClassTopic)  
 提供 **Constraint** 物件的參考資訊。  
  
 [DataColumn 類別](frlrfSystemDataDataColumnClassTopic)  
 提供 **DataColumn** 物件的參考資訊。  
  
 [DataSet 類別](frlrfSystemDataDataSetClassTopic)  
 提供 **DataSet** 物件的參考資訊。  
  
 [DataTable 類別](frlrfSystemDataDataTableClassTopic)  
 提供 **DataTable** 物件的參考資訊。  
  
 [類別庫概觀](../../../../../docs/standard/class-library-overview.md)  
 提供 .NET Framework 類別庫的概觀，包括 **System** 命名空間以及它的第二層命名空間 **System.Data**。  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)