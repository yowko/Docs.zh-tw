---
title: "推斷關聯性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 推斷關聯性
若被推斷為資料表的項目具有子項目，且子項目也被推斷為資料表，則兩個資料表間會建立 <xref:System.Data.DataRelation>。  這時，名為 **ParentTableName\_Id** 的新資料行會被加入為父項目建立的資料表，以及為項目子系建立的資料表。  這個識別欄位的 **ColumnMapping** 屬性會被設定為 **MappingType.Hidden**。  該資料行將成為父資料表的自動遞增主索引鍵，且會用於兩個資料表間的 **DataRelation**。  加入的識別欄位的資料型別將是 **System.Int32**，而其他所有推斷資料行的資料型別是 **System.String**。  也會使用父資料表和子資料表中的新資料行，建立 **DeleteRule** \= **Cascade** 的 <xref:System.Data.ForeignKeyConstraint>。  
  
 例如，請考量下列 XML：  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推斷處理序會產生兩個資料表：**Element1** 與 **ChildElement1**。  
  
 **Element1** 資料表會有兩個資料行：**Element1\_Id** 與 **ChildElement2**。  **Element1\_Id** 資料行的 **ColumnMapping** 屬性會設定為 **MappingType.Hidden**。  **ChildElement2** 資料行的 **ColumnMapping** 屬性會設定為 **MappingType.Element**。  **Element1\_Id** 資料行將設為 **Element1** 資料表的主索引鍵。  
  
 **ChildElement1** 資料表會有三個資料行：**attr1**、**attr2** 和 **Element1\_Id**。  **attr1** 和 **attr2** 資料行的 **ColumnMapping** 屬性會被設定為 **MappingType.Attribute**。  **Element1\_Id** 資料行的 **ColumnMapping** 屬性會設定為 **MappingType.Hidden**。  
  
 **DataRelation** 和 **ForeignKeyConstraint** 則會使用兩個資料表的 **Element1\_Id** 資料行建立。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|Element1\_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **資料表：**ChildElement1  
  
|attr1|attr2|Element1\_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation：**Element1\_ChildElement1  
  
 **ParentTable：**Element1  
  
 **ParentColumn：**Element1\_Id  
  
 **ChildTable：**ChildElement1  
  
 **ChildColumn：**Element1\_Id  
  
 **Nested：**True  
  
 **ForeignKeyConstraint：**Element1\_ChildElement1  
  
 **Column：**Element1\_Id  
  
 **ParentTable：**Element1  
  
 **ChildTable：**ChildElement1  
  
 **DeleteRule：**Cascade  
  
 **AcceptRejectRule：**None  
  
## 請參閱  
 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [巢狀 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)   
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)