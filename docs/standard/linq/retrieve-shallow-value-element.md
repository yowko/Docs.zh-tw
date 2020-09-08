---
title: 如何取出元素的淺層值-LINQ to XML
description: 使用 `ShallowValue` 擴充方法來取出專案的淺層值。 淺層值只是該元素的值;也就是說，它不會包含子項目的值。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 761ffc07b13ebdc652b75bf96ba5b121c7912fd7
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552709"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-linq-to-xml"></a><span data-ttu-id="30af5-104">如何取出元素的淺層值 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="30af5-104">How to retrieve the shallow value of an element (LINQ to XML)</span></span>

<span data-ttu-id="30af5-105">本文說明如何取出專案的淺層值（這是該元素的值），而不包含子項目的值。</span><span class="sxs-lookup"><span data-stu-id="30af5-105">This article shows how to retrieve the shallow value of an element, which is the value of that element only, not including values of descendent elements.</span></span> <span data-ttu-id="30af5-106">當您想要根據項目的內容進行選取時，擷取表層值就非常有用。</span><span class="sxs-lookup"><span data-stu-id="30af5-106">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="30af5-107">當您使用 cast 或 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性來抓取專案值時，此值會包含下階。</span><span class="sxs-lookup"><span data-stu-id="30af5-107">When you use casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property to retrieve an element value, the value includes the descendants.</span></span> <span data-ttu-id="30af5-108">若要取得淺層值，您可以使用 `ShallowValue` 擴充方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="30af5-108">To retrieve the shallow value you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="30af5-109">此範例會宣告可抓取專案淺層值的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="30af5-109">The example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="30af5-110">接著會在查詢中使用此擴充方法，將所有包含計算值的項目列出。</span><span class="sxs-lookup"><span data-stu-id="30af5-110">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example-use-the-shallowvalue-extension-method-to-retrieve-the-shallow-value-of-an-element"></a><span data-ttu-id="30af5-111">範例：使用 `ShallowValue` 擴充方法來取出元素的淺層值</span><span class="sxs-lookup"><span data-stu-id="30af5-111">Example: Use the `ShallowValue` extension method to retrieve the shallow value of an element</span></span>

<span data-ttu-id="30af5-112">這些範例會使用包含下列內容 Report.xml 文字檔：</span><span class="sxs-lookup"><span data-stu-id="30af5-112">The examples uses the text file Report.xml that contains the following:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Report>
  <Section>
    <Heading>
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>
      <Column Name="Name">=Customer.Name.Heading</Column>
    </Heading>
    <Detail>
      <Column Name="CustomerId">=Customer.CustomerId</Column>
      <Column Name="Name">=Customer.Name</Column>
    </Detail>
  </Section>
</Report>
```

<span data-ttu-id="30af5-113">以下是範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="30af5-113">Here is the code for the example:</span></span>

```csharp
public static class MyExtensions
{
    public static string ShallowValue(this XElement xe)
    {
        return xe
               .Nodes()
               .OfType<XText>()
               .Aggregate(new StringBuilder(),
                          (s, c) => s.Append(c),
                          s => s.ToString());
    }
}

class Program
{
    static void Main(string[] args)
    {
        XElement root = XElement.Load("Report.xml");

        IEnumerable<XElement> query = from el in root.Descendants()
                                      where el.ShallowValue().StartsWith("=")
                                      select el;

        foreach (var q in query)
        {
            Console.WriteLine("{0}{1}{2}",
                q.Name.ToString().PadRight(8),
                q.Attribute("Name").ToString().PadRight(20),
                q.ShallowValue());
        }
    }
}
```

```vb
Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function ShallowValue(ByVal xe As XElement)
        Return xe _
               .Nodes() _
               .OfType(Of XText)() _
               .Aggregate(New StringBuilder(), _
                              Function(s, c) s.Append(c), _
                              Function(s) s.ToString())
    End Function

    Sub Main()
        Dim root As XElement = XElement.Load("Report.xml")

        Dim query As IEnumerable(Of XElement) = _
            From el In root.Descendants() _
            Where (el.ShallowValue().StartsWith("=")) _
            Select el

        For Each q As XElement In query
            Console.WriteLine("{0}{1}{2}", _
                q.Name.ToString().PadRight(8), _
                q.Attribute("Name").ToString().PadRight(20), _
                q.ShallowValue())
        Next
    End Sub
End Module
```

<span data-ttu-id="30af5-114">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="30af5-114">This example produces the following output:</span></span>

```output
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="30af5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30af5-115">See also</span></span>

- [<span data-ttu-id="30af5-116">LINQ to XML 軸總覽</span><span class="sxs-lookup"><span data-stu-id="30af5-116">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
