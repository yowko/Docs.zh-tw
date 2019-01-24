---
title: HOW TO：控制投影 (Visual Basic) 的類型
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: e892e6328576a9727a13a4c1acd951d44ce4daa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628869"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="59e88-102">HOW TO：控制投影 (Visual Basic) 的類型</span><span class="sxs-lookup"><span data-stu-id="59e88-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="59e88-103">投影使採用一組資料、進行篩選、變更其組織結構，甚至變更其型別的程序。</span><span class="sxs-lookup"><span data-stu-id="59e88-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="59e88-104">大部分的查詢運算式都會執行投影。</span><span class="sxs-lookup"><span data-stu-id="59e88-104">Most query expressions perform projections.</span></span> <span data-ttu-id="59e88-105">本節中所顯示的大部分查詢運算式會評估為 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，但是您可以控制投影的型別以建立其他型別的集合。</span><span class="sxs-lookup"><span data-stu-id="59e88-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="59e88-106">本主題顯示如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="59e88-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59e88-107">範例</span><span class="sxs-lookup"><span data-stu-id="59e88-107">Example</span></span>  
 <span data-ttu-id="59e88-108">下列範例會定義新型別 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="59e88-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="59e88-109">接著，查詢運算式會在 `Customer` 子句中具現化新的 `Select` 物件。</span><span class="sxs-lookup"><span data-stu-id="59e88-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="59e88-110">這會造成查詢運算式的型別變成 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="59e88-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="59e88-111">此範例使用下列 XML 文件：[範例 XML 檔：客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="59e88-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="59e88-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="59e88-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="59e88-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59e88-113">See also</span></span>
- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="59e88-114">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59e88-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
