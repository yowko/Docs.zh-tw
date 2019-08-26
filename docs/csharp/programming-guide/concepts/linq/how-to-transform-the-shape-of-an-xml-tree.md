---
title: 作法：轉換 XML 樹狀結構的組織結構 (C#)
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: c6f78decdcc32d202f4a0f1e51a012dce8aa7d6c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592229"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="23846-102">作法：轉換 XML 樹狀結構的組織結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="23846-102">How to: Transform the Shape of an XML Tree (C#)</span></span>
<span data-ttu-id="23846-103">XML 文件的「組織結構」  會參考其項目名稱、屬性名稱，及其階層的特性。</span><span class="sxs-lookup"><span data-stu-id="23846-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="23846-104">有時候您必須變更 XML 文件的組織結構。</span><span class="sxs-lookup"><span data-stu-id="23846-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="23846-105">例如，您可能想要將現有的 XML 文件傳送到需要不同項目和屬性名稱的其他系統。</span><span class="sxs-lookup"><span data-stu-id="23846-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="23846-106">您可以瀏覽文件，在必要時刪除並重新命名項目，但使用功能結構會使程式碼更容易讀取與維護。</span><span class="sxs-lookup"><span data-stu-id="23846-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="23846-107">如需函數式建構的詳細資訊，請參閱[函數式建構 (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="23846-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="23846-108">第一個範例會變更 XML 文件的組織。</span><span class="sxs-lookup"><span data-stu-id="23846-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="23846-109">此範例會在樹狀結構中，將複雜的項目從一個位置移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="23846-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="23846-110">本主題中的第二個範例會使用不同於來源文件的組織結構，建立 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="23846-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="23846-111">此範例會變更項目名稱的大小寫、重新命名某些項目，並將某些項目從來源樹狀排除在轉換的樹狀之外。</span><span class="sxs-lookup"><span data-stu-id="23846-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23846-112">範例</span><span class="sxs-lookup"><span data-stu-id="23846-112">Example</span></span>  
 <span data-ttu-id="23846-113">下列程式碼會使用內嵌的查詢運算式變更 XML 檔案的組織結構。</span><span class="sxs-lookup"><span data-stu-id="23846-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="23846-114">此範例中的 XML 來源文件包含的 `Customers` 項目在包含所有客戶的 `Root` 項目之下。</span><span class="sxs-lookup"><span data-stu-id="23846-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="23846-115">同時，它所包含的 `Orders` 項目在包含所有訂單的 `Root` 項目之下。</span><span class="sxs-lookup"><span data-stu-id="23846-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="23846-116">此範例會建立新的 XML 樹狀結構，其中每個客戶的訂單會包含在 `Orders` 項目的 `Customer` 項目中。</span><span class="sxs-lookup"><span data-stu-id="23846-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="23846-117">原始文件在 `CustomerID` 項目中也包含 `Order` 項目；這個項目將會從改變組織結構的文件中移除。</span><span class="sxs-lookup"><span data-stu-id="23846-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="23846-118">此範例使用下列 XML 文件：[XML 範例檔：客戶和訂單 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="23846-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="23846-119">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="23846-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="23846-120">範例</span><span class="sxs-lookup"><span data-stu-id="23846-120">Example</span></span>  
 <span data-ttu-id="23846-121">此範例會重新命名某些項目，並將某些屬性轉換為項目。</span><span class="sxs-lookup"><span data-stu-id="23846-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="23846-122">此程式馬會呼叫可傳回 `ConvertAddress` 物件之清單的 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="23846-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="23846-123">此方法的引數是一個查詢，可判斷 `Address` 屬性值為 `Type` 的 `"Shipping"` 複雜項目。</span><span class="sxs-lookup"><span data-stu-id="23846-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="23846-124">此範例使用下列 XML 文件：[XML 範例檔：典型訂購單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="23846-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="23846-125">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="23846-125">This code produces the following output:</span></span>  
  
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
