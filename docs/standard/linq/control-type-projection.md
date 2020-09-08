---
title: 如何控制投影的類型-LINQ to XML
description: 您可以控制您的查詢所傳回的集合類型;它不需要是 Xelement 的 IEnumerable。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: c4be649a5f35f7e9cbe65332a60b1c8aeb2a66ea
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552281"
---
# <a name="how-to-control-the-type-of-a-projection-linq-to-xml"></a>如何控制投影的類型 (LINQ to XML) 

*投射* 是篩選一組資料、變更其圖形（可能為其類型）的程式。 大部分的查詢運算式都會進行投影。 此區段中的大部分查詢運算式會評估為 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ，但您可以建立其他類型的集合。 本文說明如何進行這項操作。

## <a name="example-define-a-new-type-and-create-a-query-that-creates-an-ienumerable-of-that-type"></a>範例：定義新的型別，並建立可建立該型別之 IEnumerable 的查詢

下列範例會定義新的型別， `Customer` 而且查詢運算式會在子句中具現化新 `Customer` 的物件 `Select` 。 這會造成查詢運算式的型別變成 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。 此範例會使用 XML [檔範例 xml 檔：客戶和訂單](sample-xml-file-customers-orders.md)。

```csharp
public class Customer
{
    private string customerID;
    public string CustomerID{ get{return customerID;} set{customerID = value;}}

    private string companyName;
    public string CompanyName{ get{return companyName;} set{companyName = value;}}

    private string contactName;
    public string ContactName { get{return contactName;} set{contactName = value;}}

    public Customer(string customerID, string companyName, string contactName)
    {
        CustomerID = customerID;
        CompanyName = companyName;
        ContactName = contactName;
    }

    public override string ToString()
    {
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }
}

class Program
{
    static void Main(string[] args)
    {
        XElement custOrd = XElement.Load("CustomersOrders.xml");
        IEnumerable<Customer> custList =
            from el in custOrd.Element("Customers").Elements("Customer")
            select new Customer(
                (string)el.Attribute("CustomerID"),
                (string)el.Element("CompanyName"),
                (string)el.Element("ContactName")
            );
        foreach (Customer cust in custList)
            Console.WriteLine(cust);
    }


}
```

```vb
Public Class Customer
    Private customerIDValue As String
    Public Property CustomerID() As String
        Get
            Return customerIDValue
        End Get
        Set(ByVal value As String)
            customerIDValue = value
        End Set
    End Property

    Private companyNameValue As String
    Public Property CompanyName() As String
        Get
            Return companyNameValue
        End Get
        Set(ByVal value As String)
            companyNameValue = value
        End Set
    End Property

    Private contactNameValue As String
    Public Property ContactName() As String
        Get
            Return contactNameValue
        End Get
        Set(ByVal value As String)
            contactNameValue = value
        End Set
    End Property

    Public Sub New(ByVal customerID As String, _
                   ByVal companyName As String, _
                   ByVal contactName As String)
        CustomerIDValue = customerID
        CompanyNameValue = companyName
        ContactNameValue = contactName
    End Sub

    Public Overrides Function ToString() As String
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)
    End Function
End Class

Sub Main()
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
    Dim custList As IEnumerable(Of Customer) = _
        From el In custOrd.<Customers>.<Customer> _
        Select New Customer( _
            el.@<CustomerID>, _
            el.<CompanyName>.Value, _
            el.<ContactName>.Value _
        )
    For Each cust In custList
        Console.WriteLine(cust)
    Next
End Sub
```

這個範例會產生下列輸出：

```output
GREAL:Great Lakes Food Market:Howard Snyder
HUNGC:Hungry Coyote Import Store:Yoshi Latimer
LAZYK:Lazy K Kountry Store:John Steel
LETSS:Let's Stop N Shop:Jaime Yorres
```

## <a name="see-also"></a>另請參閱

- <xref:System.Linq.Enumerable.Select%2A>
- [投影和轉換 (LINQ to XML)  (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
