---
title: "使用 XPathNavigator 評估 XPath 運算式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d513f48155a582a5158cccdd682f5b8485caefd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>使用 XPathNavigator 評估 XPath 運算式
<xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法，以評估 XPath 運算式。 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法會使用 XPath 運算式，評估它並根據 XPath 運算式的結果傳回 W3C XPath 型別：Boolean、Number、String 或 Node Set。  
  
## <a name="the-evaluate-method"></a>評估方法  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法會使用 XPath 運算式，評估它並傳回具型別的結果：Boolean (<xref:System.Boolean>)、Number (<xref:System.Double>)、String (<xref:System.String>) 或 Node Set (<xref:System.Xml.XPath.XPathNodeIterator>)。 例如，<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法可用於數學方法。 下列範例程式碼會計算 `books.xml` 檔案中所有書籍的總價。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 該範例採用 `books.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>position 及 last 函式  
 會多載 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法。 其中一個 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法會採用 <xref:System.Xml.XPath.XPathNodeIterator> 物件做為參數。 此特定 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法與僅將 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 物件做為參數的 <xref:System.Xml.XPath.XPathExpression> 方法相同，只是它允許節點集引數來指定要執行評估的目前內容。 此內容對於 XPath `position()` 及 `last()` 函式是必要的，因為它們相對於目前的內容節點。 除非是用做位置步驟中的述詞，否則 `position()` 及 `last()` 函式需要節點集的參考以進行評估，否則 `position` 及 `last` 函式會傳回 `0`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [使用 XPathNavigator 選取 XML 資料](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [使用 XPathNavigator 比對節點](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath 查詢中辨識的節點型別](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [XPath 查詢及命名空間](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [編譯的 XPath 運算式](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
