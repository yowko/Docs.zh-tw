---
title: 如何根據位置 LINQ to XML 尋找子項目
description: 瞭解如何尋找以元素位置為基礎的尋找元素。 其中會顯示三個方法：一個使用 XPathEvaluate，兩個使用 LINQ to XML 查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 889e3dbac3acf229fd49422285d650fc13792521
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557118"
---
# <a name="how-to-find-child-elements-based-on-position-linq-to-xml"></a>如何根據位置 (LINQ to XML 尋找子項目) 

本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 來根據專案位置尋找元素，例如尋找第二個專案，或第三個到第五個專案。 它也會示範兩種使用 LINQ to XML 查詢來執行相同動作的方式。

有兩種方法可以用延遲方式撰寫此 LINQ to XML 查詢。 您可以使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 運算子，或者，您可以使用採用索引的 <xref:System.Linq.Enumerable.Where%2A> 多載。 當您使用 <xref:System.Linq.Enumerable.Where%2A> 多載時，您可以使用採用兩個引數的 Lambda 運算式。 下列範例顯示根據位置進行選擇的兩種方法。

## <a name="example-find-the-second-through-the-fourth-test-elements"></a>範例：尋找第二個到第四個 `Test` 元素

此範例會在範例 XML 檔中尋找第二個到第四個 `Test` 元素 [：測試](sample-xml-file-test-configuration.md)設定。 結果為項目的集合。

XPath 運算式為 `Test[position() >= 2 and position() <= 4]`。

```csharp
XElement testCfg = XElement.Load("TestConfig.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    testCfg
    .Elements("Test")
    .Skip(1)
    .Take(3);

// LINQ to XML query
IEnumerable<XElement> list2 =
    testCfg
    .Elements("Test")
    .Where((el, idx) => idx >= 1 && idx <= 3);

// XPath expression
IEnumerable<XElement> list3 =
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");

if (list1.Count() == list2.Count() &&
    list1.Count() == list3.Count() &&
    list1.Intersect(list2).Count() == list1.Count() &&
    list1.Intersect(list3).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim testCfg As XElement = XElement.Load("TestConfig.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    testCfg.Elements("Test").Skip(1).Take(3)

'LINQ to XML query
Dim list2 As IEnumerable(Of XElement) = _
    testCfg.Elements("Test"). _
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)

' XPath expression
Dim list3 As IEnumerable(Of XElement) = _
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")

If list1.Count() = list2.Count() And _
       list1.Count() = list3.Count() And _
       list1.Intersect(list2).Count() = list1.Count() And _
       list1.Intersect(list3).Count() = list1.Count() Then

    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

這個範例會產生下列輸出：

```output
Results are identical
<Test TestId="0002" TestType="CMD">
  <Name>Find succeeding characters</Name>
  <CommandLine>Examp2.EXE</CommandLine>
  <Input>abc</Input>
  <Output>def</Output>
</Test>
<Test TestId="0003" TestType="GUI">
  <Name>Convert multiple numbers to strings</Name>
  <CommandLine>Examp2.EXE /Verbose</CommandLine>
  <Input>123</Input>
  <Output>One Two Three</Output>
</Test>
<Test TestId="0004" TestType="GUI">
  <Name>Find correlated key</Name>
  <CommandLine>Examp3.EXE</CommandLine>
  <Input>a1</Input>
  <Output>b1</Output>
</Test>
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](./comparison-xpath-linq-xml.md)
