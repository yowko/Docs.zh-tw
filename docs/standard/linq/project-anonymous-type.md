---
title: 如何投影匿名型別-LINQ to XML
description: '您可以投影至匿名型別，而不是只建立在投影中使用的型別。 本文提供 c # 和 Visual Basic 的範例。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 5851492f075068337c60316664138dd09c97443b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552216"
---
# <a name="how-to-project-an-anonymous-type-linq-to-xml"></a>如何將匿名型別投影 (LINQ to XML) 

在某些情況下，您可能會想要將查詢投射至新的型別，但是查詢會是您只用于新型別的專案。 您可以投影至匿名型別，而不是建立型別。 匿名型別提供一個方便的方式，在物件中封裝一組唯讀屬性，而不需要先明確地定義型別。 如果您撰寫的查詢會在子句中建立匿名型別的物件 `select` ，則查詢會傳回 <xref:System.Collections.IEnumerable> 型別的。

下列範例顯示如何建立匿名型別的物件，該物件是以兩個屬性（property） `Amount` 和來初始化 `Message` 。

```csharp
var v = new { Amount = 108, Message = "Hello" };
```

```vb
Dim v = New With { .Amount = 108, .Message = "Hello" };
```

每個屬性的類型會由編譯器推斷。 型別名稱是由編譯器所產生，無法在原始程式碼層級使用。

如需匿名型別的詳細資訊，請參閱：

- [匿名類型 (C# 程式設計手冊)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [匿名類型 (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

## <a name="example-project-an-anonymous-type-by-creating-objects-in-the-select-clause"></a>範例：在子句中建立物件來投影匿名型別 `select`

在這個範例中，`select` 子句會規劃匿名型別。 然後，此範例會使用 `var` 來建立 `IEnumerable` 物件。 在 `foreach` 迴圈中，反覆運算變數會變成在查詢運算式中建立之匿名型別的執行個體。

此範例會使用 XML [檔範例 xml 檔：客戶和訂單](sample-xml-file-customers-orders.md)。

```csharp
XElement custOrd = XElement.Load("CustomersOrders.xml");
var custList =
    from el in custOrd.Element("Customers").Elements("Customer")
    select new {
        CustomerID = (string)el.Attribute("CustomerID"),
        CompanyName = (string)el.Element("CompanyName"),
        ContactName = (string)el.Element("ContactName")
    };
foreach (var cust in custList)
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);
```

```vb
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
Dim custList = _
    From el In custOrd.<Customers>.<Customer> _
    Select New With { _
        .CustomerID = el.@<CustomerID>, _
        .CompanyName = el.<CompanyName>.Value, _
        .ContactName = el.<ContactName>.Value _
    }
For Each cust In custList
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)
Next
```

這個範例會產生下列輸出：

```output
GREAL:Great Lakes Food Market:Howard Snyder
HUNGC:Hungry Coyote Import Store:Yoshi Latimer
LAZYK:Lazy K Kountry Store:John Steel
LETSS:Let's Stop N Shop:Jaime Yorres
```

## <a name="see-also"></a>另請參閱

- [匿名類型 (C# 程式設計手冊)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [匿名類型 (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
