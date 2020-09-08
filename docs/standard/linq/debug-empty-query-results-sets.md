---
title: 如何針對空的查詢結果集進行調試-LINQ to XML
description: 當您查詢預設命名空間中的 XML 樹狀結構時，請避免查詢常見的錯誤，因為 XML 不在命名空間中。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 3320763fffe77ddd6ca4c78e77629ec0805e4290
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552270"
---
# <a name="how-to-debug-empty-query-results-sets-linq-to-xml"></a>如何將空的查詢結果集 (LINQ to XML) 

查詢 XML 時所遇到的其中一個最常見的問題是，如果 XML 樹狀結構有預設的命名空間，即使 XML 不在命名空間中，開發人員有時候還是會撰寫查詢。

本文中的第一組範例會示範如何載入預設命名空間中的 XML，然後進行不當查詢的一般方式。

第二組範例顯示所需的修正，讓您可以在命名空間中查詢 XML。

如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

## <a name="example-an-improper-query-on-xml-in-a-namespace"></a>範例：對命名空間中的 XML 進行不當查詢

此範例顯示 XML 在命名空間中的建立，以及傳回空結果集的查詢。

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
```

此範例會產生下列結果：

```output
Result set follows:
End of result set
```

## <a name="example-a-proper-query-on-xml-in-a-namespace"></a>範例：對命名空間中的 XML 進行適當查詢

此範例示範如何在命名空間中建立 XML，以及正確編碼的查詢。

解決方案是要宣告與初始化 <xref:System.Xml.Linq.XNamespace> 物件，並在指定 <xref:System.Xml.Linq.XName> 物件時使用。 在這個情況下，<xref:System.Xml.Linq.XContainer.Elements%2A> 方法的引數為 <xref:System.Xml.Linq.XName> 物件。

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
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

此範例會產生下列結果：

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>另請參閱

- [基本查詢 (LINQ to XML)  (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
