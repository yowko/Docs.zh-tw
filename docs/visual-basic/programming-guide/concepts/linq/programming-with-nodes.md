---
title: 使用節點 (Visual Basic) 進行程式設計
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 871755ef0293513f07c60b1d5735c47692163b78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="programming-with-nodes-visual-basic"></a>使用節點 (Visual Basic) 進行程式設計
必須撰寫程式 (例如，XML 編輯器、轉換系統或報表寫入器) 的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 開發人員通常需要撰寫的程式可在比項目和屬性更細微的層級上作業。 他們通常需要在節點層級、管理的文字節點、處理指示與註解上作業。 這個主題提供一些關於在節點層級進行程式設計的詳細資料。  
  
## <a name="node-details"></a>節點詳細資料  
 這裡提供程式設計人員在節點層級上作業時應該知道的一些程式設計詳細資料。  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>XDocument 之子節點的父屬性設定為 Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> 屬性包含父代 <xref:System.Xml.Linq.XElement>，而不包含父節點。 <xref:System.Xml.Linq.XDocument> 的子節點沒有父代 <xref:System.Xml.Linq.XElement>。 其父代為文件，因此，這些節點的 <xref:System.Xml.Linq.XObject.Parent%2A> 屬性設定為 Null。  
  
 下列範例為其示範：  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 這個範例會產生下列輸出：  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>文字節點可以是相鄰的  
 在多個 XML 程式撰寫模型 (Programming Model) 中，相鄰的文字節點永遠會遭到合併。 這有時候稱為文字節點的正規化。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 不會正規化文字節點。 如果您將兩個文字節點加入到相同的項目，則會讓兩個文字節點變成相鄰的。 不過，如果您新增指定為字串 (而非 <xref:System.Xml.Linq.XText> 節點) 的內容，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 可能會合併字串與相鄰的文字節點。  
  
 下列範例為其示範：  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 這個範例會產生下列輸出：  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>文字節點可以是空白的  
 在某些 XML 程式撰寫模型中，保證文字節點不包含空字串。 原因是，這種文字節點對於序列化 XML 不會有任何影響。 不過，因為相同的原因，文字節點可以是相鄰的，如果您藉由將文字節點的值設定為空字串來移除該文字節點中的文字，文字節點本身將不會遭到刪除。  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 這個範例會產生下列輸出：  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>空文字節點影響序列化  
 如果項目僅包含一個空的文字子節點，該項目會以長標記語法序列化：`<Child></Child>`。 如果項目不包含任何子節點，則該項目會以短標記語法序列化：`<Child />`。  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>命名空間為 LINQ to XML 樹狀結構中的屬性  
 即使命名空間宣告與屬性具有相同的語法，在某些程式設計介面 (例如，XSLT 和 XPath) 中，命名空間宣告不會被視為屬性。 不過，在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，命名空間會當做 <xref:System.Xml.Linq.XAttribute> 物件，儲存在 XML 樹狀結構中。 如果您逐一查看包含命名空間宣告之項目的屬性，您將可以看到命名空間宣告，做為所傳回之集合中的其中一個項目。  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> 屬性會指出屬性是否為命名空間宣告。  
  
```vb  
Dim root As XElement = _   
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>XPath 座標軸方法不會傳回 XDocument 的子系空白字元  
 只要文字節點只包含空白字元，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 就允許使用 <xref:System.Xml.Linq.XDocument> 的文字子節點。 不過，XPath 物件模型不包含當做文件子節點的空白字元，因此，當您使用 <xref:System.Xml.Linq.XDocument> 座標軸逐一查看 <xref:System.Xml.Linq.XContainer.Nodes%2A> 的子系時，將不會傳回空白字元文字節點。 但是，當您使用 XPath 座標軸方法逐一查看 <xref:System.Xml.Linq.XDocument> 的子系時，將不會傳回空白字元文字節點。  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 這個範例會產生下列輸出：  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration 物件不是節點  
 當您逐一查看 <xref:System.Xml.Linq.XDocument> 的子節點時，您將不會看到 XML 宣告物件。 這是文件的屬性，而不是其子節點。  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>另請參閱  
 [進階的 LINQ to XML 程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
