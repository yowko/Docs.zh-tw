---
title: 如何： 擷取項目 (LINQ to XML) 的值 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: ff2a1712a79bdedd74fe51391f01dd900ae585e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>如何： 擷取項目 (LINQ to XML) 的值 (Visual Basic)
本主題顯示如何取得項目的值。 以下有兩種主要的方式可達成此目標。 其中一種方式為，將 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別。 然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別，並將其指派給您的變數。 或者，您可以使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性或 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> 屬性。  
  
 使用 Visual Basic 時，最好的方法是使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性。  
  
## <a name="example"></a>範例  
 若要擷取項目的值，您只要將 <xref:System.Xml.Linq.XElement> 物件轉型為所需的型別即可。 您永遠可以將項目轉型為字串，如下所示：  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>範例  
 您也可以將項目轉型為非字串的型別。 例如，如果您有包含整數的項目，您可以將其轉型為 `int`，如下列程式碼所示：  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會針對下列資料類型提供明確轉換運算子：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會提供 <xref:System.Xml.Linq.XAttribute> 物件相同的轉換運算子。  
  
## <a name="example"></a>範例  
 您可以使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來擷取項目的內容：  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>範例  
 即使您不確定項目是否存在，您有時候還是會嘗試擷取項目的值。 在這個情況下，當您將轉換的項目指派給可為 Null 的型別 (`string` 或 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中其中一個可為 Null 的型別) 時，如果項目不存在，被指派的變數只會設定為 `Nothing`。 下列程式碼顯示，項目可能存在或可能不存在時，使用轉型比使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性更為容易。  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 此程式碼會產生下列輸出：  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 一般而言，使用轉換擷取元素及屬性內容時，您可以撰寫較簡易的程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
