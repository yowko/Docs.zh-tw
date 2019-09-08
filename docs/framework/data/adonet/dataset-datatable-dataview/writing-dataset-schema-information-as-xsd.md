---
title: 將資料集結構描述資訊當做 XSD 寫入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f86e9100489ddf35d8ef5f98e386306a7dbfd4ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784174"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>將資料集結構描述資訊當做 XSD 寫入
您可以將 <xref:System.Data.DataSet> 的結構描述寫為 XML 結構描述定義語言 (XSD) 結構描述，即可以在 XML 文件中進行傳輸，而不論是否有任何相關資料。 可以將 XML 架構寫入檔案、資料流程、 <xref:System.Xml.XmlWriter>或字串，這對於產生強型別**資料集**很有説明。 如需強型別**資料集**物件的詳細資訊，請參閱具[類型的資料集](typed-datasets.md)。  
  
 您可以使用<xref:System.Data.DataColumn>物件的**ColumnMapping**屬性，指定資料表中的資料行如何以 XML 架構表示。 如需詳細資訊，請參閱將[資料集內容撰寫為 Xml 資料](writing-dataset-contents-as-xml-data.md)中的「將資料行對應至 xml 元素、屬性和文字」。  
  
 若要將**資料集**的架構當做 XML 架構寫入檔案、資料流程或**XmlWriter**中，請使用**DataSet**的**WriteXmlSchema**方法。 **WriteXmlSchema**會採用一個參數，指定所產生之 XML 架構的目的地。 下列程式碼範例示範如何藉由傳遞包含檔案名和<xref:System.IO.StreamWriter>物件的字串，將**DataSet**的 XML 架構寫入檔案。  
  
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
  
 若要取得**資料集**的架構，並將它寫入為 XML 架構字串，請使用**GetXmlSchema**方法，如下列範例所示。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>另請參閱

- [在 DataSet 中使用 XML](using-xml-in-a-dataset.md)
- [將資料集內容當作 XML 資料寫入](writing-dataset-contents-as-xml-data.md)
- [具類型的 DataSet](typed-datasets.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md)
