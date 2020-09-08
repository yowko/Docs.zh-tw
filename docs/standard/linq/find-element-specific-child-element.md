---
title: 如何尋找具有特定子項目的元素-LINQ to XML
description: 尋找其子項目有特定值的元素
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 947983ea1ea9d50528a9cb0beaa9c86b545e5ea6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552088"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-linq-to-xml"></a>如何尋找具有特定子專案的元素， (LINQ to XML) 

本文說明如何尋找子專案具有特定值的元素。

## <a name="example-find-an-element-whose-child-element-has-a-specific-value"></a>範例：尋找其子項目有特定值的元素

此範例會尋找 `Test` `CommandLine` 其子項目具有 "Examp2.EXE" 值的元素。 此範例會使用 XML [檔範例 xml 檔：測試](sample-xml-file-test-configuration.md)設定。

```csharp
XElement root = XElement.Load("TestConfig.xml");
IEnumerable<XElement> tests =
    from el in root.Elements("Test")
    where (string)el.Element("CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Dim root As XElement = XElement.Load("TestConfig.xml")
Dim tests As IEnumerable(Of XElement) = _
    From el In root.<Test> _
    Where el.<CommandLine>.Value = "Examp2.EXE" _
    Select el
For Each el as XElement In tests
    Console.WriteLine(el.@TestId)
Next
```

這個範例會產生下列輸出：

```output
0002
0006
```

請注意，程式碼的 Visual Basic 版本會使用 [Xml 子軸屬性](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)、 [xml 屬性軸屬性](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)和 [xml Value 屬性](../../visual-basic/language-reference/xml-axis/xml-value-property.md)。

## <a name="example-find-when-the-xml-is-in-a-namespace"></a>範例：尋找 XML 在命名空間中的時間

下列範例會執行與上一個範例相同，但在命名空間中的 XML。 此範例會使用 XML [檔範例 xml 檔：命名空間中的測試](sample-xml-file-test-configuration-namespace.md)設定。

如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

```csharp
XElement root = XElement.Load("TestConfigInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<XElement> tests =
    from el in root.Elements(ad + "Test")
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")
        Dim tests As IEnumerable(Of XElement) = _
            From el In root.<Test> _
            Where el.<CommandLine>.Value = "Examp2.EXE" _
            Select el
        For Each el As XElement In tests
            Console.WriteLine(el.@TestId)
        Next
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
0002
0006
```

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [標準查詢運算子概觀 (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [投射作業 (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [標準查詢運算子概觀 (Visual Basic)](/../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
