---
title: DataSets
description: 瞭解資料集，這是記憶體常駐資料的標記法，可提供一致的關聯式程式設計模型，而不論 ADO.NET 中的資料來源為何。
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: d78918773c3cc88d8a925788d81cdafdc0a2db27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153582"
---
# <a name="adonet-datasets"></a>ADO.NET 資料集

<xref:System.Data.DataSet>物件是使用 ADO.NET 支援中斷連線的分散式資料案例的核心。 資料 **集** 是記憶體常駐的資料表示，可提供一致的關聯式程式設計模型，而不論資料來源為何。 它可與多個不同的資料來源一起使用、與 XML 資料一起使用，或管理應用程式的本機資料。 **資料集**代表一組完整的資料，包括相關資料表、條件約束和資料表之間的關聯性。 下圖顯示 **資料集** 物件模型。  
  
 ![ADO.Net 圖形](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
DataSet 物件模型  
  
 **資料集中**的方法和物件與關係資料庫模型中的方法和物件一致。  
  
 **DataSet**也可以將其內容保存及重載為 xml，並將其架構做為 xml 架構定義語言， (XSD) 架構。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](./dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="the-datatablecollection"></a>DataTableCollection  

 ADO.NET **資料集** 包含由物件所表示的零或多個資料表的集合 <xref:System.Data.DataTable> 。 <xref:System.Data.DataTableCollection>包含**資料集中**的所有**DataTable**物件。  
  
 **DataTable**是在 <xref:System.Data> 命名空間中定義，代表記憶體常駐資料的單一資料表。 它包含由 <xref:System.Data.DataColumnCollection> 所表示的資料行集合，以及由 <xref:System.Data.ConstraintCollection> 所表示的條件約束，它們共同定義資料表的結構描述。 **DataTable**還包含由所表示的資料列集合 <xref:System.Data.DataRowCollection> ，其中包含資料表中的資料。 連同其目前狀態一起，<xref:System.Data.DataRow> 還保留其目前及原始版本，以識別儲存在資料列中之值的變更。  
  
## <a name="the-dataview-class"></a>DataView 類別  

 <xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。 您可以使用 <xref:System.Data.DataView>，以不同排序次序公開 (Expose) 資料表中的資料，而且可以按照資料列狀態或根據篩選條件運算式來篩選資料。 如需詳細資訊，請參閱 [dataview](./dataset-datatable-dataview/dataviews.md)。  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  

 **資料集**包含其物件中的關聯性 <xref:System.Data.DataRelationCollection> 。 關聯性（由物件所代表）會將 <xref:System.Data.DataRelation> 一個 **datatable** 中的資料列與另一個 **datatable**中的資料列產生關聯。 關聯性類似於在關聯式資料庫中，主索引鍵資料行與外部索引鍵資料行之間存在的聯結路徑。 **DataRelation**會識別**資料集**的兩個數據表中相符的資料行。  
  
 關聯性可讓您在 **資料集中**從一個資料表導覽至另一個資料表。 **DataRelation**的基本專案是關聯性的名稱、相關資料表的名稱，以及每個資料表中的相關資料行。 藉由將 <xref:System.Data.DataColumn> 物件的陣列指定為索引鍵資料行，可在每個資料表中建立多個資料行的關聯性。 當您加入的關聯性時 <xref:System.Data.DataRelationCollection> ，您可以選擇性地加入 **UniqueKeyConstraint** 和 **ForeignKeyConstraint** ，以在變更相關資料行值時強制執行完整性條件約束。  
  
 如需詳細資訊，請參閱 [新增 datarelation](./dataset-datatable-dataview/adding-datarelations.md)。  
  
## <a name="xml"></a>XML  

 您可以從 XML 資料流程或檔填滿 **資料集** 。 您可以使用 XML 資料流程或檔，為數據 **集** 提供資料、架構資訊或兩者。 從 XML 資料流程或檔提供的資訊，可以與現有的資料或 **資料集**內已存在的架構資訊結合。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](./dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="extendedproperties"></a>ExtendedProperties  

 **DataSet**、 **DataTable**和**DataColumn**都具有**ExtendedProperties**屬性。 **ExtendedProperties** 是 **PropertyCollection** ，您可以在其中放置自訂資訊，例如用來產生結果集的 SELECT 語句，或是產生資料的時間。 **ExtendedProperties**集合會與**資料集**的架構資訊一起保存。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  

 LINQ to DataSet 針對儲存在資料集中的已中斷連線資料，提供與語言整合的查詢功能。 LINQ to DataSet 使用標準 LINQ 語法，並在使用 Visual Studio IDE 時提供編譯時期語法檢查、靜態類型和 IntelliSense 支援。  
  
 如需詳細資訊，請參閱 [LINQ to DataSet](linq-to-dataset.md)。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
- [DataSet、DataTable 和 DataView](./dataset-datatable-dataview/index.md)
- [在 ADO.NET 中傳送和修改資料](retrieving-and-modifying-data.md)
