---
title: 使用 Visual Basic LINQ to XML 中的全域命名空間
description: 您可以使用 Imports 語句，在 Visual Basic 中宣告命名空間，這是指命名空間是預設命名空間，還是有前置詞。 本文討論匯入語句和使用命名空間的其他層面。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: f05fcab6788388e36e2b68a2d4f022ea63e74280
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552816"
---
# <a name="work-with-global-namespaces-in-visual-basic-linq-to-xml"></a>使用 Visual Basic (LINQ to XML 中的全域命名空間) 

Visual Basic 中 XML 常值的其中一個重要功能，就是使用語句宣告 XML 命名空間的功能 `Imports` 。 利用這個功能，您可以宣告使用前置詞的 XML 命名空間，或者，您可以宣告預設的 XML 命名空間。

這項功能在兩種情況下很有用：

- XML 常值中宣告的命名空間不會延續到內嵌的運算式中。 宣告全域命名空間可減少使用內嵌運算式搭配命名空間所需的工作量。
- 您必須宣告全域命名空間，才能使用具有 XML 屬性的命名空間。

您可以在專案層級宣告全域命名空間。 您也可以在複寫專案層級全域命名空間的模組層級宣告全域命名空間。 最後，您可以在 XML 常值中複寫全域命名空間。

使用全域宣告命名空間中的 XML 常值或 XML 屬性時，您可以在 Visual Studio 中將滑鼠游標移到 XML 常值或屬性的擴充名稱。 您將會在工具提示中看到擴充名稱。

您可以使用 <xref:System.Xml.Linq.XNamespace> 方法，取得對應到全域命名空間的 `GetXmlNamespace` 物件。

## <a name="example-use-imports-to-declare-a-global-namespace"></a>範例：用 `Imports` 來宣告全域命名空間

下列範例會使用語句宣告預設的全域命名空間 `Imports` ，然後 <xref:System.Xml.Linq.XElement> 使用 XML 常值來初始化該命名空間中的物件：

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

這個範例會產生下列輸出：

```xml
<Root xmlns="http://www.adventure-works.com" />
```

## <a name="example-declare-a-global-namespace-that-has-a-prefix"></a>範例：宣告具有前置詞的全域命名空間

下一個範例會宣告具有前置詞的全域命名空間，並使用 XML 常值來初始化元素：

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

這個範例會產生下列輸出：

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" />
```

## <a name="example-declare-a-default-namespace-and-use-an-embedded-expression-for-the-child-element"></a>範例：宣告預設命名空間，並針對元素使用內嵌運算式 `Child`

在 XML 常值中宣告的命名空間不會延續到內嵌的運算式中。 下列範例會宣告預設的命名空間，然後使用專案的內嵌運算式 `Child` 。

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child/> %>
    </Root>
Console.WriteLine(root)
```

這個範例會產生下列輸出：

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="" />
</Root>
```

產生的 XML 包含預設命名空間的宣告，因此 `Child` 元素不在命名空間中。

您可以在內嵌運算式中宣告不同的命名空間，如下所示：

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child xmlns="http://www.adventure-works.com"/> %>
    </Root>
Console.WriteLine(root)
```

這個範例會產生下列輸出：

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="http://www.adventure-works.com" />
</Root>
```

不過，使用全域預設命名空間時，您可以使用 XML 常值，而不需要宣告命名空間。 產生的 XML 會在全域宣告的預設命名空間中，如下列範例所示：

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root>
                                   <%= <Child/> %>
                               </Root>
        Console.WriteLine(root)
    End Sub
End Module
```

這個範例會產生下列輸出：

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child />
</Root>
```

## <a name="example-use-namespaces-with-xml-properties"></a>範例：搭配使用命名空間與 XML 屬性

如果您使用的是命名空間中的 XML 樹狀結構，而且您使用 XML 屬性，則必須使用全域命名空間，如此 XML 屬性也會在正確的命名空間中。 下列範例會宣告命名空間中的 XML 樹狀結構，然後列印元素的計數 `Child` 。

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <Child>content</Child>
    </Root>
Console.WriteLine(root.<Child>.Count())
```

這個範例表示沒有 `Child` 項目。 它會產生下列輸出：

```output
0
```

但是，如果您要宣告預設的全域命名空間，則 XML 常值和 XML 屬性都會位於預設的全域命名空間中：

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>content</Child>
            </Root>
        Console.WriteLine(root.<Child>.Count())
    End Sub
End Module
```

這個範例表示有一個 `Child` 項目， 它會產生下列輸出：

```output
1
```

如果您要宣告具有前置詞的全域命名空間，可以將前置詞同時用於 XML 常值和 XML 屬性：

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>content</aw:Child>
            </aw:Root>
        Console.WriteLine(root.<aw:Child>.Count())
    End Sub
End Module
```

## <a name="example-use-getxmlnamespace-to-get-an-xnamespace"></a>範例：使用 `GetXmlNamespace` 取得 `XNamespace`

您可以 <xref:System.Xml.Linq.XNamespace> 使用方法來取得物件 `GetXmlNamespace` ：

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Dim xn As XNamespace = GetXmlNamespace(aw)
        Console.WriteLine(xn)
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
http://www.adventure-works.com
```

## <a name="see-also"></a>另請參閱

- [命名空間總覽](namespaces-overview.md)
