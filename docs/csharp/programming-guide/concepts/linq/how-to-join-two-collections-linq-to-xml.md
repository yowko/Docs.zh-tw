---
title: 作法：聯結兩個集合 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 893966f3b803b92efbc89a65870623f10195c85f
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485375"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="08f9c-102">作法：聯結兩個集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="08f9c-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="08f9c-103">XML 文件中的項目或屬性有時候會參考其他項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="08f9c-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="08f9c-104">例如，[XML 範例檔：客戶和訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML 文件包含客戶清單與訂單清單。</span><span class="sxs-lookup"><span data-stu-id="08f9c-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="08f9c-105">每個 `Customer` 項目都包含一個 `CustomerID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="08f9c-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="08f9c-106">每個 `Order` 項目都包含一個 `CustomerID` 項目。</span><span class="sxs-lookup"><span data-stu-id="08f9c-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="08f9c-107">每個訂單中的 `CustomerID` 項目都會參考客戶中的 `CustomerID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="08f9c-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="08f9c-108">[XSD 範例檔：客戶和訂單](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md)主題包含可用於驗證此文件的 XSD。</span><span class="sxs-lookup"><span data-stu-id="08f9c-108">The topic [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="08f9c-109">它會使用 XSD 的 `xs:key` 和 `xs:keyref` 功能來建立 `CustomerID` 項目的 `Customer` 屬性為索引鍵，並在每個 `CustomerID` 項目中的 `Order` 項目和每個 `CustomerID` 項目中的 `Customer` 屬性之間建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="08f9c-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="08f9c-110">利用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，您可以使用 `join` 子句來利用此關聯性。</span><span class="sxs-lookup"><span data-stu-id="08f9c-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="08f9c-111">請注意，因為沒有可用的索引，所以這種聯結的執行階段效能會比較差。</span><span class="sxs-lookup"><span data-stu-id="08f9c-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="08f9c-112">如需 `join` 的詳細資訊，請參閱[聯結作業 (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="08f9c-112">For more detailed information about `join`, see [Join Operations (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08f9c-113">範例</span><span class="sxs-lookup"><span data-stu-id="08f9c-113">Example</span></span>  
 <span data-ttu-id="08f9c-114">下列範例會將 `Customer` 項目聯結到 `Order` 項目，並在訂單中產生包含 `CompanyName` 項目的新 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="08f9c-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="08f9c-115">執行查詢之前，此範例會驗證文件是否符合[XSD 範例檔：客戶和訂單](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md)中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="08f9c-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="08f9c-116">這可確保聯結子句永遠可以運作。</span><span class="sxs-lookup"><span data-stu-id="08f9c-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="08f9c-117">此查詢會先擷取所有 `Customer` 項目，然後將這些項目聯結到 `Order` 項目。</span><span class="sxs-lookup"><span data-stu-id="08f9c-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="08f9c-118">它僅會選取 `CustomerID` 大於 "K" 之客戶的訂單。</span><span class="sxs-lookup"><span data-stu-id="08f9c-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="08f9c-119">接著，它會規劃包含每個訂單內客戶資訊的新 `Order` 項目。</span><span class="sxs-lookup"><span data-stu-id="08f9c-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="08f9c-120">此範例使用下列 XML 文件：[XML 範例檔：客戶和訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="08f9c-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="08f9c-121">此範例使用下列 XSD 結構描述：[XSD 範例檔：客戶和訂單](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md)。</span><span class="sxs-lookup"><span data-stu-id="08f9c-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="08f9c-122">請注意，以這種方式聯結的效能不會很好。</span><span class="sxs-lookup"><span data-stu-id="08f9c-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="08f9c-123">聯結會透過線性搜尋執行。</span><span class="sxs-lookup"><span data-stu-id="08f9c-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="08f9c-124">沒有雜湊資料表或索引協助執行。</span><span class="sxs-lookup"><span data-stu-id="08f9c-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="08f9c-125">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="08f9c-125">This code produces the following output:</span></span>  
  
```  
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
