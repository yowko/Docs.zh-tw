---
title: Visual Basic 中的 XML 常值-LINQ to XML
description: 您可以使用 XML 常值和內嵌運算式，在 Visual Basic 中建立 XML 樹狀結構。 內嵌的運算式可讓您評估運算式，並將運算式的結果插入到 XML 樹狀中。
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552200"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a>Visual Basic 中的 XML 常值 (LINQ to XML) 

本文提供有關使用 XML 常值和內嵌運算式在 Visual Basic 中建立 XML 樹狀結構的資訊。

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a>範例：使用 XML 常值建立 XML 樹狀結構

下列範例示範如何 <xref:System.Xml.Linq.XElement> 使用 XML 常值建立，在此案例中為 `contacts` ：

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a>範例：使用 XML 常值以簡單的內容建立 System.xml.linq.xelement>

您可以建立包含簡單內容的 <xref:System.Xml.Linq.XElement>，如下所示：

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

這個範例會產生下列輸出：

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a>範例：使用 XML 常值建立空白元素

您可以建立空的 <xref:System.Xml.Linq.XElement>，如下所示：

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

這個範例會產生下列輸出：

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a>使用內嵌運算式來建立內容

XML 常值的其中一個重要功能是，這些 XML 常值允許內嵌的運算式。 內嵌的運算式可讓您評估運算式，並將運算式的結果插入到 XML 樹狀中。 如果運算式評估 <xref:System.Xml.Linq.XElement> 的型別，會將項目插入到樹狀中。 如果運算式評估 <xref:System.Xml.Linq.XAttribute> 的型別，會將屬性插入到樹狀結構中。 您只能將專案和屬性插入樹狀結構中的元素和屬性。

請務必注意，只有單一運算式可進入內嵌的運算式。 您無法內嵌多個語句。 如果運算式的延伸超過單一行，您必須使用行接續字元。

如果您使用內嵌的運算式，將現有的節點 (包括項目) 和屬性加入到新的 XML 樹狀結構，而且如果現有的節點已經成為父代，這些節點就會遭到複製。 新複製的節點會附加到新的 XML 樹狀結構中。 如果現有的節點沒有父代，這些節點只會附加到新的 XML 樹狀結構。 本文的最後一個範例將示範這項功能。

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a>範例：使用內嵌運算式插入元素

下列範例使用內嵌的運算式，將項目插入到樹狀中：

```vb
xmlTree1 As XElement = _
    <Root>
        <Child>Contents</Child>
    </Root>
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child> %>
    </Root>
Console.WriteLine(xmlTree2)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Child>Contents</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-for-content"></a>範例：將內嵌的運算式用於內容

您可以使用內嵌的運算式提供項目的內容：

```vb
Dim str As String
str = "Some content"
Dim root As XElement = <Root><%= str %></Root>
Console.WriteLine(root)
```

這個範例會產生下列輸出：

```xml
<Root>Some content</Root>
```

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a>範例：在內嵌運算式中使用 LINQ 查詢

您可以使用 LINQ 查詢的結果來提供元素的內容：

```vb
Dim arr As Integer() = {1, 2, 3}

Dim n As XElement = _
    <Root>
        <%= From i In arr Select <Child><%= i %></Child> %>
    </Root>

Console.WriteLine(n)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Child>3</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a>範例：使用內嵌運算式提供節點名稱

您也可以使用內嵌運算式來計算屬性名稱、屬性值、元素名稱和元素值：

```vb
Dim eleName As String = "ele"
Dim attName As String = "att"
Dim attValue As String = "aValue"
Dim eleValue As String = "eValue"
Dim n As XElement = _
    <Root <%= attName %>=<%= attValue %>>
        <<%= eleName %>>
            <%= eleValue %>
        </>
    </Root>
Console.WriteLine(n)
```

這個範例會產生下列輸出：

```xml
<Root att="aValue">
  <ele>eValue</ele>
</Root>
```

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a>範例：使用內嵌運算式來複製和附加節點

如先前所述，如果您使用內嵌運算式來加入現有的節點 (包括專案) 和屬性新增至新的 XML 樹狀結構，而且如果加入的節點已經成為父節點，則會複製節點，並將複製附加至新的 XML 樹狀結構。 如果現有的節點不是父節點，這些節點只會附加到新的 XML 樹狀結構。

下列程式碼示範將成為父代的項目加入到樹狀結構時，以及將沒有父代的項目加入樹狀結構時的行為。

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
Dim child2 As XElement = <Child2>2</Child2>

' Create a tree and add Child1 and Child2 to it.
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child1>(0) %>
        <%= child2 %>
    </Root>

' Compare Child1 identity.
Console.WriteLine("Child1 was {0}", _
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _
    "attached", "cloned"))

' Compare Child2 identity.
Console.WriteLine("Child2 was {0}", _
    IIf(child2 Is xmlTree2.Element("Child2"), _
    "attached", "cloned"))
```

這個範例會產生下列輸出：

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a>另請參閱

- [功能結構](functional-construction.md)
