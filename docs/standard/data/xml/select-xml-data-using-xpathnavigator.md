---
title: 使用 XPathNavigator 選取 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a7aebc98627a079d08870b59e4a848a51dbfaaf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520109"
---
# <a name="select-xml-data-using-xpathnavigator"></a>使用 XPathNavigator 選取 XML 資料
<xref:System.Xml.XPath.XPathNavigator> 類別提供一組方法，可以使用 XPath 運算式選取 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的一組節點。 一旦選取，即可重複處理已選取的節點集。  
  
## <a name="xpathnavigator-selection-methods"></a>XPathNavigator 選取方法  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供一組方法，可以使用 XPath 運算式選取 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的一組節點。 <xref:System.Xml.XPath.XPathNavigator> 類別也提供了一組最佳化方法，可以選取上階節點、子節點及子代節點，其速度比使用 XPath 運算式快。 若為選取的單一節點，會在 <xref:System.Xml.XPath.XPathNodeIterator> 物件或 <xref:System.Xml.XPath.XPathNavigator> 物件中傳回已選取的節點集。  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>使用 XPath 運算式選取節點  
 若要使用 XPath 運算式來選取一組節點，請使用下列其中一種選取方法。  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 呼叫時，這些方法會傳回一組節點，您可以使用 <xref:System.Xml.XPath.XPathNodeIterator> 物件或 <xref:System.Xml.XPath.XPathNavigator> 物件 (若為選取的單一節點) 來隨意巡覽這些節點。  
  
 使用 <xref:System.Xml.XPath.XPathNodeIterator> 物件來巡覽不會影響用於建立它之 <xref:System.Xml.XPath.XPathNavigator> 物件的位置。 從 <xref:System.Xml.XPath.XPathNavigator> 方法傳回的 <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 物件會置於傳回的單一節點上，而且也不會影響用來建立它之 <xref:System.Xml.XPath.XPathNavigator> 物件的位置。  
  
 下列範例顯示如何從 <xref:System.Xml.XPath.XPathNavigator> 物件建立 <xref:System.Xml.XPath.XPathDocument> 物件、如何使用 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法來選取 <xref:System.Xml.XPath.XPathDocument> 物件中的節點，以及如何使用 <xref:System.Xml.XPath.XPathNodeIterator> 物件來重複處理已選取的節點。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 該範例採用 `books.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>最佳化選取方法  
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 方法表示一般用來擷取子節點、子代節點及上階節點的 XPath 運算式。 這些方法已針對效能最佳化，而且速度比其相對應的 XPath 運算式快。 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> 方法會依據 <xref:System.Xml.XPath.XPathNodeType> 值或要選取之節點的區域名稱及命名空間 URI，來選取上階節點、子節點及子代節點。 選取的上階節點、子節點及子代節點會在 <xref:System.Xml.XPath.XPathNodeIterator> 物件中傳回。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [使用 XPathNavigator 評估 XPath 運算式](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [使用 XPathNavigator 比對節點](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [使用 XPath 查詢辨識的節點類型](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [XPath 查詢和命名空間](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [編譯 XPath 運算式](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
