---
title: 如何：尋找正前面的同層級項目 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 82c0ee6e7340ada18fb2077c0b8b04fb6a41671a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318551"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="b9308-102">如何：尋找正前面的同層級項目 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b9308-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="b9308-103">有時候您會想要尋找節點正前面的同層級。</span><span class="sxs-lookup"><span data-stu-id="b9308-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="b9308-104">由於前面同層級座標軸的位置性述詞語意 (Semantics) 在 XPath 中與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 相反的這個差異，這是其中一個更有趣的比較。</span><span class="sxs-lookup"><span data-stu-id="b9308-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9308-105">範例</span><span class="sxs-lookup"><span data-stu-id="b9308-105">Example</span></span>  
 <span data-ttu-id="b9308-106">在這個範例中，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢會使用 <xref:System.Linq.Enumerable.Last%2A> 運算子，尋找集合中由 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> 傳回的最後一個節點。</span><span class="sxs-lookup"><span data-stu-id="b9308-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="b9308-107">相較之下，XPath 運算式會使用述詞搭配 1 這個值來尋找正前面的項目。</span><span class="sxs-lookup"><span data-stu-id="b9308-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="b9308-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b9308-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9308-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9308-109">See Also</span></span>  
 [<span data-ttu-id="b9308-110">XPath 使用者適用的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b9308-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
