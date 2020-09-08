---
title: 如何使用群組 LINQ to XML 建立階層
description: 查看如何根據不同專案中的相關值來分組資料的範例，然後重新排序以將相關的元素放在反映關聯性的元素下。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: cd913a2546227154fc48ee4e4ae7d007b7e926a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552274"
---
# <a name="how-to-create-hierarchy-using-grouping-linq-to-xml"></a><span data-ttu-id="f7a1d-103">如何使用群組 (LINQ to XML) 建立階層</span><span class="sxs-lookup"><span data-stu-id="f7a1d-103">How to create hierarchy using grouping (LINQ to XML)</span></span>

<span data-ttu-id="f7a1d-104">您可以根據不同專案中的相關值來分組資料，然後重新排序，將相關的元素放在反映關聯性的元素下。</span><span class="sxs-lookup"><span data-stu-id="f7a1d-104">Data can be grouped based on related values in different elements, then reordered to place related elements together under an element that reflects the relationship.</span></span> <span data-ttu-id="f7a1d-105">本文提供 c # 和 Visual Basic 的範例。</span><span class="sxs-lookup"><span data-stu-id="f7a1d-105">This article provides an example for C# and Visual Basic.</span></span>

## <a name="example-create-a-new-xml-document-in-which-data-is-grouped-by-category"></a><span data-ttu-id="f7a1d-106">範例：建立新的 XML 檔，其中的資料依類別目錄分組</span><span class="sxs-lookup"><span data-stu-id="f7a1d-106">Example: Create a new XML document in which data is grouped by category</span></span>

<span data-ttu-id="f7a1d-107">下列範例顯示如何將資料分組，並根據群組產生 XML。</span><span class="sxs-lookup"><span data-stu-id="f7a1d-107">The following example shows how to group data, and generate XML based on the grouping.</span></span> <span data-ttu-id="f7a1d-108">它會先依元素值的相等來分組資料 `<Category>` ，然後產生 xml 階層反映群組的新 xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="f7a1d-108">It first groups data by equality of value of the `<Category>` elements, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>

<span data-ttu-id="f7a1d-109">此範例會使用 XML [檔範例 xml 檔：數值資料](sample-xml-file-numerical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f7a1d-109">This example uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement doc = XElement.Load("Data.xml");
var newData =
    new XElement("Root",
        from data in doc.Elements("Data")
        group data by (string)data.Element("Category") into groupedData
        select new XElement("Group",
            new XAttribute("ID", groupedData.Key),
            from g in groupedData
            select new XElement("Data",
                g.Element("Quantity"),
                g.Element("Price")
            )
        )
    );
Console.WriteLine(newData);
```

```vb
Dim doc As XElement = XElement.Load("Data.xml")
Dim newData As XElement = _
    <Root>
        <%= _
            From data In doc.<Data> _
            Group By category = data.<Category>(0).Value _
            Into groupedData = Group _
            Select <Group ID=<%= category %>>
                       <%= _
                           From g In groupedData _
                           Select _
                           <Data>
                               <%= g.<Quantity>(0) %>
                               <%= g.<Price>(0) %>
                           </Data> _
                       %>
                   </Group> _
        %>
    </Root>
Console.WriteLine(newData)
```

<span data-ttu-id="f7a1d-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f7a1d-110">This example produces the following output:</span></span>

```xml
<Root>
  <Group ID="A">
    <Data>
      <Quantity>3</Quantity>
      <Price>24.50</Price>
    </Data>
    <Data>
      <Quantity>5</Quantity>
      <Price>4.95</Price>
    </Data>
    <Data>
      <Quantity>3</Quantity>
      <Price>66.00</Price>
    </Data>
    <Data>
      <Quantity>15</Quantity>
      <Price>29.00</Price>
    </Data>
  </Group>
  <Group ID="B">
    <Data>
      <Quantity>1</Quantity>
      <Price>89.99</Price>
    </Data>
    <Data>
      <Quantity>10</Quantity>
      <Price>.99</Price>
    </Data>
    <Data>
      <Quantity>8</Quantity>
      <Price>6.99</Price>
    </Data>
  </Group>
</Root>
```
