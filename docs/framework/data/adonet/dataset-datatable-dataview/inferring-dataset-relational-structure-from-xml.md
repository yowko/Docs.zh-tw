---
title: "從 XML 推斷 DataSet 關聯式結構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 從 XML 推斷 DataSet 關聯式結構
<xref:System.Data.DataSet> 的關聯式結構或結構描述是由資料表、資料行、條件約束和關聯所組成。  從 XML 載入 <xref:System.Data.DataSet> 時，可預先定義結構描述，也可從正在載入的 XML 中，明確或透過介面建立。  如需從 XML 載入 <xref:System.Data.DataSet> 之結構描述和內容的詳細資訊，請參閱[從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) 和[從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)。  
  
 如果正在從 XML 建立 <xref:System.Data.DataSet> 的結構描述，則慣用的方法為使用 XML 結構描述定義語言 \(XSD\) \(如[從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)中所述\) 或 XML 資料精簡 \(XDR\) 來明確地指定結構描述。  如果 XML 中沒有可用的 XML 結構描述或 XDR 結構描述，可從 XML 項目和屬性的結構推斷出 <xref:System.Data.DataSet> 的結構描述。  
  
 本節藉由顯示 XML 項目和屬性及其結構，以及產生的推斷 <xref:System.Data.DataSet> 結構描述，說明 <xref:System.Data.DataSet> 結構描述的推斷規則。  
  
 推斷程序中並不需要包含 XML文件中的所有屬性。  符合命名空間的屬性可包含對 XML 文件重要、但對 <xref:System.Data.DataSet> 結構描述不重要的中繼資料。  您可以使用 <xref:System.Data.DataSet.InferXmlSchema%2A>，指定在推斷處理序中要忽略的命名空間。  如需詳細資訊，請參閱[從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)。  
  
## 在本節中  
 [DataSet 結構描述推斷程序摘要](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 提供進階摘要，說明從 XML 推斷 <xref:System.Data.DataSet> 結構描述的規則。  
  
 [推斷資料表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 說明被推斷為 <xref:System.Data.DataSet> 中資料表的 XML 項目。  
  
 [推斷資料行](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 說明被推斷為資料表資料行的 XML 項目和屬性。  
  
 [推斷關聯性](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 說明針對巢狀推斷資料表建立的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 物件。  
  
 [推斷項目文字](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 說明建立為 XML 項目內文字的資料行，並說明 XML 項目中的文字何時會被忽略。  
  
 [推斷限制](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 討論結構描述推論的限制。  
  
## 相關章節  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 說明 <xref:System.Data.DataSet> 物件如何與 XML 資料互動。  
  
 [從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 說明根據 XML 結構描述定義語言 \(XSD\) 結構描述所建立的 <xref:System.Data.DataSet> 關聯式結構 \(或結構描述\)。  
  
 [ADO.NET 概觀](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 描述 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)