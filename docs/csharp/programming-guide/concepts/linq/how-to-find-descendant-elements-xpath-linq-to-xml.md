---
title: 如何：尋找子系項目 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: df1b151948b7b11757f2f8f312fa1f0bba00673a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580638"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="fddfb-102">如何：尋找子系項目 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fddfb-102">How to: Find Descendant Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="fddfb-103">本主題顯示如何利用特定名稱取得子代項目。</span><span class="sxs-lookup"><span data-stu-id="fddfb-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="fddfb-104">XPath 運算式為 `//Name`。</span><span class="sxs-lookup"><span data-stu-id="fddfb-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fddfb-105">範例</span><span class="sxs-lookup"><span data-stu-id="fddfb-105">Example</span></span>  
 <span data-ttu-id="fddfb-106">此範例會尋找名稱為 `Name` 的所有子代。</span><span class="sxs-lookup"><span data-stu-id="fddfb-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="fddfb-107">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="fddfb-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="fddfb-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fddfb-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fddfb-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="fddfb-109">See Also</span></span>

- [<span data-ttu-id="fddfb-110">XPath 使用者適用的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fddfb-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
