---
title: 如何轉換 XML 樹狀結構的形狀-LINQ to XML
description: 您可以使用功能結構來變更 XML 檔的形狀;也就是說，若要保留資料，但變更專案名稱、屬性名稱和階層等專案。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 6b4127571d5a6a9fa8e92079424dd19eaf5a2f29
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552179"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-linq-to-xml"></a><span data-ttu-id="e65a1-103">如何將 XML 樹狀結構的圖形轉換 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="e65a1-103">How to transform the shape of an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="e65a1-104">XML 文件的「組織結構」\*\* 會參考其項目名稱、屬性名稱，及其階層的特性。</span><span class="sxs-lookup"><span data-stu-id="e65a1-104">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>

<span data-ttu-id="e65a1-105">有時候您必須變更 XML 文件的組織結構。</span><span class="sxs-lookup"><span data-stu-id="e65a1-105">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="e65a1-106">例如，您可能想要將現有的 XML 文件傳送到需要不同項目和屬性名稱的其他系統。</span><span class="sxs-lookup"><span data-stu-id="e65a1-106">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="e65a1-107">您可以瀏覽文件，在必要時刪除並重新命名項目，但使用功能結構會使程式碼更容易讀取與維護。</span><span class="sxs-lookup"><span data-stu-id="e65a1-107">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="e65a1-108">如需功能結構的詳細資訊，請參閱 [功能結構](functional-construction.md)。</span><span class="sxs-lookup"><span data-stu-id="e65a1-108">For more information about functional construction, see [Functional construction](functional-construction.md).</span></span>

<span data-ttu-id="e65a1-109">本文中的第一個範例會變更 XML 檔的組織。</span><span class="sxs-lookup"><span data-stu-id="e65a1-109">The first example in this article changes the organization of an XML document.</span></span> <span data-ttu-id="e65a1-110">此範例會在樹狀結構中，將複雜的項目從一個位置移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="e65a1-110">It moves complex elements from one location in the tree to another.</span></span>

<span data-ttu-id="e65a1-111">第二個範例會建立一個 XML 檔，其圖形與來源文件的不同。</span><span class="sxs-lookup"><span data-stu-id="e65a1-111">The second example creates an XML document whose shape differs from that of the source document.</span></span> <span data-ttu-id="e65a1-112">它會省略一些元素、將其他專案重新命名，以及變更元素名稱的大小寫。</span><span class="sxs-lookup"><span data-stu-id="e65a1-112">It omits some elements, renames others, and changes the casing of the element names.</span></span>

## <a name="example-use-embedded-query-expressions-to-change-the-shape-of-an-xml-tree"></a><span data-ttu-id="e65a1-113">範例：使用內嵌查詢運算式來變更 XML 樹狀結構的形狀</span><span class="sxs-lookup"><span data-stu-id="e65a1-113">Example: Use embedded query expressions to change the shape of an XML tree</span></span>

<span data-ttu-id="e65a1-114">下列範例會使用內嵌查詢運算式來變更 XML 檔案的圖形。</span><span class="sxs-lookup"><span data-stu-id="e65a1-114">The following example changes the shape of an XML file using embedded query expressions.</span></span>

<span data-ttu-id="e65a1-115">此範例的來源 XML [檔（範例 xml 檔：客戶和訂單](sample-xml-file-customers-orders.md)）包含元素底下 `Customers` `Root` 包含所有客戶的專案。</span><span class="sxs-lookup"><span data-stu-id="e65a1-115">The source XML document for this example, [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="e65a1-116">同時，它所包含的 `Orders` 項目在包含所有訂單的 `Root` 項目之下。</span><span class="sxs-lookup"><span data-stu-id="e65a1-116">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="e65a1-117">此範例會建立新的 XML 樹狀結構，其中每個客戶的訂單都會包含在專案 `Orders` 內的元素中 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="e65a1-117">The example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="e65a1-118">原始檔案也 `CustomerID` 會在專案中包含元素 `Order` ; 新樹狀結構中會省略這個元素。</span><span class="sxs-lookup"><span data-stu-id="e65a1-118">The original document also contains a `CustomerID` element in the `Order` element; this element is omitted from the new tree.</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");
XElement newCustOrd =
    new XElement("Root",
        from cust in co.Element("Customers").Elements("Customer")
        select new XElement("Customer",
            cust.Attributes(),
            cust.Elements(),
            new XElement("Orders",
                from ord in co.Element("Orders").Elements("Order")
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")
                select new XElement("Order",
                    ord.Attributes(),
                    ord.Element("EmployeeID"),
                    ord.Element("OrderDate"),
                    ord.Element("RequiredDate"),
                    ord.Element("ShipInfo")
                )
            )
        )
    );
Console.WriteLine(newCustOrd);
```

 ```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim newCustOrd = _
    <Root>
        <%= From cust In co.<Customers>.<Customer> _
            Select _
            <Customer>
                <%= cust.Attributes() %>
                <%= cust.Elements() %>
                <Orders>
                    <%= From ord In co.<Orders>.<Order> _
                        Where ord.<CustomerID>.Value = cust.@CustomerID _
                        Select _
                        <Order>
                            <%= ord.Attributes() %>
                            <%= ord.<EmployeeID> %>
                            <%= ord.<OrderDate> %>
                            <%= ord.<RequiredDate> %>
                            <%= ord.<ShipInfo> %>
                        </Order> _
                    %>
                </Orders>
            </Customer> _
        %>
    </Root>
Console.WriteLine(newCustOrd)
```

<span data-ttu-id="e65a1-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e65a1-119">This example produces the following output:</span></span>

```xml
<Root>
  <Customer CustomerID="GREAL">
    <CompanyName>Great Lakes Food Market</CompanyName>
    <ContactName>Howard Snyder</ContactName>
    <ContactTitle>Marketing Manager</ContactTitle>
    <Phone>(503) 555-7555</Phone>
    <FullAddress>
      <Address>2732 Baker Blvd.</Address>
      <City>Eugene</City>
      <Region>OR</Region>
      <PostalCode>97403</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
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
    <Orders />
  </Customer>
  ...
</Root>
```

## <a name="example-create-a-document-whose-shape-differs-from-that-of-the-source-document"></a><span data-ttu-id="e65a1-120">範例：建立其圖形與來源文件不同的檔</span><span class="sxs-lookup"><span data-stu-id="e65a1-120">Example: Create a document whose shape differs from that of the source document</span></span>

<span data-ttu-id="e65a1-121">此範例會重新命名某些項目，並將某些屬性轉換為項目。</span><span class="sxs-lookup"><span data-stu-id="e65a1-121">This example renames some elements and converts some attributes to elements.</span></span> <span data-ttu-id="e65a1-122">它會呼叫，它會傳回 `ConvertAddress` 物件的清單 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="e65a1-122">It calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e65a1-123">此方法的引數是一個查詢，可判斷 `Address` 屬性值為 `Type` 的 `"Shipping"` 複雜項目。</span><span class="sxs-lookup"><span data-stu-id="e65a1-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span> <span data-ttu-id="e65a1-124">此範例會使用 XML [檔範例 xml 檔：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。</span><span class="sxs-lookup"><span data-stu-id="e65a1-124">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
static IEnumerable<XElement> ConvertAddress(XElement add)
{
    List<XElement> fragment = new List<XElement>() {
        new XElement("NAME", (string)add.Element("Name")),
        new XElement("STREET", (string)add.Element("Street")),
        new XElement("CITY", (string)add.Element("City")),
        new XElement("ST", (string)add.Element("State")),
        new XElement("POSTALCODE", (string)add.Element("Zip")),
        new XElement("COUNTRY", (string)add.Element("Country"))
    };
    return fragment;
}

static void Main(string[] args)
{
    XElement po = XElement.Load("PurchaseOrder.xml");
    XElement newPo = new XElement("PO",
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),
        ConvertAddress(
            (from el in po.Elements("Address")
            where (string)el.Attribute("Type") == "Shipping"
            select el)
            .First()
        )
    );
    Console.WriteLine(newPo);
}
```

```vb
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)
    Dim fragment = New List(Of XElement)
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)
    fragment.Add(<ST><%= add.<State>.Value %></ST>)
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)
    Return fragment
End Function

Sub Main()
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")
    Dim newPo As XElement = _
        <PO>
            <ID><%= po.@PurchaseOrderNumber %></ID>
            <DATE><%= CDate(po.@OrderDate) %></DATE>
            <%= _
                ConvertAddress( _
                (From el In po.<Address> _
                Where el.@Type = "Shipping" _
                Select el) _
                .First() _
                ) _
            %>
        </PO>
    Console.WriteLine(newPo)
End Sub
```

<span data-ttu-id="e65a1-125">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e65a1-125">This example produces the following output:</span></span>

```xml
<PO>
  <ID>99503</ID>
  <DATE>1999-10-20T00:00:00</DATE>
  <NAME>Ellen Adams</NAME>
  <STREET>123 Maple Street</STREET>
  <CITY>Mill Valley</CITY>
  <ST>CA</ST>
  <POSTALCODE>10999</POSTALCODE>
  <COUNTRY>USA</COUNTRY>
</PO>
```

## <a name="see-also"></a><span data-ttu-id="e65a1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e65a1-126">See also</span></span>

- [<span data-ttu-id="e65a1-127">投影和轉換 (LINQ to XML)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="e65a1-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
