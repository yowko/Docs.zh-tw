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
# <a name="datatables"></a>DataTables

<xref:System.Data.DataSet> 是由資料表集合、關係和條件約束所組成。 在 ADO.NET 中， <xref:System.Data.DataTable> 物件是用來代表 **資料集中**的資料表。 **DataTable**代表記憶體中關聯式資料的一個資料表;資料是的本機資料。以 .NET 為基礎的應用程式，但可以從資料來源（例如 Microsoft SQL Server 使用**DataAdapter**來填入）取得詳細資訊，請參閱[從 Dataadapter 填入資料集](../populating-a-dataset-from-a-dataadapter.md)。  
  
 **DataTable**類別是 .NET Framework 類別庫內的**system.object**命名空間的成員。 您可以單獨建立和使用 **DataTable** ，或是當做 **資料集**的成員，而且 **datatable** 物件也可以與其他 .NET Framework 物件搭配使用，包括 <xref:System.Data.DataView> 。 您可以透過**dataset**物件的**Tables**屬性存取**dataset**中的資料表集合。  
  
 資料表的結構描述 (或稱為結構) 是由資料行或條件約束來表示。 您可以使用物件以及**DataTable** <xref:System.Data.DataColumn> <xref:System.Data.ForeignKeyConstraint> 和物件來定義 DataTable 的架構 <xref:System.Data.UniqueConstraint> 。 資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。  
  
 除了架構以外， **DataTable** 也必須擁有資料列來包含和排序資料。 <xref:System.Data.DataRow> 類別 (Class) 代表資料表所包含的實際資料。 您可以使用 **DataRow** 及其屬性和方法，來取出、評估和運算元據表中的資料。 當您存取和變更資料列內的資料時， **DataRow** 物件會維持其目前和原始狀態。  
  
 您可以使用一或多個資料表中的相關資料行，在資料表之間建立父子關係 (Parent-Child Relationship)。 您可以使用建立 **DataTable** 物件之間的關聯性 <xref:System.Data.DataRelation> 。 然後可以使用**DataRelation**物件來傳回特定資料列的相關子資料列或父資料列。 如需詳細資訊，請參閱 [新增 datarelation](adding-datarelations.md)。  
  
## <a name="in-this-section"></a>本節內容  

 [建立 DataTable](creating-a-datatable.md)  
 說明如何建立 **DataTable** 並將它加入至 **資料集**。  
  
 [DataTable 結構描述定義](datatable-schema-definition.md)  
 提供有關建立及使用 **DataColumn** 物件和條件約束的資訊。  
  
 [在 DataTable 中操作資料](manipulating-data-in-a-datatable.md)  
 說明如何加入、修改和刪除資料表中的資料。 說明如何使用 **DataTable** 事件來檢查資料表中資料的變更。  
  
 [處理 DataTable 的事件](handling-datatable-events.md)  
 提供可與 **DataTable**搭配使用之事件的相關資訊，包括修改資料行值和加入或刪除資料列時的事件。  
  
## <a name="related-sections"></a>相關章節  

 [ADO.NET](../index.md)  
 描述 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。  
  
 [DataSet、DataTable 和 DataView](index.md)  
 提供 ADO.NET **資料集** 的相關資訊，包括如何建立資料表之間的關聯性。  
  
 <xref:System.Data.Constraint>  
 提供有關 **條件約束** 物件的參考資訊。  
  
 <xref:System.Data.DataColumn>  
 提供 **DataColumn** 物件的參考資訊。  
  
 <xref:System.Data.DataSet>  
 提供有關 **DataSet** 物件的參考資訊。  
  
 <xref:System.Data.DataTable>  
 提供 **DataTable** 物件的參考資訊。  
  
 [類別庫總覽](../../../../standard/class-library-overview.md)  
 提供 .NET Framework 類別庫的總覽，包括 **system** 命名空間以及其第二層命名空間、 **system.object**。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
