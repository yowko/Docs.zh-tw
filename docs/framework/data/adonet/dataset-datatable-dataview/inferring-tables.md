---
title: "推斷資料表 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 推斷資料表
從 XML 文件推斷 <xref:System.Data.DataSet> 的結構描述時，ADO.NET 首先會決定要用哪些 XML 項目來表示資料表。  下列 XML 結構將針對 **DataSet** 結構描述產生資料表：  
  
-   具有屬性的項目  
  
-   具有項目子系的項目  
  
-   重複項目  
  
## 具有屬性的項目  
 具有指定屬性的項目會產生推斷資料表。  例如，請考量下列 XML：  
  
```  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 推斷處理序會產生名為 Element1 的資料表。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|attr1|Element1\_Text|  
|-----------|--------------------|  
|value1||  
|value2|Text1|  
  
## 具有項目子系的項目  
 具有項目子系的項目會產生推斷資料表。  例如，請考量下列 XML：  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 推斷處理序會產生名為 Element1 的資料表。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 如果文件或根項目具有將推斷為資料行的屬性或項目子系，便會產生推斷資料表。  如果文件項目沒有可被推斷為資料行的屬性和項目子系，則項目將被推斷為 **DataSet**。  例如，請考量下列 XML：  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 推斷處理序會產生名為 DocumentElement 的資料表。  
  
 **DataSet：**NewDataSet  
  
 **資料表：**DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 另一個方法是考量下列 XML：  
  
```  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推斷程序會產生名為 DocumentElement 的 **DataSet**，其中包含名為 Element1 的資料表。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## 重複項目  
 重複項目會產生單一推斷資料表。  例如，請考量下列 XML：  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 推斷處理序會產生名為 Element1 的資料表。  
  
 **DataSet：**DocumentElement  
  
 **資料表：**Element1  
  
|Element1\_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## 請參閱  
 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)