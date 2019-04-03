---
title: HOW TO：列出樹狀結構 (Visual Basic) 中的所有節點
ms.date: 07/20/2015
ms.assetid: e19289c4-26d1-435b-b0db-fb8bc856b753
ms.openlocfilehash: 6576beaaed00905ce7a09f338251934ea375cb7e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824841"
---
# <a name="how-to-list-all-nodes-in-a-tree-visual-basic"></a>HOW TO：列出樹狀結構 (Visual Basic) 中的所有節點
列出樹狀中的所有節點有時候很有幫助。 這在精確了解方法或屬性如何影響樹狀結構時相當實用。 以文字格式列出所有節點的其中一個方法為產生正確而且明確識別樹狀結構中任何節點的 XPath 運算式。  
  
 若是使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 執行 XPath 運算式，則不會特別有幫助。 XPath 運算式的效能比 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的效能差，而且 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的功能更為強大。 不過，若是要識別 XML 樹狀中的節點，XPath 就非常適合。  
  
## <a name="example"></a>範例  
 這個範例顯示名稱為 `GetXPath` 的函式，可針對 XML 樹狀結構中的任何節點，產生特定的 XPath 運算式。 即使節點位於命名空間中，它也可以產生適當的 XPath 運算式。 XPath 運算式是利用命名空間前置詞產生。  
  
 接著，此範例會建立包含數種節點類型之範例的小型 XML 樹狀結構。 它會逐一查看下階節點，並列印每個節點的 XPath 運算式。  
  
 您會注意到，XML 宣告不是樹狀結構中的節點。  
  
 下列為包含數種節點類型的 XML 檔案：  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<?target data?>  
<Root AttName="An Attribute" xmlns:aw="http://www.adventure-works.com">  
  <!--This is a comment-->  
  <Child>Text</Child>  
  <Child>Other Text</Child>  
  <ChildWithMixedContent>text<b>BoldText</b>otherText</ChildWithMixedContent>  
  <aw:ElementInNamespace>  
    <aw:ChildInNamespace />  
  </aw:ElementInNamespace>  
</Root>  
```  
  
 下列為上述 XML 樹狀結構中的節點清單，以 XPath 運算式表示：  
  
```  
/processing-instruction()  
/Root  
/Root/@AttName  
/Root/@xmlns:aw  
/Root/comment()  
/Root/Child[1]  
/Root/Child[1]/text()  
/Root/Child[2]  
/Root/Child[2]/text()  
/Root/ChildWithMixedContent  
/Root/ChildWithMixedContent/text()[1]  
/Root/ChildWithMixedContent/b  
/Root/ChildWithMixedContent/b/text()  
/Root/ChildWithMixedContent/text()[2]  
/Root/aw:ElementInNamespace  
/Root/aw:ElementInNamespace/aw:ChildInNamespace  
```  
  
```vb  
Module Module1  
<System.Runtime.CompilerServices.Extension()> _  
    Private Function StrCat(Of T)(ByVal source As IEnumerable(Of T), _  
                                  ByVal separator As String) As String  
        Return _  
        source.Aggregate(New StringBuilder(), _  
            Function(sb, i) sb _  
                .Append(i.ToString()) _  
                .Append(separator), _  
                Function(s) s.ToString())  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function GetXPath(ByVal xobj As XObject) As String  
        Dim retStr As String  
        If xobj.Parent Is Nothing Then  
            Dim doc As XDocument = TryCast(xobj, XDocument)  
            If doc IsNot Nothing Then  
                Return "."  
            End If  
            Dim el As XElement = TryCast(xobj, XElement)  
            If el IsNot Nothing Then  
                Return ("/" & NameWithPredicate(el))  
            End If  
  
            ' The XPath data model does not include white space text nodes  
            ' that are children of a document, so this method returns null.  
            Dim xt As XText = TryCast(xobj, XText)  
            If xt IsNot Nothing Then  
                Return Nothing  
            End If  
            Dim com As XComment = TryCast(xobj, XComment)  
            If com IsNot Nothing Then  
                If com.Document().Nodes().OfType(Of XComment)().Count() <> 1 Then  
                    Return "/comment()[" & (com.NodesBeforeSelf().OfType _  
                        (Of XComment)().Count() + 1) & "]"  
                Else  
                    Return "/comment()"  
                End If  
            End If  
  
            Dim pi As XProcessingInstruction = TryCast(xobj, XProcessingInstruction)  
            If pi IsNot Nothing Then  
                If pi.Document.Nodes().OfType(Of XProcessingInstruction)(). _  
                        Count() <> 1 Then  
                    Return "/processing-instruction()[" & _  
                        (pi.NodesBeforeSelf().OfType(Of XProcessingInstruction)() _  
                        .Count() + 1) & "]"  
                Else  
                    Return "/processing-instruction()"  
                End If  
            End If  
        Else  
            Dim el As XElement = TryCast(xobj, XElement)  
            If el IsNot Nothing Then  
                Return "/" & el.Ancestors().InDocumentOrder(). _  
                    Select(Function(e) NameWithPredicate(e)) _  
                    .StrCat("/") & NameWithPredicate(el)  
            End If  
  
            Dim at As XAttribute = TryCast(xobj, XAttribute)  
            If at IsNot Nothing Then  
                Return "/" & at.Parent().AncestorsAndSelf().InDocumentOrder(). _  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") & _  
                    "@" & GetQName(at)  
            End If  
  
            Dim com As XComment = TryCast(xobj, XComment)  
            If com IsNot Nothing Then  
                retStr = "/" & com.Parent.AncestorsAndSelf().InDocumentOrder(). _  
                Select(Function(e) NameWithPredicate(e)).StrCat("/") & "comment()"  
                If com.Parent().Nodes().OfType(Of XComment)().Count() <> 1 Then  
                    retStr &= "[" & (com.NodesBeforeSelf().OfType(Of XComment)().Count() + 1) & "]"  
                End If  
                Return retStr  
            End If  
  
            Dim cd As XCData = TryCast(xobj, XCData)  
            If cd IsNot Nothing Then  
                retStr = "/" & cd.Parent.AncestorsAndSelf().InDocumentOrder(). _  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") & "text()"  
                If cd.Parent.Nodes().OfType(Of XText)().Count() <> 1 Then  
                    retStr &= "[" & (cd.NodesBeforeSelf().OfType(Of XText)(). _  
                        Count() + 1) & "]"  
                End If  
                Return retStr  
            End If  
  
            Dim tx As XText = TryCast(xobj, XText)  
            If tx IsNot Nothing Then  
                retStr = "/" & tx.Parent.AncestorsAndSelf().InDocumentOrder(). _  
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") & "text()"  
                If tx.Parent.Nodes().OfType(Of XText)().Count() <> 1 Then  
                    retStr &= "[" & (tx.NodesBeforeSelf().OfType(Of XText)(). _  
                        Count() + 1) & "]"  
                End If  
                Return retStr  
            End If  
  
            Dim pi As XProcessingInstruction = TryCast(xobj, XProcessingInstruction)  
            If pi IsNot Nothing Then  
                retStr = "/" & pi.Parent.AncestorsAndSelf().InDocumentOrder(). _  
                    Select(Function(e) NameWithPredicate(e)). _  
                    StrCat("/") & "processing-instruction()"  
                If pi.Parent.Nodes().OfType(Of XProcessingInstruction)().Count() <> 1 Then  
                    retStr &= "[" & (pi.NodesBeforeSelf().OfType(Of XProcessingInstruction)(). _  
                        Count() + 1) & "]"  
                End If  
            End If  
        End If  
        Return Nothing  
    End Function  
  
    Private Function GetQName(ByVal xe As XElement) As String  
        Dim prefix As String = xe.GetPrefixOfNamespace(xe.Name.Namespace)  
        If xe.Name.Namespace = XNamespace.None Or prefix Is Nothing Then  
            Return xe.Name.LocalName.ToString()  
        Else  
            Return prefix + ":" & xe.Name.LocalName.ToString()  
        End If  
    End Function  
  
    Private Function GetQName(ByVal xa As XAttribute) As String  
        Dim prefix As String = _  
            xa.Parent.GetPrefixOfNamespace(xa.Name.Namespace)  
        If xa.Name.Namespace = XNamespace.None Or prefix Is Nothing Then  
            Return xa.Name.ToString()  
        Else  
            Return prefix + ":" & xa.Name.LocalName  
        End If  
    End Function  
  
    Public Function NameWithPredicate(ByVal el As XElement) As String  
        If el.Parent IsNot Nothing AndAlso el.Parent.Elements(el.Name).Count() <> 1 Then  
            Return GetQName(el) + "[" & _  
                (el.ElementsBeforeSelf(el.Name).Count() + 1) & "]"  
        Else  
            Return GetQName(el)  
        End If  
    End Function  
  
    Sub Main()  
        Dim aw As XNamespace = "http://www.adventure-works.com"  
        Dim doc As XDocument = _  
            <?xml version='1.0' encoding="utf-8" standalone='yes'?>  
            <?target data?>  
            <Root AttName='An Attribute' xmlns:aw='http://www.adventure-works.com'>  
                <!--This is a comment-->  
                <Child>Text</Child>  
                <Child>Other Text</Child>  
                <ChildWithMixedContent>text<b>BoldText</b>otherText</ChildWithMixedContent>  
                <aw:ElementInNamespace>  
                    <aw:ChildInNamespace/>  
                </aw:ElementInNamespace>  
            </Root>  
        doc.Save("Test.xml")  
        Console.WriteLine(File.ReadAllText("Test.xml"))  
        Console.WriteLine("------")  
        For Each obj As XObject In doc.DescendantNodes()  
            Console.WriteLine(obj.GetXPath())  
            Dim el As XElement = TryCast(obj, XElement)  
            If el IsNot Nothing Then  
                For Each at As XAttribute In el.Attributes()  
                    Console.WriteLine(at.GetXPath())  
                Next  
            End If  
        Next  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<?target data?>  
<Root AttName="An Attribute" xmlns:aw="http://www.adventure-works.com">  
  <!--This is a comment-->  
  <Child>Text</Child>  
  <Child>Other Text</Child>  
  <ChildWithMixedContent>text<b>BoldText</b>otherText</ChildWithMixedContent>  
  <aw:ElementInNamespace>  
    <aw:ChildInNamespace />  
  </aw:ElementInNamespace>  
</Root>  
------  
/processing-instruction()  
/Root  
/Root/@AttName  
/Root/@xmlns:aw  
/Root/comment()  
/Root/Child[1]  
/Root/Child[1]/text()  
/Root/Child[2]  
/Root/Child[2]/text()  
/Root/ChildWithMixedContent  
/Root/ChildWithMixedContent/text()[1]  
/Root/ChildWithMixedContent/b  
/Root/ChildWithMixedContent/b/text()  
/Root/ChildWithMixedContent/text()[2]  
/Root/aw:ElementInNamespace  
/Root/aw:ElementInNamespace/aw:ChildInNamespace  
```  
  
## <a name="see-also"></a>另請參閱

- [進階查詢技術 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
