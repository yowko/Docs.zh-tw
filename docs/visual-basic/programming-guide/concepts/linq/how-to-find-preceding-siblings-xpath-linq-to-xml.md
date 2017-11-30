---
title: "如何： 尋找前一個同層級 (XPATH-LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54d70c1bfb3f1c2d3882b7582f6a11682eea46a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="6a3f5-102">如何： 尋找前一個同層級 (XPATH-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a3f5-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="6a3f5-103">這個主題會比較 XPath `preceding-sibling` 座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 子系 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="6a3f5-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="6a3f5-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="6a3f5-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="6a3f5-105">請注意，<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 和 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 的結果都會以文件的順序排列。</span><span class="sxs-lookup"><span data-stu-id="6a3f5-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a3f5-106">範例</span><span class="sxs-lookup"><span data-stu-id="6a3f5-106">Example</span></span>  
 <span data-ttu-id="6a3f5-107">下列範例會尋找 `FullAddress` 項目，然後使用 `preceding-sibling` 座標軸擷取先前的項目。</span><span class="sxs-lookup"><span data-stu-id="6a3f5-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="6a3f5-108">此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="6a3f5-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim add As XElement = co.<Customers>.<Customer>. _  
        <FullAddress>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="6a3f5-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="6a3f5-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a3f5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a3f5-110">See Also</span></span>  
 [<span data-ttu-id="6a3f5-111">LINQ to XML (Visual Basic) 的 XPath 使用者適用的</span><span class="sxs-lookup"><span data-stu-id="6a3f5-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
