---
title: 如何針對命名空間中的 XML 撰寫查詢-LINQ to XML
description: '若要在命名空間中的 XML 上撰寫查詢，您可以使用具有正確命名空間的 XName 物件。 瞭解如何在 c # 和 Visual Basic 中進行這項作業，以及如何建立查詢。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 7d2c765c30409b019bf4723b9161c577e2074c04
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552142"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-linq-to-xml"></a>如何在命名空間中撰寫 XML 的查詢 (LINQ to XML) 

若要在命名空間中的 XML 上撰寫查詢，您必須使用 <xref:System.Xml.Linq.XName> 具有正確命名空間的物件。

若為 C#，最常見的方法是使用包含 URI 的字串初始化 <xref:System.Xml.Linq.XNamespace>，然後使用加法運算子多載結合命名空間與區域名稱。

針對 Visual Basic，最常見的方法是定義全域命名空間，然後使用 XML 常值和使用全域命名空間的 XML 屬性。 您可以定義預設的全域命名空間，在此情況下，XML 常值中的項目預設會在命名空間中。 或者，您可以使用前置詞來定義全域命名空間，然後視需要在 XML 常值和 XML 屬性中使用前置詞。 如同 XML 的其他格式，這些屬性預設永遠在沒有命名空間中。

本文的第一個範例示範如何在預設命名空間中建立 XML 樹狀結構。 第二個範例顯示如何在命名空間中建立具有前置詞的 XML 樹狀結構。

## <a name="example-create-a-tree-in-a-default-namespace-and-retrieve-elements"></a>範例：在預設命名空間中建立樹狀結構並取出元素

下列範例會在預設命名空間中建立 XML 樹狀結構，然後抓取專案的集合。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
            From el In root.<Child> _
            Select el
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
1
2
3
```

## <a name="example-create-a-tree-in-a-namespace-with-a-prefix-and-retrieve-elements"></a>範例：在命名空間中建立具有前置詞和取得元素的樹狀結構

在 c # 中，不論您是在使用具有前置詞的命名空間的 XML 樹狀結構上撰寫查詢，或是在具有預設命名空間的 XML 樹狀結構上撰寫查詢，您都可以使用相同的方式撰寫查詢。

下列範例會在命名空間中建立具有前置詞的 XML 樹狀結構，然後抓取專案的集合。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
    <aw:Child>1</aw:Child>
    <aw:Child>2</aw:Child>
    <aw:Child>3</aw:Child>
    <aw:AnotherChild>4</aw:AnotherChild>
    <aw:AnotherChild>5</aw:AnotherChild>
    <aw:AnotherChild>6</aw:AnotherChild>
</aw:Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>1</aw:Child>
                <aw:Child>2</aw:Child>
                <aw:Child>3</aw:Child>
                <aw:AnotherChild>4</aw:AnotherChild>
                <aw:AnotherChild>5</aw:AnotherChild>
                <aw:AnotherChild>6</aw:AnotherChild>
            </aw:Root>
        Dim c1 As IEnumerable(Of XElement) = _
            From el In root.<aw:Child> _
            Select el
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
1
2
3
```

## <a name="see-also"></a>另請參閱

- [命名空間總覽](namespaces-overview.md)
