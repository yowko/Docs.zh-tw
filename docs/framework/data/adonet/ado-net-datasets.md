---
title: ADO.NET 資料集
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: acbe5a549539a77d63332687486cbe8744592f8b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786983"
---
# <a name="adonet-datasets"></a>ADO.NET 資料集
物件<xref:System.Data.DataSet>是支援已中斷連線之分散式資料案例與 ADO.NET 的核心。 **DataSet**是記憶體常駐的資料表示，可提供一致的關聯式程式設計模型，不論資料來源為何。 它可與多個不同的資料來源一起使用、與 XML 資料一起使用，或管理應用程式的本機資料。 資料**集**代表一組完整的資料，包括相關資料表、條件約束和資料表之間的關聯性。 下圖顯示**資料集**物件模型。  
  
 ![ADO.Net 圖形](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
DataSet 物件模型  
  
 **資料集中**的方法和物件與關係資料庫模型中的相同。  
  
 **DataSet**也可以將其內容保存並重載為 xml，並將其架構當做 xml 架構定義語言（XSD）架構。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](./dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 ADO.NET**資料集**包含由<xref:System.Data.DataTable>物件所表示之零或多個資料表的集合。 包含 DataSet 中的所有**DataTable**物件。 <xref:System.Data.DataTableCollection>  
  
 **DataTable**定義于<xref:System.Data>命名空間中，並代表記憶體常駐資料的單一資料表。 它包含由 <xref:System.Data.DataColumnCollection> 所表示的資料行集合，以及由 <xref:System.Data.ConstraintCollection> 所表示的條件約束，它們共同定義資料表的結構描述。 **DataTable**也包含由表示<xref:System.Data.DataRowCollection>的資料列集合，其中包含資料表中的資料。 連同其目前狀態一起，<xref:System.Data.DataRow> 還保留其目前及原始版本，以識別儲存在資料列中之值的變更。  
  
## <a name="the-dataview-class"></a>DataView 類別  
 <xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。 您可以使用 <xref:System.Data.DataView>，以不同排序次序公開 (Expose) 資料表中的資料，而且可以按照資料列狀態或根據篩選條件運算式來篩選資料。 如需詳細資訊，請參閱[dataview](./dataset-datatable-dataview/dataviews.md)。  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 **資料集**包含其<xref:System.Data.DataRelationCollection>物件中的關聯性。 關聯性（由<xref:System.Data.DataRelation>物件表示）會將一個**datatable**中的資料列與另一個**datatable**中的資料列產生關聯。 關聯性類似於在關聯式資料庫中，主索引鍵資料行與外部索引鍵資料行之間存在的聯結路徑。 **DataRelation**會識別**資料集**的兩個數據表中相符的資料行。  
  
 關聯性可讓您在**資料集中**從一個資料表流覽至另一個。 **DataRelation**的基本要素是關聯性的名稱、相關資料表的名稱，以及每個資料表中的相關資料行。 藉由將 <xref:System.Data.DataColumn> 物件的陣列指定為索引鍵資料行，可在每個資料表中建立多個資料行的關聯性。 當您將關聯性加入至<xref:System.Data.DataRelationCollection>時，您可以選擇性地加入**UniqueKeyConstraint**和**ForeignKeyConstraint** ，以在對相關資料行值進行變更時，強制執行完整性條件約束。  
  
 如需詳細資訊，請參閱[新增 datarelation](./dataset-datatable-dataview/adding-datarelations.md)。  
  
## <a name="xml"></a>XML  
 您可以從 XML 資料流程或檔填滿**資料集**。 您可以使用 XML 資料流程或檔，將資料、架構資訊或兩者提供給資料**集**。 從 XML 資料流程或檔提供的資訊，可以與**資料集**內已經存在的現有資料或架構資訊結合。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](./dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **DataSet**、 **DataTable**和**DataColumn**全都具有**ExtendedProperties**屬性。 **ExtendedProperties**是一個**PropertyCollection** ，您可以在其中放置自訂資訊，例如用來產生結果集的 SELECT 語句，或產生資料的時間。 **ExtendedProperties**集合會與**資料集**的架構資訊保存在一起。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 LINQ to DataSet 為儲存在資料集中的已中斷連接資料提供語言整合式查詢功能。 LINQ to DataSet 使用標準[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]語法，並在使用 Visual Studio IDE 時提供編譯時期語法檢查、靜態型別和 IntelliSense 支援。  
  
 如需詳細資訊，請參閱 [LINQ to DataSet](linq-to-dataset.md)。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](ado-net-overview.md)
- [DataSet、DataTable 和 DataView](./dataset-datatable-dataview/index.md)
- [在 ADO.NET 中擷取和修改資料](retrieving-and-modifying-data.md)
