---
title: 將資料集結構描述資訊當做 XSD 寫入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 2a59a9fc1c3b2f52543f4cc69de22a5703fa9b8b
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44707431"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="29696-102">將資料集結構描述資訊當做 XSD 寫入</span><span class="sxs-lookup"><span data-stu-id="29696-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="29696-103">您可以將 <xref:System.Data.DataSet> 的結構描述寫為 XML 結構描述定義語言 (XSD) 結構描述，即可以在 XML 文件中進行傳輸，而不論是否有任何相關資料。</span><span class="sxs-lookup"><span data-stu-id="29696-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="29696-104">XML 結構描述寫入檔案時，資料流<xref:System.Xml.XmlWriter>，或字串，它可用於產生強型別**資料集**。</span><span class="sxs-lookup"><span data-stu-id="29696-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="29696-105">如需有關強型別**資料集**物件，請參閱[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="29696-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="29696-106">您可以指定如何將資料表資料行表示 XML 結構描述中使用**ColumnMapping**屬性<xref:System.Data.DataColumn>物件。</span><span class="sxs-lookup"><span data-stu-id="29696-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="29696-107">如需詳細資訊，請參閱 「 至 XML 項目、 屬性和文字的對應資料行 」 中[寫入為 XML 資料的資料集內容](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="29696-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="29696-108">要寫入的結構描述**資料集**做為檔案，XML 結構描述，資料流，或**XmlWriter**，使用**WriteXmlSchema**方法**DataSet**。</span><span class="sxs-lookup"><span data-stu-id="29696-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="29696-109">**WriteXmlSchema**接受一個參數，指定產生的 XML 結構描述的目的地。</span><span class="sxs-lookup"><span data-stu-id="29696-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="29696-110">下列程式碼範例示範如何撰寫的 XML 結構描述**資料集**藉由傳遞字串，包含檔案名稱的檔案和<xref:System.IO.StreamWriter>物件。</span><span class="sxs-lookup"><span data-stu-id="29696-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="29696-111">若要取得的結構描述**資料集**並將它撰寫為 XML 結構描述字串，請使用**GetXmlSchema**方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="29696-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="29696-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29696-112">See Also</span></span>  
 [<span data-ttu-id="29696-113">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="29696-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="29696-114">將資料集內容當作 XML 資料寫入</span><span class="sxs-lookup"><span data-stu-id="29696-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="29696-115">具類型的 DataSet</span><span class="sxs-lookup"><span data-stu-id="29696-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="29696-116">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="29696-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="29696-117">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="29696-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
