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
# <a name="how-to-control-the-type-of-a-projection-c"></a>如何控制投射的類型（c #）
投影使採用一組資料、進行篩選、變更其組織結構，甚至變更其型別的程序。 大部分的查詢運算式都會執行投影。 本節中所顯示的大部分查詢運算式會評估為 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，但是您可以控制投影的型別以建立其他型別的集合。 本主題顯示如何執行此動作。  
  
## <a name="example"></a>範例  
 下列範例會定義新型別 `Customer`。 接著，查詢運算式會在 `Customer` 子句中具現化新的 `Select` 物件。 這會造成查詢運算式的型別變成 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)。  
  
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
  
 此程式碼會產生下列輸出：  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.Enumerable.Select%2A>
