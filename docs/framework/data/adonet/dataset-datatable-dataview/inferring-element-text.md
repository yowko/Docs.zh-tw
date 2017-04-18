---
title: "推斷項目文字 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 推斷項目文字
如果項目包含文字且沒有推斷為資料表的項目子系 \(例如具有屬性的項目或重複的項目\)，名為 **TableName\_Text** 的新資料行便會被加入為項目推斷的資料表。  項目中包含的文字會加入資料表中的資料列，並儲存在新資料行內。  新資料行的 **ColumnMapping** 屬性會被設定為 **MappingType.SimpleContent**。  
  
 例如，請考量下列 XML。  
  
```  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 推斷程序將產生名為 **Element1** 的資料表，其中有兩個資料行：**attr1** 和 **Element1\_Text**。  **attr1** 資料行的 **ColumnMapping** 屬性會設定為 **MappingType.Attribute**。  **Element1\_Text** 資料行的 **ColumnMapping** 屬性會設定為 **MappingType.SimpleContent**。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|attr1|Element1\_Text|  
|-----------|--------------------|  
|value1|Text1|  
  
 如果項目包含文字，但是它的項目子系也包含文字，則不會有資料行加入資料表來儲存項目中包含的文字。  包含在項目中的文字會被忽略，而項目子系中的文字會被包含在資料表的資料列內。  例如，請考量下列 XML。  
  
```  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 推斷程序會產生名為 **Element1** 的資料表，並具有一個名為 **ChildElement1** 的資料行。  **ChildElement1** 項目的文字會被包含在資料表的資料列內。  其他文字則被忽略。  **ChildElement1** 資料行的 **ColumnMapping** 屬性會設定為 **MappingType.Element**。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## 請參閱  
 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)