---
title: 將資料集內容當做 XML 資料寫入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 9a63e79b2fce137ba9d21db861850a471cb42b9f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833960"
---
# <a name="writing-dataset-contents-as-xml-data"></a>將資料集內容當做 XML 資料寫入
在 ADO.NET 中，您可以寫入使用 XML 形式的 <xref:System.Data.DataSet>，具有或不具有其結構描述皆可。 如果結構描述資訊是以 XML 內嵌的，它就會以 XML 結構描述定義語言 (XSD) 寫入。 結構描述包含 <xref:System.Data.DataSet> 的資料表定義，以及關聯性和條件約束定義。  
  
 將 <xref:System.Data.DataSet> 寫為 XML 資料時，<xref:System.Data.DataSet> 中的資料列會以其目前版本寫入。 不過，<xref:System.Data.DataSet> 也可寫入為 DiffGram，如此便能夠包含資料列的目前和原始值。  
  
 @No__t-0 的 XML 標記法可以寫入檔案、資料流程、 **XmlWriter**或字串中。 這些選擇在您要傳輸 XML 形式的 <xref:System.Data.DataSet> 時，可提供相當大的彈性。 若要以字串形式取得 <xref:System.Data.DataSet> 的 XML 標記法，請使用**GetXml**方法，如下列範例所示。  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml**會傳回不含架構資訊 <xref:System.Data.DataSet> 的 XML 標記法。 若要將 <xref:System.Data.DataSet> （XML 架構）的架構資訊寫入字串，請使用**GetXmlSchema**。  
  
 若要將 <xref:System.Data.DataSet> 寫入檔案、資料流程或**XmlWriter**，請使用**WriteXml**方法。 您傳遞至**WriteXml**的第一個參數是 XML 輸出的目的地。 例如，傳遞包含檔案名、system.servicemodel 物件等的字串，**依此類推。** 您可以傳遞**XmlWriteMode**的選擇性第二個參數，以指定寫入 XML 輸出的方式。  
  
 下表顯示**XmlWriteMode**的選項。  
  
|XmlWriteMode 選項|描述|  
|-------------------------|-----------------|  
|**IgnoreSchema**|將 <xref:System.Data.DataSet> 目前的內容寫入為 XML 資料，其中不包含 XML 結構描述。 這是預設值。|  
|**WriteSchema**|將 <xref:System.Data.DataSet> 目前的內容寫入為 XML 資料，它會將關聯式結構做為內嵌 XML 結構描述。|  
|**DiffGram**|將整個 <xref:System.Data.DataSet> 寫入為 DiffGram (包括原始值和目前值)。 如需詳細資訊，請參閱[diffgram](diffgrams.md)。|  
  
 撰寫包含**DataRelation**物件之 <xref:System.Data.DataSet> 的 XML 表示時，您很可能會想要產生的 xml 將每個關聯的子資料列都放在其相關的父項目內。 若要完成這項操作，請**將 datarelation 的** **Nested**屬性設為**true** ，並將**datarelation**新增至 <xref:System.Data.DataSet>。 如需詳細資訊，請參閱 <<c0>嵌套 datarelation。  
  
 以下是兩個範例，說明如何將 <xref:System.Data.DataSet> 的 XML 表示寫入檔案。 第一個範例會將產生的 XML 檔案名當做字串傳遞給**WriteXml**。 第二個範例會傳遞**StreamWriter**物件。
  
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
 您可以使用**DataColumn**物件的**ColumnMapping**屬性，指定資料表中的資料行如何以 XML 表示。 下表顯示資料表資料行之**ColumnMapping**屬性的不同**MappingType**值，以及所產生的 XML。  
  
|MappingType 值|描述|  
|-----------------------|-----------------|  
|**目**|這是預設值。 資料行會寫為 XML 項目，其中 ColumnName 為項目名稱，並且資料行內容會寫為項目文字。 例如:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**屬性**|資料行會寫為目前資料行 XML 項目的 XML 屬性，其中 ColumnName 是屬性名稱，且資料行內容會寫為屬性值。 例如:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|資料行內容會寫為目前資料行 XML 項目中的文字。 例如:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> 請注意，如果資料表的資料行具有**元素**資料行或嵌套關聯，則無法設定**SimpleContent** 。|  
|**隱含**|XML 輸出中不會寫入資料行。|  
  
## <a name="see-also"></a>另請參閱

- [在 DataSet 中使用 XML](using-xml-in-a-dataset.md)
- [DiffGram](diffgrams.md)
- [巢狀 DataRelation](nesting-datarelations.md)
- [將資料集結構描述資訊當作 XSD 寫入](writing-dataset-schema-information-as-xsd.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md)
