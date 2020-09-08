---
title: 如何從 XML 產生文字檔-LINQ to XML
description: '您可以使用 c # 和 Visual Basic，從 XML 檔案產生 (CSV) 文字檔的逗號分隔值。 本文提供一個範例。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 2650d223d542b3582fa8cd2a00f4b880ef04e5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552126"
---
# <a name="how-to-generate-text-files-from-xml-linq-to-xml"></a><span data-ttu-id="a36c3-104">如何從 XML (LINQ to XML) 產生文字檔</span><span class="sxs-lookup"><span data-stu-id="a36c3-104">How to generate text files from XML (LINQ to XML)</span></span>

<span data-ttu-id="a36c3-105">本文提供的範例示範如何使用 c # 和 Visual Basic，從 XML 檔案 (CSV) 文字檔產生逗點分隔值。</span><span class="sxs-lookup"><span data-stu-id="a36c3-105">This article provides an example that shows how to use C# and Visual Basic to generate a comma-separated values (CSV) text file from an XML file.</span></span>

## <a name="example-generate-a-csv-file-from-an-xml-document"></a><span data-ttu-id="a36c3-106">範例：從 XML 檔產生 CSV 檔案</span><span class="sxs-lookup"><span data-stu-id="a36c3-106">Example: Generate a CSV file from an XML document</span></span>

<span data-ttu-id="a36c3-107">此範例會從 XML [檔範例 xml 檔：客戶和訂單](sample-xml-file-customers-orders.md)產生 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="a36c3-107">This example generates a CSV file from XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md).</span></span>

<span data-ttu-id="a36c3-108">C # 版本會使用方法語法和 `Aggregate` 運算子，在單一運算式中產生檔案。</span><span class="sxs-lookup"><span data-stu-id="a36c3-108">The C# version uses method syntax and the `Aggregate` operator to generate the file in a single expression.</span></span> <span data-ttu-id="a36c3-109">如需詳細資訊，請參閱 [LINQ (c # ) 中的查詢語法和方法語法 ](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="a36c3-109">For more information, see [Query Syntax and Method Syntax in LINQ (C#)](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>

<span data-ttu-id="a36c3-110">Visual Basic 版本會使用程式性程式碼，將字串的集合匯總成單一字串。</span><span class="sxs-lookup"><span data-stu-id="a36c3-110">The Visual Basic version uses procedural code to aggregate the collection of strings into a single string.</span></span>

```csharp
XElement custOrd = XElement.Load("CustomersOrders.xml");
string csv =
    (from el in custOrd.Element("Customers").Elements("Customer")
    select
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",
            (string)el.Attribute("CustomerID"),
            (string)el.Element("CompanyName"),
            (string)el.Element("ContactName"),
            (string)el.Element("ContactTitle"),
            (string)el.Element("Phone"),
            (string)el.Element("FullAddress").Element("Address"),
            (string)el.Element("FullAddress").Element("City"),
            (string)el.Element("FullAddress").Element("Region"),
            (string)el.Element("FullAddress").Element("PostalCode"),
            (string)el.Element("FullAddress").Element("Country"),
            Environment.NewLine
        )
    )
    .Aggregate(
        new StringBuilder(),
        (sb, s) => sb.Append(s),
        sb => sb.ToString()
    );
Console.WriteLine(csv);
```

```vb
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
Dim strCollection As IEnumerable(Of String) = _
    From el In custOrd.<Customers>.<Customer> _
    Select _
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}", _
            el.@CustomerID, _
            el.<CompanyName>.Value, _
            el.<ContactName>.Value, _
            el.<ContactTitle>.Value, _
            el.<Phone>.Value, _
            el.<FullAddress>.<Address>.Value, _
            el.<FullAddress>.<City>.Value, _
            el.<FullAddress>.<Region>.Value, _
            el.<FullAddress>.<PostalCode>.Value, _
            el.<FullAddress>.<Country>.Value, _
            Environment.NewLine _
        )
Dim sb As StringBuilder = New StringBuilder()
For Each str As String In strCollection
    sb.Append(str)
Next
Console.WriteLine(sb.ToString())
```

<span data-ttu-id="a36c3-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a36c3-111">This example produces the following output:</span></span>

```output
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA
```

## <a name="see-also"></a><span data-ttu-id="a36c3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a36c3-112">See also</span></span>

- [<span data-ttu-id="a36c3-113">LINQ 中的查詢語法及方法語法 (C#)</span><span class="sxs-lookup"><span data-stu-id="a36c3-113">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
