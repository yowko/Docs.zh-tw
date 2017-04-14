---
title: "將 DataSet 結構描述資訊寫為 XSD | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 將 DataSet 結構描述資訊寫為 XSD
您可以將 <xref:System.Data.DataSet> 的結構描述寫為 XML 結構描述定義語言 \(XSD\) 結構描述，即可以在 XML 文件中進行傳輸，而不論是否有任何相關資料。  XML 結構描述可以寫入檔案、資料流、<xref:System.Xml.XmlWriter> 或字串，對於產生強型別的 **DataSet** 相當有用。  如需關於強型別 **DataSet** 物件的詳細資訊，請參閱 [具型別的 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。  
  
 您可以使用 <xref:System.Data.DataColumn> 物件的 **ColumnMapping** 屬性，指定資料表的資料行如何以 XML 結構描述來表示。  如需詳細資訊，請參閱 [將 DataSet 內容撰寫成 XML 資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md) 中的＜對應資料行至 XML 項目、屬性和文字＞。  
  
 若要將 **DataSet** 的結構描述寫為 XML 結構描述或寫入檔案、資料流或 **XmlWriter**，請使用 **DataSet** 的 **WriteXmlSchema** 方法。  **WriteXmlSchema** 採用的某個參數，會指定所產生 XML 結構描述的目的端。  下列程式碼範例會說明如何藉由傳遞包含檔名和 <xref:System.IO.StreamWriter> 物件的字串，將 **DataSet** 的 XML 結構描述寫入檔案。  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 若要取得 **DataSet** 的結構描述，並將它寫為 XML 結構描述字串，請使用下列範例所示的 **GetXmlSchema** 方法。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## 請參閱  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [將 DataSet 內容撰寫成 XML 資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)   
 [具型別的 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)