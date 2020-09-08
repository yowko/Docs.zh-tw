---
title: 如何取出元素的值-LINQ to XML
description: 瞭解取得元素或屬性值的兩個主要方式：轉換成所需的型別，或使用 System.xml.linq.xelement> 和 System.xml.linq.xattribute> 屬性。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 010af5db9ec991bfe0345c93def3241150aa15e2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552697"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml"></a>如何擷取元素值 (LINQ to XML)

本文說明如何取得元素的值。 有兩種主要的方法可以取得此值：

- 將 <xref:System.Xml.Linq.XElement> 或轉換 <xref:System.Xml.Linq.XAttribute> 成所需的型別。 然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別，並將其指派給您的變數。

- 使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> 屬性。 您也可以使用這些屬性來設定值。

使用 c # 時，轉換通常是比較好的方法。 如果您將專案或屬性轉型為可為 null 的實值型別，則在抓取專案的值 (或可能不存在的屬性) 時，會比較容易撰寫程式碼。 本文的最後一個範例將示範這項功能。 不過，您無法透過轉換來設定專案的內容，就像您可以透過屬性來設定一樣 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 。

使用 Visual Basic，更好的方法是使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性。

## <a name="string-cast-example"></a>字串轉換範例  

若要取出專案的值，請將 <xref:System.Xml.Linq.XElement> 物件轉換成您想要的類型。 您可以將元素轉換成字串，如下所示：

```csharp
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + (string)e);
```

```vb
Dim e As XElement = <StringElement>abcde</StringElement>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & e.Value)
```

這個範例會產生下列輸出：

```output
<StringElement>abcde</StringElement>
Value of e:abcde
```

## <a name="integer-cast-example"></a>整數轉換範例  

您也可以將項目轉型為非字串的型別。 例如，如果您有包含整數的項目，您可以將其轉型為 `int`，如下列程式碼所示：  

```csharp
XElement e = new XElement("Age", "44");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + (int)e);
```

```vb
Dim e As XElement = <Age>44</Age>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & CInt(e))
```

這個範例會產生下列輸出：

```output
<Age>44</Age>
Value of e:44
```

LINQ to XML 為下列資料類型提供明確的轉換運算子： `string` 、 `bool` 、 `bool?` 、 `int` 、 `int?` 、 `uint` 、 `uint?` 、 `long` `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `GUID` 、、、、 `GUID?` 、、、、、、、、、、、、、、、、、和。

LINQ to XML 為物件提供相同的轉換運算子 <xref:System.Xml.Linq.XAttribute> 。

## <a name="value-property-example"></a>Value 屬性範例

您可以使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來擷取項目的內容：

```csharp
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + e.Value);
```

```vb
Dim e As XElement = <StringElement>abcde</StringElement>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & e.Value)
```

這個範例會產生下列輸出：

```output
<StringElement>abcde</StringElement>
Value of e:abcde
```

## <a name="element-might-not-exist-example"></a>元素可能不存在範例

有時候您會嘗試取出專案的值，即使您不確定它是否存在也是一樣。 在此情況下，當您將轉換元素指派給可為 null 的參考型別或可為 null 的實值型別時，如果專案不存在，則指派的變數會設定為 `null` (c # ) 或 `nothing` (Visual Basic) 。 下列程式碼顯示當元素可能不存在時，使用轉換比使用屬性更容易 <xref:System.Xml.Linq.XElement.Value%2A> 。

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "child 1 content"),
    new XElement("Child2", "2")
);

// The following assignments show why it's easier to use
// casting when the element might or might not exist.

string c1 = (string)root.Element("Child1");
Console.WriteLine("c1:{0}", c1 == null ? "element doesn't exist" : c1);

int? c2 = (int?)root.Element("Child2");
Console.WriteLine("c2:{0}", c2 == null ? "element doesn't exist" : c2.ToString());

string c3 = (string)root.Element("Child3");
Console.WriteLine("c3:{0}", c3 == null ? "element doesn't exist" : c3);

int? c4 = (int?)root.Element("Child4");
Console.WriteLine("c4:{0}", c4 == null ? "element doesn't exist" : c4.ToString());

Console.WriteLine();

// The following assignments show the required code when using
// the Value property when the element might or might not exist.
// Notice that this is more difficult than the casting approach.

XElement e1 = root.Element("Child1");
string v1;
if (e1 == null)
    v1 = null;
else
    v1 = e1.Value;
Console.WriteLine("v1:{0}", v1 == null ? "element doesn't exist" : v1);

XElement e2 = root.Element("Child2");
int? v2;
if (e2 == null)
    v2 = null;
else
    v2 = Int32.Parse(e2.Value);
Console.WriteLine("v2:{0}", v2 == null ? "element doesn't exist" : v2.ToString());

XElement e3 = root.Element("Child3");
string v3;
if (e3 == null)
    v3 = null;
else
    v3 = e3.Value;
Console.WriteLine("v3:{0}", v3 == null ? "element doesn't exist" : v3);

XElement e4 = root.Element("Child4");
int? v4;
if (e4 == null)
    v4 = null;
else
    v4 = Int32.Parse(e4.Value);
Console.WriteLine("v4:{0}", v4 == null ? "element doesn't exist" : v4.ToString());
```

```vb
Dim root As XElement = <Root>
                           <Child1>child 1 content</Child1>
                           <Child2>2</Child2>
                       </Root>

' The following assignments show why it's easier to use
' casting when the element might or might not exist.

Dim c1 As String = CStr(root.Element("Child1"))
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element doesn't exist", c1))

Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element doesn't exist", c2.ToString()))

Dim c3 As String = CStr(root.Element("Child3"))
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element doesn't exist", c3))

Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element doesn't exist", c4.ToString()))

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
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element doesn't exist", v1))

Dim e2 As XElement = root.Element("Child2")
Dim v2 As Nullable(Of Integer)
If (e2 Is Nothing) Then
    v2 = Nothing
Else
    v2 = e2.Value
End If
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element doesn't exist", v2))

Dim e3 As XElement = root.Element("Child3")
Dim v3 As String
If (e3 Is Nothing) Then
    v3 = Nothing
Else
    v3 = e3.Value
End If
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element doesn't exist", v3))

Dim e4 As XElement = root.Element("Child4")
Dim v4 As Nullable(Of Integer)
If (e4 Is Nothing) Then
    v4 = Nothing
Else
    v4 = e4.Value
End If
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element doesn't exist", v4))
```

這個範例會產生下列輸出：

```output
c1:child 1 content
c2:2
c3:element doesn't exist
c4:element doesn't exist

v1:child 1 content
v2:2
v3:element doesn't exist
v4:element doesn't exist
```

一般情況下，您可以藉由轉換來取得專案和屬性的內容，以撰寫更簡單的程式碼。

## <a name="see-also"></a>另請參閱

- [LINQ to XML 軸總覽](linq-xml-axes-overview.md)
