---
title: "如何： 轉換 XML 樹狀結構 (Visual Basic) 的圖形"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cad7e5fc53b59593cf0c367d65d5bd44564bb1c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a>如何： 轉換 XML 樹狀結構 (Visual Basic) 的圖形
XML 文件的「組織結構」會參考其項目名稱、屬性名稱，及其階層的特性。  
  
 有時候您必須變更 XML 文件的組織結構。 例如，您可能想要將現有的 XML 文件傳送到需要不同項目和屬性名稱的其他系統。 您可以瀏覽文件，在必要時刪除並重新命名項目，但使用功能結構會使程式碼更容易讀取與維護。 如需功能結構的詳細資訊，請參閱[功能建構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)。  
  
 第一個範例會變更 XML 文件的組織。 此範例會在樹狀結構中，將複雜的項目從一個位置移到另一個位置。  
  
 本主題中的第二個範例會使用不同於來源文件的組織結構，建立 XML 文件。 此範例會變更項目名稱的大小寫、重新命名某些項目，並將某些項目從來源樹狀排除在轉換的樹狀之外。  
  
## <a name="example"></a>範例  
 下列程式碼會使用內嵌的查詢運算式變更 XML 檔案的組織結構。  
  
 此範例中的 XML 來源文件包含的 `Customers` 項目在包含所有客戶的 `Root` 項目之下。 同時，它所包含的 `Orders` 項目在包含所有訂單的 `Root` 項目之下。 此範例會建立新的 XML 樹狀結構，其中每個客戶的訂單會包含在 `Orders` 項目的 `Customer` 項目中。 原始文件在 `CustomerID` 項目中也包含 `Order` 項目；這個項目將會從改變組織結構的文件中移除。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。  
  
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
  
 此程式馬會呼叫可傳回 `ConvertAddress` 物件之清單的 <xref:System.Xml.Linq.XElement>。 此方法的引數是一個查詢，可判斷 `Address` 屬性值為 `Type` 的 `"Shipping"` 複雜項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)。  
  
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
 [投影和轉換 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
