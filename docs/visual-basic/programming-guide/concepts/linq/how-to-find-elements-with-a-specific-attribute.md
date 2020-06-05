---
title: 作法：尋找具有特定屬性的項目 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: 4b625fcccc834f860072ad92587bbfd7ed5ec4ad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364769"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="38fbe-102">如何：尋找具有特定屬性的元素（XPath-LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="38fbe-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="38fbe-103">有時候您會想要尋找具有特定屬性的所有項目。</span><span class="sxs-lookup"><span data-stu-id="38fbe-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="38fbe-104">您並不關心屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="38fbe-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="38fbe-105">但是，您想要根據屬性的存在與否來選擇。</span><span class="sxs-lookup"><span data-stu-id="38fbe-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="38fbe-106">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="38fbe-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="38fbe-107">範例</span><span class="sxs-lookup"><span data-stu-id="38fbe-107">Example</span></span>  
 <span data-ttu-id="38fbe-108">下列程式碼只會選取具有 `Select` 屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="38fbe-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
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
  
 <span data-ttu-id="38fbe-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="38fbe-109">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38fbe-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38fbe-110">See also</span></span>

- [<span data-ttu-id="38fbe-111">XPath 使用者的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="38fbe-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
