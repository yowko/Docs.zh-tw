---
title: 作法：尋找子項目清單 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 2868abfd-9f7b-412a-9cb5-f643f0fed146
ms.openlocfilehash: d03b89f93fede3abd2d482c01979e93876d60c0b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410769"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="7ecbc-102">如何：尋找子項目的清單（XPath-LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7ecbc-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7ecbc-103">本主題會比較 XPath 子專案座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="7ecbc-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="7ecbc-104">XPath 運算式為：`./*`</span><span class="sxs-lookup"><span data-stu-id="7ecbc-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ecbc-105">範例</span><span class="sxs-lookup"><span data-stu-id="7ecbc-105">Example</span></span>  
 <span data-ttu-id="7ecbc-106">此範例會尋找 `Address` 項目的所有子項目。</span><span class="sxs-lookup"><span data-stu-id="7ecbc-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="7ecbc-107">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecbc-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po.Elements()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")  
  
If (list1.Count() = list2.Count()) AndAlso _  
    (list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="7ecbc-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7ecbc-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ecbc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ecbc-109">See also</span></span>

- [<span data-ttu-id="7ecbc-110">XPath 使用者的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7ecbc-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
