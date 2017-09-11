---
title: "如何：控制投影的類型 (C#)"
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
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e681fbffe681237d0b0ac3d7a161180e478172f9
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="b269f-102">如何：控制投影的類型 (C#)</span><span class="sxs-lookup"><span data-stu-id="b269f-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="b269f-103">投影使採用一組資料、進行篩選、變更其組織結構，甚至變更其型別的程序。</span><span class="sxs-lookup"><span data-stu-id="b269f-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="b269f-104">大部分的查詢運算式都會執行投影。</span><span class="sxs-lookup"><span data-stu-id="b269f-104">Most query expressions perform projections.</span></span> <span data-ttu-id="b269f-105">本節中所顯示的大部分查詢運算式會評估為 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，但是您可以控制投影的型別以建立其他型別的集合。</span><span class="sxs-lookup"><span data-stu-id="b269f-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="b269f-106">本主題顯示如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="b269f-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b269f-107">範例</span><span class="sxs-lookup"><span data-stu-id="b269f-107">Example</span></span>  
 <span data-ttu-id="b269f-108">下列範例會定義新型別 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="b269f-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="b269f-109">接著，查詢運算式會在 `Customer` 子句中具現化新的 `Select` 物件。</span><span class="sxs-lookup"><span data-stu-id="b269f-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="b269f-110">這會造成查詢運算式的型別變成 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="b269f-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="b269f-111">此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="b269f-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
        return String.Format("{0}:{1}:{2}", this.customerID, this.companyName, this.contactName);  
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
  
 <span data-ttu-id="b269f-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b269f-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="b269f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b269f-113">See Also</span></span>  
 <span data-ttu-id="b269f-114"><xref:System.Linq.Enumerable.Select%2A></span><span class="sxs-lookup"><span data-stu-id="b269f-114"><xref:System.Linq.Enumerable.Select%2A></span></span>   
 [<span data-ttu-id="b269f-115">投影和轉換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b269f-115">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

