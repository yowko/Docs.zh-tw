---
title: '如何聯結兩個集合（LINQ to XML）（c #）'
description: '這個 c # 範例會將 LINQ to XML 中的專案聯結至其他元素，並產生新的 XML 檔。'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 10792ed4907e778b41821c9b32574bd8fc0ab35f
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104992"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="c3718-103">如何聯結兩個集合（LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="c3718-103">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="c3718-104">XML 文件中的項目或屬性有時候會參考其他項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="c3718-104">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="c3718-105">例如，[範例 XML 檔：客戶和訂單 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML 文件包含客戶清單與訂單清單。</span><span class="sxs-lookup"><span data-stu-id="c3718-105">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="c3718-106">每個 `Customer` 項目都包含一個 `CustomerID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c3718-106">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="c3718-107">每個 `Order` 項目都包含一個 `CustomerID` 項目。</span><span class="sxs-lookup"><span data-stu-id="c3718-107">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="c3718-108">每個訂單中的 `CustomerID` 項目都會參考客戶中的 `CustomerID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c3718-108">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="c3718-109">[範例 XSD 檔：客戶和訂單](./sample-xsd-file-customers-and-orders1.md)主題包含可用於驗證此文件的 XSD。</span><span class="sxs-lookup"><span data-stu-id="c3718-109">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="c3718-110">它會使用 XSD 的 `xs:key` 和 `xs:keyref` 功能來建立 `CustomerID` 項目的 `Customer` 屬性為索引鍵，並在每個 `CustomerID` 項目中的 `Order` 項目和每個 `CustomerID` 項目中的 `Customer` 屬性之間建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="c3718-110">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="c3718-111">利用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，您可以使用 `join` 子句來利用此關聯性。</span><span class="sxs-lookup"><span data-stu-id="c3718-111">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="c3718-112">因為沒有可用的索引，所以這類聯結將會有不佳的執行時間效能。</span><span class="sxs-lookup"><span data-stu-id="c3718-112">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="c3718-113">如需 `join` 的詳細資訊，請參閱[聯結作業 (C#)](./join-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="c3718-113">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="c3718-114">範例</span><span class="sxs-lookup"><span data-stu-id="c3718-114">Example</span></span>

<span data-ttu-id="c3718-115">下列範例會將 `Customer` 項目聯結到 `Order` 項目，並在訂單中產生包含 `CompanyName` 項目的新 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c3718-115">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="c3718-116">執行查詢前，此範例會驗證文件是否使用[範例 XSD 檔：客戶和訂單](./sample-xsd-file-customers-and-orders1.md)中的結構描述進行編譯。</span><span class="sxs-lookup"><span data-stu-id="c3718-116">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="c3718-117">這可確保聯結子句永遠可以運作。</span><span class="sxs-lookup"><span data-stu-id="c3718-117">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="c3718-118">此查詢會先擷取所有 `Customer` 項目，然後將這些項目聯結到 `Order` 項目。</span><span class="sxs-lookup"><span data-stu-id="c3718-118">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="c3718-119">它僅會選取 `CustomerID` 大於 "K" 之客戶的訂單。</span><span class="sxs-lookup"><span data-stu-id="c3718-119">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="c3718-120">接著，它會規劃包含每個訂單內客戶資訊的新 `Order` 項目。</span><span class="sxs-lookup"><span data-stu-id="c3718-120">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="c3718-121">此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="c3718-121">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="c3718-122">此範例使用下列 XSD 結構描述︰[範例 XSD 檔：客戶和訂單](./sample-xsd-file-customers-and-orders1.md)。</span><span class="sxs-lookup"><span data-stu-id="c3718-122">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="c3718-123">以這種方式加入將無法順利執行。</span><span class="sxs-lookup"><span data-stu-id="c3718-123">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="c3718-124">聯結會透過線性搜尋執行。</span><span class="sxs-lookup"><span data-stu-id="c3718-124">Joins are performed via a linear search.</span></span> <span data-ttu-id="c3718-125">沒有雜湊資料表或索引協助執行。</span><span class="sxs-lookup"><span data-stu-id="c3718-125">There are no hash tables or indexes to help with performance.</span></span>

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

<span data-ttu-id="c3718-126">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="c3718-126">This code produces the following output:</span></span>

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```
