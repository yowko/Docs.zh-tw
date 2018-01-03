---
title: "ADO.NET 資料集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b117b8b75cd4b90f3689fa535b0afbac0ca00fdc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="adonet-datasets"></a>ADO.NET 資料集
<xref:System.Data.DataSet> 物件對於支援 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 的中斷連接、分散式的資料案例非常重要。 **資料集**是常駐記憶體的表示法提供與資料來源無關的一致性關聯式程式設計模型的資料。 它可與多個不同的資料來源一起使用、與 XML 資料一起使用，或管理應用程式的本機資料。 **資料集**表示一組完整的資料，包括相關的資料表、 條件約束及資料表間的關聯性。 下圖顯示**資料集**物件模型。  
  
 ![ADO.Net 圖形](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
DataSet 物件模型  
  
 中的物件與方法**資料集**與關聯式資料庫模型中一致。  
  
 **資料集**也可以保存及重新載入其內容為 XML，以及其與 XML 結構描述定義語言 (XSD) 結構描述的結構描述。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **資料集**包含零個或多個資料表所表示的集合<xref:System.Data.DataTable>物件。 <xref:System.Data.DataTableCollection>包含所有**DataTable**中的物件**資料集**。  
  
 A **DataTable**中定義<xref:System.Data>命名空間和表示記憶體常駐資料的單一資料表。 它包含由 <xref:System.Data.DataColumnCollection> 所表示的資料行集合，以及由 <xref:System.Data.ConstraintCollection> 所表示的條件約束，它們共同定義資料表的結構描述。 A **DataTable**也包含由資料列集合<xref:System.Data.DataRowCollection>，其中包含資料表中的資料。 連同其目前狀態一起，<xref:System.Data.DataRow> 還保留其目前及原始版本，以識別儲存在資料列中之值的變更。  
  
## <a name="the-dataview-class"></a>DataView 類別  
 <xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。 您可以使用 <xref:System.Data.DataView>，以不同排序次序公開 (Expose) 資料表中的資料，而且可以按照資料列狀態或根據篩選條件運算式來篩選資料。 如需詳細資訊，請參閱[Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)。  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A**資料集**包含關聯性中的其<xref:System.Data.DataRelationCollection>物件。 關聯性，由<xref:System.Data.DataRelation>物件，其中一個相關聯資料列**DataTable**中另一個資料列與**DataTable**。 關聯性類似於在關聯式資料庫中，主索引鍵資料行與外部索引鍵資料行之間存在的聯結路徑。 A **DataRelation**識別符合的資料行中的兩個資料表**資料集**。  
  
 關聯性，從一個資料表瀏覽至另一個在**資料集**。 基本項目**DataRelation**為關聯性的名稱、 相關，資料表的名稱和每個資料表中相關的資料行。 藉由將 <xref:System.Data.DataColumn> 物件的陣列指定為索引鍵資料行，可在每個資料表中建立多個資料行的關聯性。 當您將加入的關聯性<xref:System.Data.DataRelationCollection>，您可以選擇性地加入**UniqueKeyConstraint**和**ForeignKeyConstraint**變更相關資料行時，強制執行完整性條件約束值。  
  
 如需詳細資訊，請參閱[加入 Datarelation](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)。  
  
## <a name="xml"></a>XML  
 您可以填入**資料集**從 XML 資料流或文件。 您可以使用 XML 資料流或文件提供給**資料集**資料、 結構描述資訊或兩者。 從 XML 資料流或文件所提供的資訊可以結合現有的資料或結構描述資訊已經存在於**資料集**。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **資料集**， **DataTable**，和**DataColumn**都**ExtendedProperties**屬性。 **ExtendedProperties**是**PropertyCollection**您可以在其中放置自訂資訊，例如 SELECT 陳述式，用來產生結果集或產生資料時的時間。 **ExtendedProperties**集合會保存在一起的結構描述資訊**資料集**。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可為儲存在 DataSet 的中斷連接資料提供 Language-integrated Query (LINQ) 功能。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]使用標準[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]語法，並提供編譯時期語法檢查、 靜態型別和 IntelliSense 支援，當您使用[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]IDE。  
  
 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="see-also"></a>請參閱  
 [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [DataSet、DataTable 和 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
