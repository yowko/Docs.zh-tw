---
title: "將資料集內容當做 XML 資料寫入 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 將資料集內容當做 XML 資料寫入
您可以在 ADO.NET 中撰寫的 XML 表示法<xref:System.Data.DataSet>、 使用或不具備其結構描述。 如果結構描述資訊是以 XML 內嵌的，它就會以 XML 結構描述定義語言 (XSD) 寫入。 結構描述中包含的資料表定義<xref:System.Data.DataSet>以及關聯和條件約束定義。  
  
 當<xref:System.Data.DataSet>撰寫為 XML 資料中的資料列<xref:System.Data.DataSet>會以其目前的版本。 不過，<xref:System.Data.DataSet>也會寫入為 DiffGram，以便將會包含目前和原始值的資料列。  
  
 XML 表示法<xref:System.Data.DataSet>可以寫入檔案時，資料流， **XmlWriter**，或字串。 這些選擇您要傳輸的 XML 表示法提供很大的彈性<xref:System.Data.DataSet>。 若要取得的 XML 表示法<xref:System.Data.DataSet>為字串時，使用**GetXml**方法，如下列範例所示。  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml**傳回的 XML 表示法<xref:System.Data.DataSet>不含結構描述資訊。 要寫入的結構描述資訊<xref:System.Data.DataSet>（做為 XML 結構描述） 字串，使用**GetXmlSchema**。  
  
 要寫入<xref:System.Data.DataSet>檔案資料流，或**XmlWriter**，使用**WriteXml**方法。 第一個參數傳遞至**WriteXml**是 XML 輸出的目的地。 例如，傳遞字串，包含檔案名稱、 **System.IO.TextWriter**物件，依此類推。 您可以將選擇性的第二個參數傳遞**XmlWriteMode**以指定要寫入的 XML 輸出的方式。  
  
 下表顯示的選項**XmlWriteMode**。  
  
|XmlWriteMode 選項|描述|  
|-------------------------|-----------------|  
|**IgnoreSchema**|目前的內容寫入<xref:System.Data.DataSet>為 XML 資料，不包含 XML 結構描述。 這是預設值。|  
|**WriteSchema**|目前的內容寫入<xref:System.Data.DataSet>為關聯式結構做為內嵌 XML 結構描述與 XML 資料。|  
|**DiffGram**|將整個<xref:System.Data.DataSet>為 DiffGram，包括原始和目前的值。 如需詳細資訊，請參閱[DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。|  
  
 撰寫的 XML 表示法時<xref:System.Data.DataSet>，其中包含**DataRelation**物件時，很可能會想讓每個關聯其相關的父項目內的巢狀的子資料列所產生的 XML。 若要達成此目的，設定**巢狀**屬性**DataRelation**至**true**當您新增**DataRelation**至<xref:System.Data.DataSet>。 如需詳細資訊，請參閱[巢狀 Datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)。  
  
 下列兩個範例說明如何撰寫的 XML 表示法<xref:System.Data.DataSet>檔案。 第一個範例會產生的 XML 檔案名稱傳遞為字串**WriteXml**。 第二個範例會傳遞**System.IO.StreamWriter**物件。  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>對應資料行至 XML 項目、屬性和文字  
 您可以指定如何以 XML 表示資料表的資料行使用**ColumnMapping**屬性**DataColumn**物件。 下表顯示不同**MappingType**值**ColumnMapping**的資料表資料行，以及產生的 XML 屬性。  
  
|MappingType 值|說明|  
|-----------------------|-----------------|  
|**項目**|這是預設值。 資料行會寫為 XML 項目，其中 ColumnName 為項目名稱，並且資料行內容會寫為項目文字。 例如：<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**屬性**|資料行會寫為目前資料行 XML 項目的 XML 屬性，其中 ColumnName 是屬性名稱，且資料行內容會寫為屬性值。 例如：<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|資料行內容會寫為目前資料行 XML 項目中的文字。 例如：<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> 請注意， **SimpleContent**無法設定資料行的資料表具有**元素**資料行或巢狀的關聯。|  
|**隱藏**|XML 輸出中不會寫入資料行。|  
  
## <a name="see-also"></a>另請參閱  
 [在資料集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)   
 [巢狀 Datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)   
 [將資料集結構描述資訊當做 XSD 寫入](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)   
 [Dataset、 Datatable 和 Dataview](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)