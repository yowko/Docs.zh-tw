---
title: '如何控制投射的類型（c #）'
description: '瞭解如何在 c # 中控制 LINQ 中投射的類型，以建立 System.xml.linq.xelement> 的 IEnumerable 以外的類型集合 <T> 。'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 32b019b5e1574e7160b4dce5fb0322caa3c1ca71
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103346"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="83435-103">如何控制投射的類型（c #）</span><span class="sxs-lookup"><span data-stu-id="83435-103">How to control the type of a projection (C#)</span></span>
<span data-ttu-id="83435-104">投影使採用一組資料、進行篩選、變更其組織結構，甚至變更其型別的程序。</span><span class="sxs-lookup"><span data-stu-id="83435-104">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="83435-105">大部分的查詢運算式都會執行投影。</span><span class="sxs-lookup"><span data-stu-id="83435-105">Most query expressions perform projections.</span></span> <span data-ttu-id="83435-106">本節中所顯示的大部分查詢運算式會評估為 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，但是您可以控制投影的型別以建立其他型別的集合。</span><span class="sxs-lookup"><span data-stu-id="83435-106">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="83435-107">本主題顯示如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="83435-107">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83435-108">範例</span><span class="sxs-lookup"><span data-stu-id="83435-108">Example</span></span>  
 <span data-ttu-id="83435-109">下列範例會定義新型別 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="83435-109">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="83435-110">接著，查詢運算式會在 `Customer` 子句中具現化新的 `Select` 物件。</span><span class="sxs-lookup"><span data-stu-id="83435-110">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="83435-111">這會造成查詢運算式的型別變成 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="83435-111">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="83435-112">此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="83435-112">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="83435-113">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="83435-113">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="83435-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83435-114">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
