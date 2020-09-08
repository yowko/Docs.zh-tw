---
title: 預設命名空間的範圍-LINQ to XML
description: XML 樹狀結構中表示的預設命名空間不在查詢的範圍內。 以下是查詢它們的適當且不適當的方式。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552820"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a>預設命名空間的範圍 (LINQ to XML) 

XML 樹狀結構中表示的預設命名空間不在查詢的範圍內。 如果您有在預設命名空間中的 XML，您必須結合命名空間與區功能變數名稱稱，以建立要在查詢中使用的限定名稱。

查詢具有預設命名空間的 XML 樹狀結構時，常見的錯誤是將查詢撰寫成 XML 不在命名空間中。 第一個範例顯示預設命名空間的一般不適當查詢。 第二個範例顯示適當的查詢。

## <a name="example-improper-query-of-xml-in-a-namespace"></a>範例：命名空間中的 XML 查詢不正確

此範例示範如何在命名空間中建立 XML，以及傳回空結果集的不適當查詢。

```csharp
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
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
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
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a>範例：適當地查詢命名空間中的 XML

此範例示範如何在命名空間中建立 XML 和適當的查詢。

在 c # 中，正確的方法是宣告和初始化 <xref:System.Xml.Linq.XNamespace> 物件，並在指定物件時使用它 <xref:System.Xml.Linq.XName> 。 在這個情況下，<xref:System.Xml.Linq.XContainer.Elements%2A> 方法的引數為 <xref:System.Xml.Linq.XName> 物件。

使用 Visual Basic 時的正確方法為宣告並初始化全域預設命名空間。 這會將所有 XML 屬性放在預設的命名空間中。

程式碼如下：

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
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
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>另請參閱

- [命名空間總覽](namespaces-overview.md)
