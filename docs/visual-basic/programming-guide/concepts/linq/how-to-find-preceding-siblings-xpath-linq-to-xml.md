---
title: "如何︰ 尋找前一個同層級項目 (XPATH-LINQ to XML) (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8a6487d52e99bbf937439c902b59bf75bb67c8e4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b8e16-102">如何︰ 尋找前一個同層級項目 (XPATH-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8e16-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b8e16-103">本主題會比較 XPath`preceding-sibling`座標軸[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]子<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>軸。</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b8e16-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> axis.</span></span>  
  
 <span data-ttu-id="b8e16-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="b8e16-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="b8e16-105">請注意，這兩者的結果<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>和<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>為文件順序。</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> </xref:System.Xml.XPath.Extensions.XPathSelectElements%2A></span><span class="sxs-lookup"><span data-stu-id="b8e16-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e16-106">範例</span><span class="sxs-lookup"><span data-stu-id="b8e16-106">Example</span></span>  
 <span data-ttu-id="b8e16-107">下列範例會尋找 `FullAddress` 項目，然後使用 `preceding-sibling` 座標軸擷取先前的項目。</span><span class="sxs-lookup"><span data-stu-id="b8e16-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="b8e16-108">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e16-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b8e16-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b8e16-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8e16-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e16-110">See Also</span></span>  
 [<span data-ttu-id="b8e16-111">LINQ to XML 的 XPath 使用者 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8e16-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
