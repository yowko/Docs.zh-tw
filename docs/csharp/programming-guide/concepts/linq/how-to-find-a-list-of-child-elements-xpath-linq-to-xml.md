---
title: 如何：尋找子項目清單 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: 445d206577e45b7db9900e187f5bea3a7e18c715
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43735733"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="a7a76-102">如何：尋找子項目清單 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a7a76-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="a7a76-103">這個主題會比較 XPath 子項目座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="a7a76-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="a7a76-104">XPath 運算式為：`./*`</span><span class="sxs-lookup"><span data-stu-id="a7a76-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7a76-105">範例</span><span class="sxs-lookup"><span data-stu-id="a7a76-105">Example</span></span>  
 <span data-ttu-id="a7a76-106">此範例會尋找 `Address` 項目的所有子項目。</span><span class="sxs-lookup"><span data-stu-id="a7a76-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="a7a76-107">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a7a76-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Elements();  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="a7a76-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a7a76-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7a76-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7a76-109">See Also</span></span>

- [<span data-ttu-id="a7a76-110">XPath 使用者適用的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a7a76-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
