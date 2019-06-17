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
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>作法：聯結兩個集合 (LINQ to XML) (C#)
XML 文件中的項目或屬性有時候會參考其他項目或屬性。 例如，[XML 範例檔：客戶和訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML 文件包含客戶清單與訂單清單。 每個 `Customer` 項目都包含一個 `CustomerID` 屬性。 每個 `Order` 項目都包含一個 `CustomerID` 項目。 每個訂單中的 `CustomerID` 項目都會參考客戶中的 `CustomerID` 屬性。  
  
 [XSD 範例檔：客戶和訂單](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md)主題包含可用於驗證此文件的 XSD。 它會使用 XSD 的 `xs:key` 和 `xs:keyref` 功能來建立 `CustomerID` 項目的 `Customer` 屬性為索引鍵，並在每個 `CustomerID` 項目中的 `Order` 項目和每個 `CustomerID` 項目中的 `Customer` 屬性之間建立關聯性。  
  
 利用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，您可以使用 `join` 子句來利用此關聯性。  
  
 請注意，因為沒有可用的索引，所以這種聯結的執行階段效能會比較差。  
  
 如需 `join` 的詳細資訊，請參閱[聯結作業 (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)。  
  
## <a name="example"></a>範例  
 下列範例會將 `Customer` 項目聯結到 `Order` 項目，並在訂單中產生包含 `CompanyName` 項目的新 XML 文件。  
  
 執行查詢之前，此範例會驗證文件是否符合[XSD 範例檔：客戶和訂單](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md)中的結構描述。 這可確保聯結子句永遠可以運作。  
  
 此查詢會先擷取所有 `Customer` 項目，然後將這些項目聯結到 `Order` 項目。 它僅會選取 `CustomerID` 大於 "K" 之客戶的訂單。 接著，它會規劃包含每個訂單內客戶資訊的新 `Order` 項目。  
  
 此範例使用下列 XML 文件：[XML 範例檔：客戶和訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)。  
  
 此範例使用下列 XSD 結構描述：[XSD 範例檔：客戶和訂單](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md)。  
  
 請注意，以這種方式聯結的效能不會很好。 聯結會透過線性搜尋執行。 沒有雜湊資料表或索引協助執行。  
  
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
  
 此程式碼會產生下列輸出：  
  
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
