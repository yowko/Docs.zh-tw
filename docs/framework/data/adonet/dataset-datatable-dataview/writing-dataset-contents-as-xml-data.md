---
title: 將資料集內容當做 XML 資料寫入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 44afa79d715ef62bcbd1c242a533876d911345c8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761905"
---
# <a name="writing-dataset-contents-as-xml-data"></a>將資料集內容當做 XML 資料寫入
在 ADO.NET 中，您可以寫入使用 XML 形式的 <xref:System.Data.DataSet>，具有或不具有其結構描述皆可。 如果結構描述資訊是以 XML 內嵌的，它就會以 XML 結構描述定義語言 (XSD) 寫入。 結構描述包含 <xref:System.Data.DataSet> 的資料表定義，以及關聯性和條件約束定義。  
  
 將 <xref:System.Data.DataSet> 寫為 XML 資料時，<xref:System.Data.DataSet> 中的資料列會以其目前版本寫入。 不過，<xref:System.Data.DataSet> 也可寫入為 DiffGram，如此便能夠包含資料列的目前和原始值。  
  
 XML 表示法<xref:System.Data.DataSet>可以寫入檔案時，資料流， **XmlWriter**，或字串。 這些選擇在您要傳輸 XML 形式的 <xref:System.Data.DataSet> 時，可提供相當大的彈性。 若要取得的 XML 表示法<xref:System.Data.DataSet>為字串時，使用**GetXml**方法，如下列範例所示。  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml**傳回的 XML 表示法<xref:System.Data.DataSet>不含結構描述資訊。 要寫入的結構描述資訊<xref:System.Data.DataSet>（做為 XML 結構描述） 字串，使用**GetXmlSchema**。  
  
 要寫入<xref:System.Data.DataSet>檔案資料流，或**XmlWriter**，使用**WriteXml**方法。 第一個參數傳遞給**WriteXml** XML 輸出的目的地。 例如，傳遞字串，包含檔案名稱， **System.IO.TextWriter**物件，依此類推。 您可以將選擇性的第二個參數傳遞**XmlWriteMode**來指定要如何寫入 XML 輸出。  
  
 下表顯示的選項**XmlWriteMode**。  
  
|XmlWriteMode 選項|描述|  
|-------------------------|-----------------|  
|**IgnoreSchema**|將 <xref:System.Data.DataSet> 目前的內容寫入為 XML 資料，其中不包含 XML 結構描述。 這是預設值。|  
|**WriteSchema**|將 <xref:System.Data.DataSet> 目前的內容寫入為 XML 資料，它會將關聯式結構做為內嵌 XML 結構描述。|  
|**DiffGram**|將整個 <xref:System.Data.DataSet> 寫入為 DiffGram (包括原始值和目前值)。 如需詳細資訊，請參閱[DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。|  
  
 寫入的 XML 表示法時<xref:System.Data.DataSet>包含**DataRelation**物件，您最有可能會想讓每個關聯性相關的父項目內變成巢狀的子資料列所產生的 XML。 若要達成此目的，設定**巢狀**屬性**DataRelation**至**true**當您將加入**DataRelation** 至<xref:System.Data.DataSet>. 如需詳細資訊，請參閱[巢狀 Datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)。  
  
 下列兩個範例說明如何將 XML 形式的 <xref:System.Data.DataSet> 寫入檔案中。 第一個範例會將產生的 XML 檔案名稱傳遞為字串**WriteXml**。 第二個範例傳遞**System.IO.StreamWriter**物件。  
  
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
  
|MappingType 值|描述|  
|-----------------------|-----------------|  
|**目**|這是預設值。 資料行會寫為 XML 項目，其中 ColumnName 為項目名稱，並且資料行內容會寫為項目文字。 例如: <br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**屬性**|資料行會寫為目前資料行 XML 項目的 XML 屬性，其中 ColumnName 是屬性名稱，且資料行內容會寫為屬性值。 例如: <br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|資料行內容會寫為目前資料行 XML 項目中的文字。 例如: <br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> 請注意， **SimpleContent**無法設定資料行的資料表包含**元素**資料行或巢狀的關聯。|  
|**隱藏**|XML 輸出中不會寫入資料行。|  
  
## <a name="see-also"></a>另請參閱  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [巢狀 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [將資料集結構描述資訊當作 XSD 寫入](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
