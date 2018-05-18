---
title: 使用 XPathNavigator 移除 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87dc7d83692f081f2c48a34cef8a33564f0e3089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="remove-xml-data-using-xpathnavigator"></a>使用 XPathNavigator 移除 XML 資料
<xref:System.Xml.XPath.XPathNavigator> 類別提供一組可用來從 XML 文件移除節點及值的方法。 為了使用這些方法，<xref:System.Xml.XPath.XPathNavigator> 物件必須是可編輯的，也就是說，它的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性必須為 `true`。  
  
 可編輯 XML 文件的 <xref:System.Xml.XPath.XPathNavigator> 物件是由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 類別的 <xref:System.Xml.XmlDocument> 方法所建立。 由 <xref:System.Xml.XPath.XPathNavigator> 類別建立的 <xref:System.Xml.XPath.XPathDocument> 物件是唯讀的，而且如果嘗試使用由 <xref:System.Xml.XPath.XPathNavigator> 物件建立之 <xref:System.Xml.XPath.XPathDocument> 物件的編輯方法，則會導致 <xref:System.NotSupportedException>。  
  
 如需有關建立可編輯 <xref:System.Xml.XPath.XPathNavigator> 物件的詳細資訊，請參閱[使用 XPathDocument 和 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)。  
  
## <a name="removing-nodes"></a>移除節點  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法，以從 XML 文件移除節點。  
  
### <a name="removing-a-node"></a>移除節點  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法，以從 XML 文件刪除 <xref:System.Xml.XPath.XPathNavigator> 物件目前所位於的目前節點。  
  
 在使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法刪除節點之後，就無法從 <xref:System.Xml.XmlDocument> 物件的根存取此節點。 刪除節點之後，<xref:System.Xml.XPath.XPathNavigator> 定位於已刪除節點的父節點上。  
  
 刪除作業不會影響定位於已刪除節點上任何 <xref:System.Xml.XPath.XPathNavigator> 物件的位置。 這些 <xref:System.Xml.XPath.XPathNavigator> 物件是有效的，這表示它們可在已刪除的樹狀子目錄內移動，但無法使用 <xref:System.Xml.XPath.XPathNavigator> 類別的一般節點集巡覽方法，移至主節點樹狀目錄。  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 方法可用來將這些 <xref:System.Xml.XPath.XPathNavigator> 物件移回主節點樹狀目錄，或從主節點樹狀目錄移至刪除的樹狀子目錄。  
  
 在下列範例中，使用 `price` 方法，刪除 `book` 檔案之第一個 `contosoBooks.xml` 項目的 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 項目。 刪除 <xref:System.Xml.XPath.XPathNavigator> 項目之後，`price` 物件的位置在父 `book` 項目上。  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>移除屬性節點  
 使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法，從 XML 文件移除屬性節點。  
  
 刪除屬性節點之後，無法再從 <xref:System.Xml.XmlDocument> 物件的根節點存取此節點，而且 <xref:System.Xml.XPath.XPathNavigator> 物件定位於父項目上。  
  
#### <a name="default-attributes"></a>預設屬性  
 無論用來移除屬性的方法為何，對於移除 XML 文件之 DTD 或 XML 結構描述中定義為預設屬性的屬性，都有特殊限制。 除非同時移除其所屬項目，否則無法移除預設屬性。 對於已宣告預設屬性的項目，預設屬性始終存在，因此刪除預設屬性會導致在項目中插入取代屬性，並將其初始化為已宣告的預設值。  
  
## <a name="removing-values"></a>移除值  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法，以從 XML 文件移除不具型別值及具型別值。  
  
### <a name="removing-untyped-values"></a>移除不具型別值  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只會插入做為參數傳遞的不具型別 `string` 值，並將其做為 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的值。 將空字串傳遞至 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法，會移除目前節點的值。  
  
 下列範例使用 `price` 方法，移除 `book` 檔案中第一個 `contosoBooks.xml` 項目的 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 項目值。  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>移除具型別值  
 當節點的型別為 W3C XML 結構描述簡單型別時，會根據簡單型別的 Facet，對 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法插入的新值執行設定前的檢查。 如果根據節點的型別，新值無效 (例如，在型別為 `-1` 的項目上設定 `xs:positiveInteger` 值)，則會導致例外狀況。 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法也無法將 `null` 當做參數傳遞。 因此，移除具型別節點的值時必須遵守節點的結構描述型別。  
  
 下列範例使用 `price` 方法，將值設為 `book`，來移除 `contosoBooks.xml` 檔案中第一個 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 項目的 `0` 項目值。 不會移除節點的值，但是根據書籍之價格的 `xs:decimal` 資料型別，已移除該價格。  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a>命名空間節點  
 無法從 <xref:System.Xml.XmlDocument> 物件刪除命名空間節點。 嘗試使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法刪除命名空間節點，會導致例外狀況。  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml 及 OuterXml 屬性  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的 XML 標記。  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及指定 XML `string` 的已剖析內容。 同樣地，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及目前節點本身。  
  
 除了本主題中所說明的方法之外，還可以使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性，從 XML 文件移除節點及值。 如需使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性修改節點的詳細資訊，請參閱[使用 XPathNavigator 修改 XML 資料](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)主題。  
  
## <a name="saving-an-xml-document"></a>儲存 XML 文件  
 使用 <xref:System.Xml.XmlDocument> 類別的方法，將用本主題中說明之方法對 <xref:System.Xml.XmlDocument> 物件所做的變更儲存下來。 如需儲存 <xref:System.Xml.XmlDocument> 物件之變更的詳細資訊，請參閱[儲存與寫入文件](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [使用 XPathNavigator 插入 XML 資料](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [使用 XPathNavigator 修改 XML 資料](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
