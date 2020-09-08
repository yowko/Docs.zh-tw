---
title: 如何控制命名空間前置詞-LINQ to XML
description: '您可以在 c # 中序列化 XML 樹狀結構，並 Visual Basic 來控制命名空間前置詞。 若要這樣做，請插入宣告命名空間的屬性。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 07efc23c11cd0dc0d281968911cf24d6ecbc76a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552139"
---
# <a name="how-to-control-namespace-prefixes-linq-to-xml"></a>如何控制命名空間前置詞 (LINQ to XML)

本文描述如何在 c # 中序列化 XML 樹狀結構和 Visual Basic 時，控制命名空間前置詞。

在許多情況下，不需要控制命名空間前置詞。 不過，某些 XML 程式設計工具需要它。 例如，您可能會操作 XSLT 樣式表單或 XAML 檔，其中包含參考特定命名空間前置詞的內嵌 XPath 運算式。 在這種情況下，請務必使用這些前置詞來序列化檔。 這是控制命名空間前置詞的常見原因。

另一個原因是您想要讓使用者手動編輯 XML 檔，而且您想要建立方便使用者輸入的命名空間前置詞。 例如，您可能要產生 XSD 文件。 若要轉換結構描述，建議您使用 `xs` 或 `xsd` 做為結構描述命名空間的前置詞。

若要控制命名空間前置詞，您可插入宣告命名空間的屬性。 如果您宣告具有特定前置詞的命名空間，LINQ to XML 將會在序列化時嘗試接受命名空間前置詞。

若要建立宣告具有特定前置詞之命名空間的屬性，您可以建立屬性，其中之屬性名稱的命名空間為 <xref:System.Xml.Linq.XNamespace.Xmlns%2A>，而屬性的名稱為命名空間前置詞。 屬性的值為命名空間的 URI。

## <a name="example-create-two-namespaces-that-have-prefixes"></a>範例：建立具有前置詞的兩個命名空間

這個範例會宣告兩個命名空間。 它會指定命名空間的前置詞 `aw` `http://www.adventure-works.com` ，以及 `fc` 命名空間的前置詞 `www.fourthcoffee.com` 。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

This example produces the following output:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a>另請參閱

- [命名空間總覽](namespaces-overview.md)
