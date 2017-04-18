---
title: "DataSet 結構描述推斷程序摘要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataSet 結構描述推斷程序摘要
推斷程序首先會決定要將 XML 文件的哪個項目推斷為資料表，  再從剩餘的 XML 決定這些資料表的資料行，  若為巢狀資料表，推斷程序會產生巢狀的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 物件。  
  
 下列為推斷規則的簡明摘要：  
  
-   具有屬性的項目會推斷為資料表。  
  
-   具有項目子系的項目會推斷為資料表。  
  
-   重複的項目會推斷為單一資料表。  
  
-   如果文件或根項目沒有可被推斷為資料行的屬性和子項目，則該項目將被推斷為 <xref:System.Data.DataSet>。  否則，該文件項目就會推斷為資料表。  
  
-   屬性會推斷為資料行。  
  
-   沒有屬性或項目子系且不重複的項目，會推斷為資料行。  
  
-   如果推斷為資料表的項目，位於同時也是推斷為巢狀化資料表的其他項目中，則會在兩個資料表之間建立巢狀化 **DataRelation**。  名為 **TableName\_Id** 的新主索引鍵資料行會加入這兩個資料表中，並由 **DataRelation** 使用。  此外，還會使用 **TableName\_Id** 資料行，在這兩個資料表之間建立 **ForeignKeyConstraint**。  
  
-   如果項目已推斷為資料表且包含文字，但沒有項目子系，則會為每個項目的文字建立一個名為 **TableName\_Text** 的新資料行。  如果項目是推斷為資料表且同時具有文字和項目子系，則會忽略文字。  
  
## 請參閱  
 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)