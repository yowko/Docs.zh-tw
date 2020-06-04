---
title: 作法：控制投影的類型
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: 6b809188f68805afcca960bd809e079d997e79c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357253"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="8a177-102">如何：控制投射的類型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="8a177-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="8a177-103">投影使採用一組資料、進行篩選、變更其組織結構，甚至變更其型別的程序。</span><span class="sxs-lookup"><span data-stu-id="8a177-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="8a177-104">大部分的查詢運算式都會執行投影。</span><span class="sxs-lookup"><span data-stu-id="8a177-104">Most query expressions perform projections.</span></span> <span data-ttu-id="8a177-105">本節中所顯示的大部分查詢運算式會評估為 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，但是您可以控制投影的型別以建立其他型別的集合。</span><span class="sxs-lookup"><span data-stu-id="8a177-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="8a177-106">本主題顯示如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="8a177-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a177-107">範例</span><span class="sxs-lookup"><span data-stu-id="8a177-107">Example</span></span>  
 <span data-ttu-id="8a177-108">下列範例會定義新型別 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="8a177-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="8a177-109">接著，查詢運算式會在 `Customer` 子句中具現化新的 `Select` 物件。</span><span class="sxs-lookup"><span data-stu-id="8a177-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="8a177-110">這會造成查詢運算式的型別變成 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="8a177-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="8a177-111">此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="8a177-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="8a177-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8a177-112">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a177-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a177-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="8a177-114">投影和轉換（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="8a177-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
