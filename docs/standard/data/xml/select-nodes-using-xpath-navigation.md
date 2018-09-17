---
title: 使用 XPath 巡覽選取節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e02dd304893e4d9354144c5b412dfd145161c6e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45596945"
---
# <a name="select-nodes-using-xpath-navigation"></a>使用 XPath 巡覽選取節點
XML 文件物件模型 (DOM) 包含可讓您在 DOM 中使用 XML 路徑語言 (XPath) 巡覽查詢資訊的方法。 您可以使用 XPath 尋找單一特定節點，或是尋找符合某些準則的所有節點。  
  
## <a name="xpath-select-methods"></a>XPath 選取方法  
 DOM 類別提供了兩種使用 XPath 選取的方法：<xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法與 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法。 <xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法會傳回符合選取準則的第一個節點。 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法則會傳回包含相符節點的 <xref:System.Xml.XmlNodeList> 方法。  
  
 下列範例使用 <xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法選取第一個 `book` 節點，其中作者的姓氏符合指定的準則。 bookstore.xml 檔案 (提供於本主題結尾) 會做為輸入檔案。  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 下一個範例使用 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法來選取所有的書籍節點，其中價格大於指定的數量。 在選取清單中的每本書籍價格都會以程式設計的方式減少百分之十。 最後，會將更新的檔案寫入主控台中。 bookstore.xml 檔案 (提供於本主題結尾) 會做為輸入檔案。  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 上述範例會從文件項目開始 XPath 查詢。 設定 XPath 查詢的起點時，便會設定做為 XPath 查詢起點的內容節點。 如果您不想從文件項目開始，而要從文件項目的第一個項目子系開始，則可以撰寫下列所示的 Select 陳述式程式碼。  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 讓所有 <xref:System.Xml.XmlNodeList> 物件與基礎文件同步處理。 因此，如果您重複節點清單並修改節點的值，則也會從節點的來源文件中更新該節點。 請注意，在前述範例中，當在選取的 <xref:System.Xml.XmlNodeList> 中修改節點時，也會修改基礎文件。  
  
> [!NOTE]
>  修改基礎文件後，建議您重新執行 select。 如果修改節點後，導致該節點被加入至節點清單 (先前未加入)，或導致該節點從節點清單中移除，則不能保證此節點清單目前是正確的。  
  
## <a name="namespaces-in-xpath-expressions"></a>XPath 運算式中的命名空間  
 XPath 運算式可包含命名空間。 命名空間解析可透過 <xref:System.Xml.XmlNamespaceManager> 予以支援。 如果 XPath 運算式包含前置詞，則必須將前置詞及命名空間 URI 配對加入至 <xref:System.Xml.XmlNamespaceManager>，並將 <xref:System.Xml.XmlNamespaceManager> 傳遞給 <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> 或 <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> 方法。 請注意上方的程式碼範例使用 <xref:System.Xml.XmlNamespaceManager> 來解析 bookstore.xml 文件的命名空間。  
  
> [!NOTE]
>  如果 XPath 運算式不包含前置詞，則會假設命名空間統一資源識別元 (URI) 為空白的命名空間。 如果 XML 包含預設命名空間，則仍必須將前置詞及命名空間 URI 加入至 <xref:System.Xml.XmlNamespaceManager>，否則就不會選取任何節點。  
  
#### <a name="input-file"></a>輸入檔案  
 下列是在本主題的範例中做為輸入檔案的 bookstore.xml 檔案：  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
