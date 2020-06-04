---
title: 作法：尋找子系項目 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: e7e2dc9e-bda9-420d-a5b1-4fabf1cca46b
ms.openlocfilehash: ee67a54116a7d91f6cf6af179d6398a4dcece9c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405231"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="0becc-102">如何：尋找子代元素（XPath-LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0becc-102">How to: Find Descendant Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="0becc-103">本主題顯示如何利用特定名稱取得子代項目。</span><span class="sxs-lookup"><span data-stu-id="0becc-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="0becc-104">XPath 運算式為 `//Name`。</span><span class="sxs-lookup"><span data-stu-id="0becc-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0becc-105">範例</span><span class="sxs-lookup"><span data-stu-id="0becc-105">Example</span></span>  
 <span data-ttu-id="0becc-106">此範例會尋找名稱為 `Name` 的所有子代。</span><span class="sxs-lookup"><span data-stu-id="0becc-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="0becc-107">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="0becc-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
      Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po...<Name>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")  
  
If (list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="0becc-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0becc-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0becc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0becc-109">See also</span></span>

- [<span data-ttu-id="0becc-110">XPath 使用者的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0becc-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
