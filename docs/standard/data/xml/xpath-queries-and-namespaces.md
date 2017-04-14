---
title: "XPath 查詢及命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# XPath 查詢及命名空間
XPath 查詢可辨識 XML文件中的命名空間，並可使用命名空間前置詞來限定項目及屬性名稱。  使用命名空間前置詞限定項目及屬性名稱，會將 XPath 查詢傳回的節點限制為那些只屬於特定命名空間的節點。  
  
 例如，如果前置詞 `books` 對應命名空間 `http://www.contoso.com/books`，則下列 XPath 查詢 `/books:books/books:book` 只會選取命名空間 `http://www.contoso.com/books` 中的那些 `book` 項目。  
  
## XmlNamespaceManager  
 若要在 XPath 查詢中使用命名空間，需使用要包含在該 XPath 查詢中的命名空間 URI 及前置詞，建構自 <xref:System.Xml.IXmlNamespaceResolver> 介面衍生的物件，如 <xref:System.Xml.XmlNamespaceManager> 類別。  
  
 可以透過下列每一種方式將 <xref:System.Xml.XmlNamespaceManager> 物件用於查詢中。  
  
-   可藉由使用 <xref:System.Xml.XPath.XPathExpression> 物件的 <xref:System.Xml.XPath.XPathExpression.SetContext%2A> 方法，使 <xref:System.Xml.XmlNamespaceManager> 物件與現有 <xref:System.Xml.XPath.XPathExpression> 物件產生關聯。  您也可使用靜態 <xref:System.Xml.XPath.XPathExpression.Compile%2A> 方法編譯新的 <xref:System.Xml.XPath.XPathExpression> 物件；該方法會採用表示 XPath 運算式的字串及 <xref:System.Xml.XmlNamespaceManager> 物件做為參數，並傳回新的 <xref:System.Xml.XPath.XPathExpression> 物件。  
  
-   <xref:System.Xml.XmlNamespaceManager> 物件本身會做為參數，連同表示 XPath 運算式的字串一起傳遞至接受的 <xref:System.Xml.XPath.XPathNavigator> 類別方法。  
  
 下列是 <xref:System.Xml.XPath.XPathNavigator> 類別的方法，其接受衍生自 <xref:System.Xml.IXmlNamespaceResolver> 介面的物件做為參數。  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### 預設命名空間  
 在下面的 XML 文件中，會使用具有空前置詞的預設命名空間來宣告 `http://www.contoso.com/books` 命名空間。  
  
```  
<books xmlns="http://www.example.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 XPath 將空前置詞視為 `null` 命名空間。  換句話說，只有對應至命名空間的前置詞可用於 XPath 查詢。  這表示如果您要根據 XML 文件中的命名空間查詢，則即使它是預設命名空間，您也需要定義它的前置詞。  
  
 例如，如果不定義上述 XML 文件的前置詞，XPath 查詢 `/books/book` 就不會傳回任何結果。  
  
 如果在有些節點不在命名空間中，有些節點在預設命名空間中的狀況下查詢文件，則必須繫結前置詞以避免模糊不清的情況。  
  
 下列程式碼定義預設命名空間的前置詞，並從 `http://www.contoso.com/books` 命名空間選取所有的 `book` 項目。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## 請參閱  
 <xref:System.Xml.XmlDocument>   
 <xref:System.Xml.XPath.XPathDocument>   
 <xref:System.Xml.XPath.XPathNavigator>   
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)   
 [使用 XPathNavigator 選取 XML 資料](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)   
 [使用 XPathNavigator 評估 XPath 運算式](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)   
 [使用 XPathNavigator 比對節點](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)   
 [在 XPath 查詢中辨識的節點型別](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)   
 [編譯 XPath 運算式](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)