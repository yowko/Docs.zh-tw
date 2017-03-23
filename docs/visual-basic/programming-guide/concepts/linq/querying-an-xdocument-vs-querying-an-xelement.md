---
title: "查詢 XDocument 與查詢 xelement 的比較 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 29044cd118bfd8ecc12bddca722ee3656d455e0f
ms.lasthandoff: 03/13/2017


---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>查詢 XDocument 與查詢 xelement 的比較 (Visual Basic)
當您載入文件<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>，您會注意到，您必須撰寫查詢稍有不同於載入透過<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>時</xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>透過  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument.Load 和 XElement.Load 之比較  
 當您載入到 XML 文件<xref:System.Xml.Linq.XElement>透過<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XElement>根目錄中的 XML 樹狀結構會包含已載入文件的根項目。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement> 不過，當您載入相同的 XML 文件<xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>樹狀結構的根<xref:System.Xml.Linq.XDocument>節點，然後載入文件的根項目是一個允許的子<xref:System.Xml.Linq.XElement>節點的<xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> ，</xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>透過</xref:System.Xml.Linq.XDocument> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 座標軸會相對於根節點進行運算。  
  
 這個第一個範例會載入使用<xref:System.Xml.Linq.XElement.Load%2A>.</xref:System.Xml.Linq.XElement.Load%2A> XML 樹狀結構 接著，它會針對樹狀結構根目錄的子項目進行查詢。  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 這個範例預期會產生下列輸出：  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 下列範例是上述，使用例外狀況的 XML 樹狀結構載入<xref:System.Xml.Linq.XDocument>而不是<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>相同  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 請注意，相同的查詢會傳回一個 `Root` 節點，而非三個子節點。  
  
 其中一種處理方式是使用<xref:System.Xml.Linq.XDocument.Root%2A>屬性，才能存取座標軸方法，如下︰</xref:System.Xml.Linq.XDocument.Root%2A>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 這個查詢會執行在同一個查詢樹狀結構的方式起源於<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> 這個範例會產生下列輸出：  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>另請參閱  
 [基本查詢 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
