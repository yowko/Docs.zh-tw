---
title: "如何：尋找具有特定屬性的項目 (XPath-LINQ to XML) (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fec0b9a4dc5cee0f10f1675f1b8b281c40be7f21
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="7bbac-102">如何：尋找具有特定屬性的項目 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7bbac-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="7bbac-103">有時候您會想要尋找具有特定屬性的所有項目。</span><span class="sxs-lookup"><span data-stu-id="7bbac-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="7bbac-104">您並不關心屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="7bbac-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="7bbac-105">但是，您想要根據屬性的存在與否來選擇。</span><span class="sxs-lookup"><span data-stu-id="7bbac-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="7bbac-106">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="7bbac-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="7bbac-107">範例</span><span class="sxs-lookup"><span data-stu-id="7bbac-107">Example</span></span>  
 <span data-ttu-id="7bbac-108">下列程式碼只會選取具有 `Select` 屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="7bbac-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="7bbac-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7bbac-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7bbac-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bbac-110">See Also</span></span>  
 [<span data-ttu-id="7bbac-111">XPath 使用者適用的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7bbac-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

