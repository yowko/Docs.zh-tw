---
title: "如何：轉換 XML 樹狀結構的組織結構 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8f11c77bc6273642bc4ffce3bf546c5a897729bc
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>轉換 XML 樹狀結構的組織結構 (C#)
XML 文件的「組織結構」**會參考其項目名稱、屬性名稱，及其階層的特性。  
  
 有時候您必須變更 XML 文件的組織結構。 例如，您可能想要將現有的 XML 文件傳送到需要不同項目和屬性名稱的其他系統。 您可以瀏覽文件，在必要時刪除並重新命名項目，但使用功能結構會使程式碼更容易讀取與維護。 如需函數式建構的詳細資訊，請參閱[函數式建構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)。  
  
 第一個範例會變更 XML 文件的組織。 此範例會在樹狀結構中，將複雜的項目從一個位置移到另一個位置。  
  
 本主題中的第二個範例會使用不同於來源文件的組織結構，建立 XML 文件。 此範例會變更項目名稱的大小寫、重新命名某些項目，並將某些項目從來源樹狀排除在轉換的樹狀之外。  
  
## <a name="example"></a>範例  
 下列程式碼會使用內嵌的查詢運算式變更 XML 檔案的組織結構。  
  
 此範例中的 XML 來源文件包含的 `Customers` 項目在包含所有客戶的 `Root` 項目之下。 同時，它所包含的 `Orders` 項目在包含所有訂單的 `Root` 項目之下。 此範例會建立新的 XML 樹狀結構，其中每個客戶的訂單會包含在 `Orders` 項目的 `Customer` 項目中。 原始文件在 `CustomerID` 項目中也包含 `Order` 項目；這個項目將會從改變組織結構的文件中移除。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)。  
  
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
  
 此程式碼會產生下列輸出：  
  
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
  
## <a name="example"></a>範例  
 此範例會重新命名某些項目，並將某些屬性轉換為項目。  
  
 此程式碼會呼叫 `ConvertAddress`，以傳回 <xref:System.Xml.Linq.XElement> 物件清單。 此方法的引數是一個查詢，可判斷 `Address` 屬性值為 `Type` 的 `"Shipping"` 複雜項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。  
  
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
  
 此程式碼會產生下列輸出：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [投影和轉換 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
