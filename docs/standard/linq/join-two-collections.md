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
# <a name="how-to-join-two-collections-linq-to-xml"></a>如何聯結兩個集合 (LINQ to XML)

XSD 檔案可以在 XML 檔案中建立關聯性，以啟用專案的聯結以建立新的元素類型。 本文提供 c # 和 Visual Basic 的範例，該範例會聯結元素並建立新的 XML 檔。

XML 文件中的項目或屬性有時候會參考其他項目或屬性。 例如，XML [檔範例 xml 檔：客戶和訂單](sample-xml-file-customers-orders.md) 包含客戶清單與訂單清單。 每個 `Customer` 元素都有一個 `CustomerID` 屬性，而且每個元素都 `Order` 包含一個專案 `CustomerID` 。 專案 `CustomerID` 中的元素值會 `Order` 參考 `Customer` 具有相符 `CustomerID` 屬性值的元素。

發行項 [範例 xsd 檔案：客戶和訂單](sample-xsd-file-customers-orders.md) 包含可用於驗證檔的 xsd `Customers and orders` 。 它會使用 `xs:key` XSD 的和 `xs:keyref` 功能來建立專案的 `CustomerID` 屬性是索引 `Customer` 鍵，以及建立專案的索引鍵和元素之間的關聯性 `CustomerID`  `Order` 。

使用 LINQ to XML，您可以使用 `join` 子句將客戶資訊加入訂單資訊，以利用此關聯性。

如需的詳細資訊 `join` ，請參閱 [ (c # ) ](../../csharp/programming-guide/concepts/linq/join-operations.md) 和 [聯結作業的聯結作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/join-operations.md)。
> [!NOTE]
> 聯結是使用線性搜尋來完成。 沒有可提升搜尋效能的索引。

## <a name="example-create-a-new-xml-document-that-has-customer-and-order-elements-joined"></a>範例：建立已 `Customer` 加入和元素的新 XML `Order` 檔

下列範例會產生新的 XML 檔，該檔會將範例 XML 檔的專案 `Customer` （ [客戶和訂單](sample-xml-file-customers-orders.md) ）加入至專案 `Order` ，並將專案包含 `CompanyName` 在訂單中。

在執行查詢之前，此範例會驗證檔是否符合 [範例 XSD 檔案：客戶和訂單](sample-xsd-file-customers-orders.md)中的架構。 這可確保 join 子句可正常運作。

查詢只會針對 `CustomerID` 大於 "K" 的客戶選取訂單。 它會 `Order` 在每個訂單中投射包含客戶資訊的新元素。

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

這個範例會產生下列輸出：

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
