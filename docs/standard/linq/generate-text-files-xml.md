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
# <a name="how-to-generate-text-files-from-xml-linq-to-xml"></a>如何從 XML (LINQ to XML) 產生文字檔

本文提供的範例示範如何使用 c # 和 Visual Basic，從 XML 檔案 (CSV) 文字檔產生逗點分隔值。

## <a name="example-generate-a-csv-file-from-an-xml-document"></a>範例：從 XML 檔產生 CSV 檔案

此範例會從 XML [檔範例 xml 檔：客戶和訂單](sample-xml-file-customers-orders.md)產生 CSV 檔案。

C # 版本會使用方法語法和 `Aggregate` 運算子，在單一運算式中產生檔案。 如需詳細資訊，請參閱 [LINQ (c # ) 中的查詢語法和方法語法 ](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。

Visual Basic 版本會使用程式性程式碼，將字串的集合匯總成單一字串。

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

這個範例會產生下列輸出：

```output
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA
```

## <a name="see-also"></a>另請參閱

- [LINQ 中的查詢語法及方法語法 (C#)](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
