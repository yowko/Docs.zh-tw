---
title: 如何尋找具有特定子項目的元素-LINQ to XML
description: 尋找其子項目有特定值的元素
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 2f97f920ce09222858a0a51eb52ffe0d58dba960
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678635"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-linq-to-xml"></a><span data-ttu-id="255b5-103">如何尋找具有特定子專案的元素， (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="255b5-103">How to find an element with a specific child element (LINQ to XML)</span></span>

<span data-ttu-id="255b5-104">本文說明如何尋找子專案具有特定值的元素。</span><span class="sxs-lookup"><span data-stu-id="255b5-104">This article shows how to find an element whose child element has a specific value.</span></span>

## <a name="example-find-an-element-whose-child-element-has-a-specific-value"></a><span data-ttu-id="255b5-105">範例：尋找其子項目有特定值的元素</span><span class="sxs-lookup"><span data-stu-id="255b5-105">Example: Find an element whose child element has a specific value</span></span>

<span data-ttu-id="255b5-106">此範例會尋找 `Test` `CommandLine` 其子項目具有 "Examp2.EXE" 值的元素。</span><span class="sxs-lookup"><span data-stu-id="255b5-106">The example finds the `Test` element whose `CommandLine` child element has a value of "Examp2.EXE".</span></span> <span data-ttu-id="255b5-107">此範例會使用 XML [檔範例 xml 檔：測試](sample-xml-file-test-configuration.md)設定。</span><span class="sxs-lookup"><span data-stu-id="255b5-107">The example uses XML document [Sample XML file: Test configuration](sample-xml-file-test-configuration.md).</span></span>

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

<span data-ttu-id="255b5-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="255b5-108">This example produces the following output:</span></span>

```output
0002
0006
```

<span data-ttu-id="255b5-109">請注意，程式碼的 Visual Basic 版本會使用 [Xml 子軸屬性](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)、 [xml 屬性軸屬性](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)和 [xml Value 屬性](../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="255b5-109">Note that the Visual Basic version of the code uses the [XML Child axis property](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

## <a name="example-find-when-the-xml-is-in-a-namespace"></a><span data-ttu-id="255b5-110">範例：尋找 XML 在命名空間中的時間</span><span class="sxs-lookup"><span data-stu-id="255b5-110">Example: Find when the XML is in a namespace</span></span>

<span data-ttu-id="255b5-111">下列範例會執行與上一個範例相同，但在命名空間中的 XML。</span><span class="sxs-lookup"><span data-stu-id="255b5-111">The following example does the same as the previous one, but for XML that's in a namespace.</span></span> <span data-ttu-id="255b5-112">此範例會使用 XML [檔範例 xml 檔：命名空間中的測試](sample-xml-file-test-configuration-namespace.md)設定。</span><span class="sxs-lookup"><span data-stu-id="255b5-112">The example uses XML document [Sample XML file: Test configuration in a namespace](sample-xml-file-test-configuration-namespace.md).</span></span>

<span data-ttu-id="255b5-113">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="255b5-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

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

<span data-ttu-id="255b5-114">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="255b5-114">This example produces the following output:</span></span>

```output
0002
0006
```

## <a name="see-also"></a><span data-ttu-id="255b5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="255b5-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="255b5-116">標準查詢運算子概觀</span><span class="sxs-lookup"><span data-stu-id="255b5-116">Standard Query Operators Overview</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="255b5-117">投影作業</span><span class="sxs-lookup"><span data-stu-id="255b5-117">Projection Operations</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
