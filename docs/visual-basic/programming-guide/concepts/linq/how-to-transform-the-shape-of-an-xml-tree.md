---
title: HOW TO：「 轉換 」 圖形的 XML 樹狀結構 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 067bf56b8dff994080ba78147d992b97a56867cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833655"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="69eb9-102">HOW TO：「 轉換 」 圖形的 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69eb9-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="69eb9-103">XML 文件的「組織結構」會參考其項目名稱、屬性名稱，及其階層的特性。</span><span class="sxs-lookup"><span data-stu-id="69eb9-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="69eb9-104">有時候您必須變更 XML 文件的組織結構。</span><span class="sxs-lookup"><span data-stu-id="69eb9-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="69eb9-105">例如，您可能想要將現有的 XML 文件傳送到需要不同項目和屬性名稱的其他系統。</span><span class="sxs-lookup"><span data-stu-id="69eb9-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="69eb9-106">您可以瀏覽文件，在必要時刪除並重新命名項目，但使用功能結構會使程式碼更容易讀取與維護。</span><span class="sxs-lookup"><span data-stu-id="69eb9-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="69eb9-107">如需函數式建構的詳細資訊，請參閱[函數式建構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="69eb9-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="69eb9-108">第一個範例會變更 XML 文件的組織。</span><span class="sxs-lookup"><span data-stu-id="69eb9-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="69eb9-109">此範例會在樹狀結構中，將複雜的項目從一個位置移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="69eb9-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="69eb9-110">本主題中的第二個範例會使用不同於來源文件的組織結構，建立 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="69eb9-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="69eb9-111">此範例會變更項目名稱的大小寫、重新命名某些項目，並將某些項目從來源樹狀排除在轉換的樹狀之外。</span><span class="sxs-lookup"><span data-stu-id="69eb9-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69eb9-112">範例</span><span class="sxs-lookup"><span data-stu-id="69eb9-112">Example</span></span>  
 <span data-ttu-id="69eb9-113">下列程式碼會使用內嵌的查詢運算式變更 XML 檔案的組織結構。</span><span class="sxs-lookup"><span data-stu-id="69eb9-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="69eb9-114">此範例中的 XML 來源文件包含的 `Customers` 項目在包含所有客戶的 `Root` 項目之下。</span><span class="sxs-lookup"><span data-stu-id="69eb9-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="69eb9-115">同時，它所包含的 `Orders` 項目在包含所有訂單的 `Root` 項目之下。</span><span class="sxs-lookup"><span data-stu-id="69eb9-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="69eb9-116">此範例會建立新的 XML 樹狀結構，其中每個客戶的訂單會包含在 `Orders` 項目的 `Customer` 項目中。</span><span class="sxs-lookup"><span data-stu-id="69eb9-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="69eb9-117">原始文件在 `CustomerID` 項目中也包含 `Order` 項目；這個項目將會從改變組織結構的文件中移除。</span><span class="sxs-lookup"><span data-stu-id="69eb9-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="69eb9-118">此範例使用下列 XML 文件：[XML 範例檔：客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="69eb9-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="69eb9-119">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="69eb9-119">This code produces the following output:</span></span>  
  
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
. . .  
```  
  
## <a name="example"></a><span data-ttu-id="69eb9-120">範例</span><span class="sxs-lookup"><span data-stu-id="69eb9-120">Example</span></span>  
 <span data-ttu-id="69eb9-121">此範例會重新命名某些項目，並將某些屬性轉換為項目。</span><span class="sxs-lookup"><span data-stu-id="69eb9-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="69eb9-122">此程式馬會呼叫可傳回 `ConvertAddress` 物件之清單的 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="69eb9-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="69eb9-123">此方法的引數是一個查詢，可判斷 `Address` 屬性值為 `Type` 的 `"Shipping"` 複雜項目。</span><span class="sxs-lookup"><span data-stu-id="69eb9-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="69eb9-124">此範例使用下列 XML 文件：[XML 範例檔：典型訂購單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="69eb9-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="69eb9-125">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="69eb9-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69eb9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69eb9-126">See also</span></span>

- [<span data-ttu-id="69eb9-127">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69eb9-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
