---
title: 如何尋找相關元素-LINQ to XML
description: '瞭解如何在 c # 和 Visual Basic 中使用 LINQ to XML 查詢和 XPath，以找出一個專案的值，以及其屬性具有相同值的元素。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: 7b39e8aef6409a51b0691cb9a9d09839e609a41c
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552189"
---
# <a name="how-to-find-related-elements-linq-to-xml"></a><span data-ttu-id="83a9a-103">如何尋找 (LINQ to XML) 的相關元素</span><span class="sxs-lookup"><span data-stu-id="83a9a-103">How to find related elements (LINQ to XML)</span></span>

<span data-ttu-id="83a9a-104">本文說明如何在 c # 和 Visual Basic 中使用 LINQ to XML 查詢和 XPath，以找出一個專案的值，以及其屬性具有相同值的元素。</span><span class="sxs-lookup"><span data-stu-id="83a9a-104">This article shows how to use LINQ to XML query and XPath, in C# and Visual Basic, to find the value of one element and an element whose attribute has the same value.</span></span>

## <a name="example-find-the-value-of-one-element-and-an-element-whose-attribute-has-the-same-value"></a><span data-ttu-id="83a9a-105">範例：尋找某個專案的值，以及其屬性具有相同值的元素</span><span class="sxs-lookup"><span data-stu-id="83a9a-105">Example: Find the value of one element and an element whose attribute has the same value</span></span>

<span data-ttu-id="83a9a-106">此範例會尋找 `Order` xml 檔範例 xml 檔中的第12個元素 [：客戶和訂單](sample-xml-file-customers-orders.md)，然後尋找該訂單的客戶。</span><span class="sxs-lookup"><span data-stu-id="83a9a-106">This example finds the 12th `Order` element in XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), and then finds the customer for that order.</span></span> <span data-ttu-id="83a9a-107">XPath 運算式為 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`。</span><span class="sxs-lookup"><span data-stu-id="83a9a-107">The XPath expression is `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`.</span></span>

> [!NOTE]
> <span data-ttu-id="83a9a-108">在 .NET 中，索引編制清單是以零為基底;也就是說，索引0是指初始元素。</span><span class="sxs-lookup"><span data-stu-id="83a9a-108">In .NET, the indexing into a list is zero-based; that is, an index of 0 refers to the initial element.</span></span> <span data-ttu-id="83a9a-109">在 XPath 述詞的節點集合中編制索引是以一為基礎。</span><span class="sxs-lookup"><span data-stu-id="83a9a-109">Indexing into a collection of nodes in an XPath predicate is one-based.</span></span> <span data-ttu-id="83a9a-110">此範例會針對此差異進行帳戶。</span><span class="sxs-lookup"><span data-stu-id="83a9a-110">This example accounts for this difference.</span></span>

```csharp
XDocument co = XDocument.Load("CustomersOrders.xml");

// LINQ to XML query
XElement customer1 =
    (from el in co.Descendants("Customer")
     where (string)el.Attribute("CustomerID") ==
          (string)(co
              .Element("Root")
              .Element("Orders")
              .Elements("Order")
              .ToList()[11]
              .Element("CustomerID"))
    select el)
    .First();

// An alternate way to write the query that avoids creation
// of a System.Collections.Generic.List:
XElement customer2 =
    (from el in co.Descendants("Customer")
     where (string)el.Attribute("CustomerID") ==
          (string)(co
              .Element("Root")
              .Element("Orders")
              .Elements("Order")
              .Skip(11).First()
              .Element("CustomerID"))
    select el)
    .First();

// XPath expression
XElement customer3 = co.XPathSelectElement(
  ".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]");

if (customer1 == customer2 && customer1 == customer3)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(customer1);
```

```vb
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")

' LINQ to XML query
Dim customer1 As XElement = ( _
    From el In co...<Customer> _
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _
        ToList()(11).<CustomerID>(0).Value _
    Select el).First()

' An alternate way to write the query that avoids creation
' of a System.Collections.Generic.List:
Dim customer2 As XElement = ( _
    From el In co...<Customer> _
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _
        Skip(11).First().<CustomerID>(0).Value _
    Select el).First()

' XPath expression
Dim customer3 As XElement = co.XPathSelectElement _
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")

If customer1 Is customer2 And customer1 Is customer3 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(customer1)
```

<span data-ttu-id="83a9a-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="83a9a-111">This example produces the following output:</span></span>

```output
Results are identical
<Customer CustomerID="HUNGC">
  <CompanyName>Hungry Coyote Import Store</CompanyName>
  <ContactName>Yoshi Latimer</ContactName>
  <ContactTitle>Sales Representative</ContactTitle>
  <Phone>(503) 555-6874</Phone>
  <Fax>(503) 555-2376</Fax>
  <FullAddress>
    <Address>City Center Plaza 516 Main St.</Address>
    <City>Elgin</City>
    <Region>OR</Region>
    <PostalCode>97827</PostalCode>
    <Country>USA</Country>
  </FullAddress>
</Customer>
```

## <a name="see-also"></a><span data-ttu-id="83a9a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83a9a-112">See also</span></span>

- [<span data-ttu-id="83a9a-113">XPath 使用者的 LINQ to XML (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="83a9a-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
