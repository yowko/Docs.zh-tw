---
title: 如何聯結兩個集合-LINQ to XML
description: 'XSD 檔案可以在 XML 檔案中建立關聯性，以啟用專案的聯結以建立新的元素類型。 本文提供 c # 和 Visual Basic 的範例，該範例會聯結元素並建立新的 XML 檔。'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2ab74f861cfd046e202a861378b8fd8792c7bac4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552243"
---
# <a name="how-to-join-two-collections-linq-to-xml"></a><span data-ttu-id="6b6c6-104">如何聯結兩個集合 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6b6c6-104">How to join two collections (LINQ to XML)</span></span>

<span data-ttu-id="6b6c6-105">XSD 檔案可以在 XML 檔案中建立關聯性，以啟用專案的聯結以建立新的元素類型。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-105">An XSD file can establish relationships in an XML file, to enable joining of elements to create new types of elements.</span></span> <span data-ttu-id="6b6c6-106">本文提供 c # 和 Visual Basic 的範例，該範例會聯結元素並建立新的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-106">This article provides an example for C# and Visual Basic that joins elements and creates a new XML document.</span></span>

<span data-ttu-id="6b6c6-107">XML 文件中的項目或屬性有時候會參考其他項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-107">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="6b6c6-108">例如，XML [檔範例 xml 檔：客戶和訂單](sample-xml-file-customers-orders.md) 包含客戶清單與訂單清單。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-108">For example, XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md) contains a list of customers and a list of orders.</span></span> <span data-ttu-id="6b6c6-109">每個 `Customer` 元素都有一個 `CustomerID` 屬性，而且每個元素都 `Order` 包含一個專案 `CustomerID` 。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-109">Every `Customer` element has a `CustomerID` attribute, and every `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="6b6c6-110">專案 `CustomerID` 中的元素值會 `Order` 參考 `Customer` 具有相符 `CustomerID` 屬性值的元素。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-110">The `CustomerID` element value in an `Order` element refers to the `Customer` element that has a matching `CustomerID` attribute value.</span></span>

<span data-ttu-id="6b6c6-111">發行項 [範例 xsd 檔案：客戶和訂單](sample-xsd-file-customers-orders.md) 包含可用於驗證檔的 xsd `Customers and orders` 。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-111">The article [Sample XSD file: Customers and orders](sample-xsd-file-customers-orders.md) contains an XSD that can be used to validate the `Customers and orders` document.</span></span> <span data-ttu-id="6b6c6-112">它會使用 `xs:key` XSD 的和 `xs:keyref` 功能來建立專案的 `CustomerID` 屬性是索引 `Customer` 鍵，以及建立專案的索引鍵和元素之間的關聯性 `CustomerID`  `Order` 。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-112">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the key and the `CustomerID` element of the  `Order`elements.</span></span>

<span data-ttu-id="6b6c6-113">使用 LINQ to XML，您可以使用 `join` 子句將客戶資訊加入訂單資訊，以利用此關聯性。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-113">With LINQ to XML, you can take advantage of this relationship by using the `join` clause to join customer information to order information.</span></span>

<span data-ttu-id="6b6c6-114">如需的詳細資訊 `join` ，請參閱 [ (c # ) ](../../csharp/programming-guide/concepts/linq/join-operations.md) 和 [聯結作業的聯結作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/join-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-114">For more detailed information about `join`, see [Join Operations (C#)](../../csharp/programming-guide/concepts/linq/join-operations.md) and [Join Operations (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>
> [!NOTE]
> <span data-ttu-id="6b6c6-115">聯結是使用線性搜尋來完成。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-115">Joins are done using linear searches.</span></span> <span data-ttu-id="6b6c6-116">沒有可提升搜尋效能的索引。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-116">There are no indexes to boost search performance.</span></span>

## <a name="example-create-a-new-xml-document-that-has-customer-and-order-elements-joined"></a><span data-ttu-id="6b6c6-117">範例：建立已 `Customer` 加入和元素的新 XML `Order` 檔</span><span class="sxs-lookup"><span data-stu-id="6b6c6-117">Example: Create a new XML document that has `Customer` and `Order` elements joined</span></span>

<span data-ttu-id="6b6c6-118">下列範例會產生新的 XML 檔，該檔會將範例 XML 檔的專案 `Customer` （ [客戶和訂單](sample-xml-file-customers-orders.md) ）加入至專案 `Order` ，並將專案包含 `CompanyName` 在訂單中。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-118">The following example generates a new XML document that joins the `Customer` elements of [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md) to the `Order` elements, and includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="6b6c6-119">在執行查詢之前，此範例會驗證檔是否符合 [範例 XSD 檔案：客戶和訂單](sample-xsd-file-customers-orders.md)中的架構。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-119">Before executing the query, the example validates that the document complies with the schema in [Sample XSD file: Customers and orders](sample-xsd-file-customers-orders.md).</span></span> <span data-ttu-id="6b6c6-120">這可確保 join 子句可正常運作。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-120">This ensures that the join clause will work.</span></span>

<span data-ttu-id="6b6c6-121">查詢只會針對 `CustomerID` 大於 "K" 的客戶選取訂單。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-121">The query selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="6b6c6-122">它會 `Order` 在每個訂單中投射包含客戶資訊的新元素。</span><span class="sxs-lookup"><span data-stu-id="6b6c6-122">It projects  new `Order` elements that contains the customer information within each order.</span></span>

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

```vb
Public Class Program
    Public Shared errors As Boolean = False

    Public Shared Function LamValidEvent(ByVal o As Object, _
                 ByVal e As ValidationEventArgs) As Boolean
        Console.WriteLine("{0}", e.Message)
        errors = True
    End Function

    Shared Sub Main()
        Dim schemas As New XmlSchemaSet()
        schemas.Add("", "CustomersOrders.xsd")

        Console.Write("Attempting to validate, ")
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")

        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))
        If errors Then
            Console.WriteLine("custOrdDoc did not validate")
        Else
            Console.WriteLine("custOrdDoc validated")
        End If

        If Not errors Then
            'Join customers and orders, and create a new XML document with
            ' a different shape.
            'The new document contains orders only for customers with a
            ' CustomerID > 'K'.
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault
            Dim newCustOrd As XElement = _
                <Root>
                    <%= From c In custOrd.<Customers>.<Customer> _
                        Join o In custOrd.<Orders>.<Order> _
                        On c.@CustomerID Equals o.<CustomerID>.Value _
                        Where c.@CustomerID.CompareTo("K") > 0 _
                        Select _
                        <Order>
                            <CustomerID><%= c.@CustomerID %></CustomerID>
                            <%= c.<CompanyName> %>
                            <%= c.<ContactName> %>
                            <%= o.<EmployeeID> %>
                            <%= o.<OrderDate> %>
                        </Order> _
                    %>
                </Root>
            Console.WriteLine(newCustOrd)
        End If
    End Sub
End Class
```

<span data-ttu-id="6b6c6-123">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="6b6c6-123">This example produces the following output:</span></span>

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
