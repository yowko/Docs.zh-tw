---
title: "如何︰ 尋找具有特定屬性 (XPATH-LINQ to XML) 項目 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 2819f0e9789218d3c2658d7c46c2d97f065ac23b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="bec24-102">如何︰ 尋找具有特定屬性 (XPATH-LINQ to XML) 項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bec24-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bec24-103">有時候您會想要尋找具有特定屬性的所有項目。</span><span class="sxs-lookup"><span data-stu-id="bec24-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="bec24-104">您並不關心屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="bec24-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="bec24-105">但是，您想要根據屬性的存在與否來選擇。</span><span class="sxs-lookup"><span data-stu-id="bec24-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="bec24-106">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="bec24-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="bec24-107">範例</span><span class="sxs-lookup"><span data-stu-id="bec24-107">Example</span></span>  
 <span data-ttu-id="bec24-108">下列程式碼只會選取具有 `Select` 屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="bec24-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```vb  
Dim doc As XElement = _   
    <Root>  
        <Child1>1</Child1>  
        <Child2 Select='true'>2</Child2>  
        <Child3>3</Child3>  
        <Child4 Select='true'>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In doc.Elements() _  
    Where el.@Select <> Nothing _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _  
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()  
  
If list1.Count() = list2.Count() And _  
    list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="bec24-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bec24-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bec24-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bec24-110">See Also</span></span>  
 [<span data-ttu-id="bec24-111">LINQ to XML 的 XPath 使用者 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bec24-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

