---
title: "推斷限制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 推斷限制
根據每份文件的 XML 項目，當您執行從 XML 推斷 <xref:System.Data.DataSet> 結構描述的處理序時，可能會得到不同的結構描述。  例如，請考量下列 XML 文件。  
  
 Document1:  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2:  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 若為 Document1，則因為 Element1 是重複的項目，所以推斷程序會產生名為 DocumentElement 的 **DataSet**，和名為 Element1 的資料表。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|Element1\_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 但是，推斷程序會為 Document2 產生名為 NewDataSet 的 **DataSet**，和名為 DocumentElement 的資料表。Element1 會被推斷為資料行，因為它沒有屬性和項目子系。  
  
 **DataSet：**NewDataSet  
  
 **資料表：**DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 這兩份 XML 文件原本可能意圖要產生相同的結構描述，但是根據每份文件包含的項目，推斷程序產生了相當不同的結果。  
  
 若要避免從 XML 文件產生結構描述時發生不一致的情況，建議您從 XML 載入 **DataSet** 時，使用 XML 結構描述定義語言 \(XSD\) 或 XML 資料精簡 \(XDR\) 來明確地指定結構描述。  如需有關使用 XML 結構描述明確指定 **DataSet** 結構描述的詳細資訊，請參閱[從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
## 請參閱  
 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)