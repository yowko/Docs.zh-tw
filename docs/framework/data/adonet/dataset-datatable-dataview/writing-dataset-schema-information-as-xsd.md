---
title: 將資料集結構描述資訊當做 XSD 寫入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f9664d8e7bc221da68492140f30419ea8fb0d316
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204360"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="6f9be-102">將資料集結構描述資訊當做 XSD 寫入</span><span class="sxs-lookup"><span data-stu-id="6f9be-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="6f9be-103">您可以將 <xref:System.Data.DataSet> 的結構描述寫為 XML 結構描述定義語言 (XSD) 結構描述，即可以在 XML 文件中進行傳輸，而不論是否有任何相關資料。</span><span class="sxs-lookup"><span data-stu-id="6f9be-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="6f9be-104">可以將 XML 架構寫入檔案、資料流程、 <xref:System.Xml.XmlWriter>或字串, 這對於產生強型別**資料集**很有説明。</span><span class="sxs-lookup"><span data-stu-id="6f9be-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="6f9be-105">如需強型別**資料集**物件的詳細資訊, 請參閱具[類型的資料集](typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="6f9be-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="6f9be-106">您可以使用<xref:System.Data.DataColumn>物件的**ColumnMapping**屬性, 指定資料表中的資料行如何以 XML 架構表示。</span><span class="sxs-lookup"><span data-stu-id="6f9be-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="6f9be-107">如需詳細資訊, 請參閱將[資料集內容撰寫為 Xml 資料](writing-dataset-contents-as-xml-data.md)中的「將資料行對應至 xml 元素、屬性和文字」。</span><span class="sxs-lookup"><span data-stu-id="6f9be-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="6f9be-108">若要將**資料集**的架構當做 XML 架構寫入檔案、資料流程或**XmlWriter**中, 請使用**DataSet**的**WriteXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="6f9be-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="6f9be-109">**WriteXmlSchema**會採用一個參數, 指定所產生之 XML 架構的目的地。</span><span class="sxs-lookup"><span data-stu-id="6f9be-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="6f9be-110">下列程式碼範例示範如何藉由傳遞包含檔案名和<xref:System.IO.StreamWriter>物件的字串, 將**DataSet**的 XML 架構寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="6f9be-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="6f9be-111">若要取得**資料集**的架構, 並將它寫入為 XML 架構字串, 請使用**GetXmlSchema**方法, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6f9be-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f9be-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f9be-112">See also</span></span>

- [<span data-ttu-id="6f9be-113">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="6f9be-113">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="6f9be-114">將資料集內容當作 XML 資料寫入</span><span class="sxs-lookup"><span data-stu-id="6f9be-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- [<span data-ttu-id="6f9be-115">具類型的 DataSet</span><span class="sxs-lookup"><span data-stu-id="6f9be-115">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="6f9be-116">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="6f9be-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="6f9be-117">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6f9be-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
