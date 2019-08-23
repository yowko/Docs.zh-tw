---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 369855d1aff854b60c251010ec42557b70c093c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952656"
---
# <a name="datatables"></a>DataTables
<xref:System.Data.DataSet> 是由資料表集合、關係和條件約束所組成。 在 ADO.NET 中<xref:System.Data.DataTable> , 物件是用來表示**資料集中**的資料表。 **DataTable**代表記憶體中關聯式資料的其中一個資料表;資料位於的本機。其所在的網路應用程式, 但可以使用**dataadapter**從資料來源 (例如 Microsoft SQL Server) 填入, 如需詳細資訊, 請參閱[從 Dataadapter 填入資料集](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)。  
  
 **DataTable**類別是 .NET Framework Class Library 內的**system.web**命名空間成員。 您可以單獨建立和使用**datatable** , 或做為**資料集**的成員, 而**datatable**物件也可以與其他<xref:System.Data.DataView>.NET Framework 物件搭配使用, 包括。 您可以透過**dataset**物件的**tables**屬性來存取**資料集中**的資料表集合。  
  
 資料表的結構描述 (或稱為結構) 是由資料行或條件約束來表示。 您可以使用<xref:System.Data.DataColumn> <xref:System.Data.UniqueConstraint>物件以及和物件來定義 DataTable 的架構。 <xref:System.Data.ForeignKeyConstraint> 資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。  
  
 除了架構之外, **DataTable**也必須有資料列來包含和排序資料。 <xref:System.Data.DataRow> 類別 (Class) 代表資料表所包含的實際資料。 您可以使用**DataRow**及其屬性和方法來取出、評估和運算元據表中的資料。 當您存取和變更資料列內的資料時, **DataRow**物件會同時維護其目前和原始狀態。  
  
 您可以使用一或多個資料表中的相關資料行，在資料表之間建立父子關係 (Parent-Child Relationship)。 您可以使用<xref:System.Data.DataRelation>, 在**DataTable**物件之間建立關聯性。 然後可以使用**DataRelation**物件傳回特定資料列的相關子系或父資料列。 如需詳細資訊, 請參閱[新增 datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [建立 DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 說明如何建立**DataTable**並將它加入至**資料集**。  
  
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 提供建立和使用**DataColumn**物件和條件約束的相關資訊。  
  
 [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 說明如何加入、修改和刪除資料表中的資料。 說明如何使用**DataTable**事件來檢查資料表中資料的變更。  
  
 [處理 DataTable 事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 提供可搭配**DataTable**使用之事件的相關資訊, 包括當資料行值已修改且資料列已加入或刪除時的事件。  
  
## <a name="related-sections"></a>相關章節  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 描述 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。  
  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 提供 ADO.NET**資料集**的相關資訊, 包括如何建立資料表之間的關聯性。  
  
 <xref:System.Data.Constraint>  
 提供有關**條件約束**物件的參考資訊。  
  
 <xref:System.Data.DataColumn>  
 提供**DataColumn**物件的相關參考資訊。  
  
 <xref:System.Data.DataSet>  
 提供有關**DataSet**物件的參考資訊。  
  
 <xref:System.Data.DataTable>  
 提供有關**DataTable**物件的參考資訊。  
  
 [類別庫概觀](../../../../standard/class-library-overview.md)  
 提供 .NET Framework Class Library 的總覽, 包括**系統**命名空間以及其第二層命名空間、 **system.web**。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
