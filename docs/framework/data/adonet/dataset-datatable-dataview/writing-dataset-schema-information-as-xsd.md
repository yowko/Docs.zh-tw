---
title: 將資料集結構描述資訊當做 XSD 寫入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 2a59a9fc1c3b2f52543f4cc69de22a5703fa9b8b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674260"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>將資料集結構描述資訊當做 XSD 寫入
您可以將 <xref:System.Data.DataSet> 的結構描述寫為 XML 結構描述定義語言 (XSD) 結構描述，即可以在 XML 文件中進行傳輸，而不論是否有任何相關資料。 XML 結構描述寫入檔案時，資料流<xref:System.Xml.XmlWriter>，或字串，它可用於產生強型別**資料集**。 如需有關強型別**資料集**物件，請參閱[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。  
  
 您可以指定如何將資料表資料行表示 XML 結構描述中使用**ColumnMapping**屬性<xref:System.Data.DataColumn>物件。 如需詳細資訊，請參閱 「 至 XML 項目、 屬性和文字的對應資料行 」 中[寫入為 XML 資料的資料集內容](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)。  
  
 要寫入的結構描述**資料集**做為檔案，XML 結構描述，資料流，或**XmlWriter**，使用**WriteXmlSchema**方法**DataSet**。 **WriteXmlSchema**接受一個參數，指定產生的 XML 結構描述的目的地。 下列程式碼範例示範如何撰寫的 XML 結構描述**資料集**藉由傳遞字串，包含檔案名稱的檔案和<xref:System.IO.StreamWriter>物件。  
  
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
  
 若要取得的結構描述**資料集**並將它撰寫為 XML 結構描述字串，請使用**GetXmlSchema**方法，如下列範例所示。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [將資料集內容當作 XML 資料寫入](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [具類型的 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
