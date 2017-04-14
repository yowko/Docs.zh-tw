---
title: "推斷資料行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 推斷資料行
ADO.NET 從 XML 文件中判斷要將哪些項目推斷成 <xref:System.Data.DataSet> 的資料表後，接著就會推斷這些資料表的資料行。  ADO.NET 2.0 導入了新的結構描述推斷引擎，可推斷每個 **simpleType** 項目的強型別資料型別。  在舊版本中，已推斷 **simpleType** 項目的資料型別一定會是 **xsd:string**。  
  
## 移轉和回溯相容性  
 **ReadXml** 方法使用 **InferSchema** 型別的引數。  這個引數可讓您指定與舊版本相容的推斷行為。  下表顯示 **InferSchema** 列舉型別可用的值。  
  
 <xref:System.Data.XmlReadMode>  
 將簡單型別永遠推斷為 <xref:System.String>，以提供回溯相容性 \(Backward Compatibility\)。  
  
 <xref:System.Data.XmlReadMode>  
 推斷強型別資料型別。  若用於 <xref:System.Data.DataTable>，則會擲回例外狀況 \(Exception\)。  
  
 <xref:System.Data.XmlReadMode>  
 忽略任何內嵌結構描述，並將資料讀入現有的 <xref:System.Data.DataSet> 結構描述中。  
  
## 屬性  
 如同[推斷資料表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)中所定義，具有屬性的項目會推斷為資料表。  然後，該項目的屬性會推斷為資料表的資料行。  資料行的 **ColumnMapping** 屬性會設定為 **MappingType.Attribute**，以確保將結構描述寫回 XML 時，資料行名稱會以屬性寫入。  屬性的值儲存在資料表的資料列中。  例如，請考量下列 XML：  
  
```  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推斷程序將產生名為 **Element1** 的資料表，其中有 **attr1** 和 **attr2** 兩個資料行。  這兩個資料行的 **ColumnMapping** 屬性都會設定為 **MappingType.Attribute**。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## 沒有屬性或項目子系的項目  
 如果項目沒有項目子系或屬性，則會推斷為資料行。  資料行的 **ColumnMapping** 屬性會設定為 **MappingType.Element**。  項目子系的文字儲存在資料表的資料列中。  例如，請考量下列 XML：  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推斷程序會產生名為 **Element1** 的資料表，其中有 **ChildElement1** 和 **ChildElement2** 兩行資料行。  這兩個資料行的 **ColumnMapping** 屬性都會設定為 **MappingType.Element**。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## 請參閱  
 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)