---
title: HOW TO：尋找具有特定屬性 (XPATH-LINQ to XML) 項目 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: 17c5e9abf607df7311ff2552b7e9c54cbf30fd59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780480"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="857b1-102">HOW TO：尋找具有特定屬性 (XPATH-LINQ to XML) 項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857b1-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="857b1-103">有時候您會想要尋找具有特定屬性的所有項目。</span><span class="sxs-lookup"><span data-stu-id="857b1-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="857b1-104">您並不關心屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="857b1-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="857b1-105">但是，您想要根據屬性的存在與否來選擇。</span><span class="sxs-lookup"><span data-stu-id="857b1-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="857b1-106">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="857b1-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="857b1-107">範例</span><span class="sxs-lookup"><span data-stu-id="857b1-107">Example</span></span>  
 <span data-ttu-id="857b1-108">下列程式碼只會選取具有 `Select` 屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="857b1-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
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
  
 <span data-ttu-id="857b1-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="857b1-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="857b1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="857b1-110">See also</span></span>

- [<span data-ttu-id="857b1-111">LINQ to XML (Visual Basic) 的 XPath 使用者適用的</span><span class="sxs-lookup"><span data-stu-id="857b1-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
