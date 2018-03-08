---
title: "編譯 XPath 運算式"
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
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e6ff5661a7e78f9b37f16acc86834561fc697bcc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="compiled-xpath-expressions"></a>編譯 XPath 運算式
<xref:System.Xml.XPath.XPathExpression> 物件表示從 <xref:System.Xml.XPath.XPathExpression.Compile%2A> 類別的靜態 <xref:System.Xml.XPath.XPathExpression> 方法或 <xref:System.Xml.XPath.XPathNavigator.Compile%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 方法傳回的編譯 XPath 查詢。  
  
## <a name="the-xpathexpression-class"></a>XPathExpression 類別  
 如果會多次使用同一 XPath 查詢，則 <xref:System.Xml.XPath.XPathExpression> 物件所表示的編譯 XPath 查詢會很有用。  
  
 例如，多次呼叫 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法，而不是每次都使用表示 XPath 查詢的字串時，請使用 <xref:System.Xml.XPath.XPathExpression.Compile%2A> 類別的 <xref:System.Xml.XPath.XPathExpression> 方法或 <xref:System.Xml.XPath.XPathNavigator.Compile%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 方法，來編譯並快取 <xref:System.Xml.XPath.XPathExpression> 物件中的 XPath 查詢，以重複使用並提升效能。  
  
 編譯後，根據從 XPath 查詢傳回的型別，可能會使用 <xref:System.Xml.XPath.XPathExpression> 物件做為下列 <xref:System.Xml.XPath.XPathNavigator> 類別方法的輸入。  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 下表說明每個 W3C XPath 傳回型別、其 Microsoft .NET Framework 對等型別，以及與 <xref:System.Xml.XPath.XPathExpression> 物件搭配使用的方法 (根據其傳回型別)。  
  
|W3C XPath 傳回型別|.NET Framework 對等型別|描述|方法|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|依文件順序建立之不重複節點的未排序集合。|<xref:System.Xml.XPath.XPathNavigator.Select%2A> 或 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|`true` 或 `false` 值。|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 或者<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|浮點數。|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|UCS 字元的順序。|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法會接受 XPath 運算式做為它的參數。 <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 方法會傳回 <xref:System.Xml.XPath.XPathNavigator> 物件，而不是其中一個 W3C XPath 傳回型別。  
  
### <a name="the-returntype-property"></a>ReturnType 屬性  
 將 XPath 查詢編譯到 <xref:System.Xml.XPath.XPathExpression> 物件中之後，您可使用 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 物件的 <xref:System.Xml.XPath.XPathExpression> 屬性來判斷 XPath 查詢傳回的型別。  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 屬性會傳回下列其中一個表示 W3C XPath 傳回型別的 <xref:System.Xml.XPath.XPathResultType> 列舉值。  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 下列範例會使用 <xref:System.Xml.XPath.XPathExpression> 物件，從 `books.xml` 檔案傳回號碼及節點集。 將每個 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 物件的 <xref:System.Xml.XPath.XPathExpression> 屬性及 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 與 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法的結果寫入主控台。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 該範例採用 `books.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>較高效能的 XPath 運算式  
 為了達到較高的效能，請在查詢中使用可能最適合的 XPath 運算式。 例如，如果 `book` 節點是 `bookstore` 節點的子節點，且 `bookstore` 節點是 XML 文件中的最上層項目，則使用 XPath 運算式 `/bookstore/book` 會比使用 `//book` 更快速。 `//book` XPath 運算式將掃描 XML 樹狀目錄中的每個節點，以識別符合的節點。  
  
 此外，在選取準則很簡單的情況下，使用 <xref:System.Xml.XPath.XPathNavigator> 類別提供之節點集巡覽方法的效能，可能會比 <xref:System.Xml.XPath.XPathNavigator> 類別提供之選取方法的效能高。 例如，如果需要選取目前節點的第一個子節點，則使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> 方法會比使用 `child::*[1]` XPath 運算式及 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法更快速。  
  
 如需 <xref:System.Xml.XPath.XPathNavigator> 類別之節點集巡覽方法的詳細資訊，請參閱[使用 XPathNavigator 巡覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [使用 XPathNavigator 選取 XML 資料](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [使用 XPathNavigator 評估 XPath 運算式](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [使用 XPathNavigator 比對節點](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [使用 XPath 查詢辨識的節點類型](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [XPath 查詢和命名空間](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
