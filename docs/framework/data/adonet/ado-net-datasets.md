---
title: "ADO.NET 資料集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# ADO.NET 資料集
<xref:System.Data.DataSet>物件是核心支援中斷連線，分散式的資料案例[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]。 **資料集**是常駐記憶體表示的資料，可提供與資料來源無關的一致性關聯式程式設計模型。 它可與多個不同的資料來源一起使用、與 XML 資料一起使用，或管理應用程式的本機資料。 **資料集**表示一組完整的資料，包括相關的資料表、 條件約束及資料表間的關係。 下圖顯示**資料集**物件模型。  
  
 ![ADO.Net 圖形](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
DataSet 物件模型  
  
 方法和物件**資料集**與關聯式資料庫模型中的一致。  
  
 **資料集**還能保存及重新載入其內容為 XML 和它的結構描述為 XML 結構描述定義語言 (XSD) 結構描述。 如需詳細資訊，請參閱[使用 XML 資料集內](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **資料集**包含零個或多個資料表所表示的集合<xref:System.Data.DataTable>物件。 <xref:System.Data.DataTableCollection>包含所有**DataTable**物件**資料集**。  
  
 A **DataTable**定義於<xref:System.Data>命名空間，表示記憶體常駐資料的單一資料表。 它包含資料行所代表的集合<xref:System.Data.DataColumnCollection>，和所代表的條件約束<xref:System.Data.ConstraintCollection>，其會一起定義的資料表結構描述。 A **DataTable**也包含由資料列集合<xref:System.Data.DataRowCollection>，其中包含資料表中的資料。 目前的狀態，以及<xref:System.Data.DataRow>會保留其目前和原始版本，以識別資料列中儲存之值的變更。  
  
## <a name="the-dataview-class"></a>DataView 類別  
 A <xref:System.Data.DataView>可讓您建立的資料儲存在不同檢視<xref:System.Data.DataTable>，通常用於資料繫結應用程式的功能。 使用<xref:System.Data.DataView>可以公開具有不同排序次序的資料表中的資料，您可以在資料列狀態或根據篩選條件運算式來篩選資料。 如需詳細資訊，請參閱[Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)。  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A**資料集**包含關聯性中的其<xref:System.Data.DataRelationCollection>物件。 關聯性，由<xref:System.Data.DataRelation>物件，將資料列，其中一**DataTable**中另一個資料列與**DataTable**。 關聯性類似於在關聯式資料庫中，主索引鍵資料行與外部索引鍵資料行之間存在的聯結路徑。 A **DataRelation**識別兩個資料表中相符的資料行**資料集**。  
  
 關聯性從一個資料表瀏覽到另一個在**資料集**。 基本項目**DataRelation**是關聯性名稱、 相關，資料表的名稱和每個資料表中相關的資料行。 藉由指定陣列的每個資料表的多個資料行可以建立關聯性<xref:System.Data.DataColumn>物件做為索引鍵資料行。 當您將加入的關聯性<xref:System.Data.DataRelationCollection>，您可以選擇性地加入**UniqueKeyConstraint**和**ForeignKeyConstraint**變更相關資料行值時，強制執行完整性條件約束。  
  
 如需詳細資訊，請參閱[加入 Datarelation](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)。  
  
## <a name="xml"></a>XML  
 您可以填入**資料集**從 XML 資料流或文件。 您可以使用 XML 資料流或文件提供給**資料集**資料、 結構描述資訊或兩者。 從 XML 資料流或文件所提供的資訊可以結合現有的資料或結構描述資訊已經存在於中**資料集**。 如需詳細資訊，請參閱[使用 XML 資料集內](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **資料集**， **DataTable**，和**DataColumn**都**ExtendedProperties**屬性。 **ExtendedProperties**是**PropertyCollection** ，您可以在其中放置自訂資訊，例如 SELECT 陳述式用來產生結果集或產生資料的時間。 **ExtendedProperties**集合永續存在的結構描述資訊**資料集**。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可為儲存在 DataSet 的中斷連接資料提供 Language-integrated Query (LINQ) 功能。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]使用標準[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]語法，並提供編譯時期語法檢查、 靜態型別和 IntelliSense 支援，當您使用[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]IDE。  
  
 如需詳細資訊，請參閱[LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)   
 [Dataset、 Datatable 和 Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)