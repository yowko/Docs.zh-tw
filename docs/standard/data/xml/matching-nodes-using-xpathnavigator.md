---
title: "使用 XPathNavigator 比對節點 | Microsoft Docs"
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
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# 使用 XPathNavigator 比對節點
<xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法來判斷節點是否符合 XPath 運算式。  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法採用 XPath 運算式做為輸入並傳回<xref:System.Boolean>，其指出目前節點是否符合指定的 XPath 運算式或指定之編譯的 <xref:System.Xml.XPath.XPathExpression> 物件。  
  
## 比對節點  
 如果目前節點符合指定的 XPath 運算式，則 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法會傳回 `true`。  例如，在下面的程式碼範例中，如果目前節點是項目 `b`，且項目 `b` 具有屬性 `c`，則 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法將傳回 `true`。  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法不會變更 <xref:System.Xml.XPath.XPathNavigator> 的狀態。  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## 請參閱  
 <xref:System.Xml.XmlDocument>   
 <xref:System.Xml.XPath.XPathDocument>   
 <xref:System.Xml.XPath.XPathNavigator>   
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)   
 [使用 XPathNavigator 選取 XML 資料](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)   
 [使用 XPathNavigator 評估 XPath 運算式](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)   
 [在 XPath 查詢中辨識的節點型別](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)   
 [XPath 查詢及命名空間](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)   
 [編譯 XPath 運算式](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)