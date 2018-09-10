---
title: 使用 XPathNavigator 擷取 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d838f3d9f4c9400fbbef0fb24f5275eff2038c49
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262109"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>使用 XPathNavigator 擷取 XML 資料
可採用幾種不同方式表示 Microsoft .NET Framework 中的 XML 文件。 包括使用 <xref:System.String>，或使用 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、<xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathDocument> 類別。 為便於在 XML 文件的不同表示之間進行切換，<xref:System.Xml.XPath.XPathNavigator> 類別提供了一些方法及屬性，可將 XML 當做 <xref:System.String>、<xref:System.Xml.XmlReader> 物件或 <xref:System.Xml.XmlWriter> 物件擷取。  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>將 XPathNavigator 轉換為字串  
 可使用 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 屬性，取得整個 XML 文件的標記，或僅取得單一節點及其子節點的標記。  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 屬性僅取得節點之子節點的標記。  
  
 下列程式碼範例顯示如何將 <xref:System.Xml.XPath.XPathNavigator> 物件中包含的整個 XML 文件與單一節點及其子節點，儲存為 <xref:System.String>。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("input.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Save the entire input.xml document to a string.  
Dim xml As String = navigator.OuterXml  
  
' Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element)  
Dim root As String = navigator.OuterXml  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Save the entire input.xml document to a string.  
string xml = navigator.OuterXml;  
  
// Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element);  
string root = navigator.OuterXml;  
```  
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>將 XPathNavigator 轉換為 XmlReader  
 使用 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> 方法，將 XML 文件或僅單一節點及其子節點的全部內容，以資料流方式傳送至 <xref:System.Xml.XmlReader> 物件。  
  
 以目前節點及其子節點建立 <xref:System.Xml.XmlReader> 物件時，會將 <xref:System.Xml.XmlReader> 物件的 <xref:System.Xml.XmlReader.ReadState%2A> 屬性設為 <xref:System.Xml.ReadState.Initial>。 當初次呼叫 <xref:System.Xml.XmlReader> 物件的 <xref:System.Xml.XmlReader.Read%2A> 方法時，<xref:System.Xml.XmlReader> 會移至 <xref:System.Xml.XPath.XPathNavigator> 的目前節點。 新的 <xref:System.Xml.XmlReader> 物件在到達 XML 樹狀目錄的尾端之前，會持續讀取。 此時，<xref:System.Xml.XmlReader.Read%2A> 方法會傳回 `false`，且 <xref:System.Xml.XmlReader> 物件的 <xref:System.Xml.XmlReader.ReadState%2A> 屬性會設為 <xref:System.Xml.ReadState.EndOfFile>。  
  
 建立或移動 <xref:System.Xml.XPath.XPathNavigator> 物件，並不會變更 <xref:System.Xml.XmlReader> 物件的位置。 僅當定位在項目或根節點上時，<xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> 方法才有效。  
  
 下列範例顯示如何取得包含 <xref:System.Xml.XmlReader> 物件中整個 XML 文件與單一節點及其子節點的 <xref:System.Xml.XPath.XPathDocument> 物件。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlReader.  
Dim xml As XmlReader = navigator.ReadSubtree()  
  
While xml.Read()  
    Console.WriteLine(xml.ReadInnerXml())  
End While  
  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlReader = navigator.ReadSubtree()  
  
While book.Read()  
    Console.WriteLine(book.ReadInnerXml())  
End While  
  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlReader.  
XmlReader xml = navigator.ReadSubtree();  
  
while (xml.Read())  
{  
    Console.WriteLine(xml.ReadInnerXml());  
}  
  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlReader book = navigator.ReadSubtree();  
  
while (book.Read())  
{  
    Console.WriteLine(book.ReadInnerXml());  
}  
  
book.Close();  
```  
  
 該範例採用 `books.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>將 XPathNavigator 轉換為 XmlWriter  
 使用 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> 方法，將 XML 文件或僅單一節點及其子節點的全部內容，以資料流方式傳送至 <xref:System.Xml.XmlWriter> 物件。  
  
 建立 <xref:System.Xml.XPath.XPathNavigator> 物件，並不會變更 <xref:System.Xml.XmlWriter> 物件的位置。  
  
 下列範例顯示如何取得包含 <xref:System.Xml.XmlWriter> 物件中整個 XML 文件與單一節點及其子節點的 <xref:System.Xml.XPath.XPathDocument> 物件。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlWriter.  
Dim xml As XmlWriter = XmlWriter.Create("newbooks.xml")  
navigator.WriteSubtree(xml)  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlWriter = XmlWriter.Create("book.xml")  
navigator.WriteSubtree(book)  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlWriter.  
XmlWriter xml = XmlWriter.Create("newbooks.xml");  
navigator.WriteSubtree(xml);  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlWriter book = XmlWriter.Create("book.xml");  
navigator.WriteSubtree(book);  
book.Close();  
```  
  
 範例將在本主題的前面部分所找到的 `books.xml` 檔案當做輸入。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [使用 XPathNavigator 導覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
- [使用 XPathNavigator 導覽屬性和命名空間節點](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [使用 XPathNavigator 存取強型別 XML 資料](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
