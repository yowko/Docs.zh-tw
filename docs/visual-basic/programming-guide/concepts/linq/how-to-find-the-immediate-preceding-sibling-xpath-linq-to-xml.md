---
title: HOW TO：尋找正前面的同層級 (XPATH-LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: ca3602a24b80d9002a639d9a319a731541aeb2df
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840415"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="a1c4a-102">HOW TO：尋找正前面的同層級 (XPATH-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1c4a-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a1c4a-103">有時候您會想要尋找節點正前面的同層級。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="a1c4a-104">由於前面同層級座標軸的位置性述詞語意 (Semantics) 在 XPath 中與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 相反的這個差異，這是其中一個更有趣的比較。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1c4a-105">範例</span><span class="sxs-lookup"><span data-stu-id="a1c4a-105">Example</span></span>  
 <span data-ttu-id="a1c4a-106">在這個範例中，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢會使用 <xref:System.Linq.Enumerable.Last%2A> 運算子，尋找集合中由 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> 傳回的最後一個節點。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="a1c4a-107">相較之下，XPath 運算式會使用述詞搭配 1 這個值來尋找正前面的項目。</span><span class="sxs-lookup"><span data-stu-id="a1c4a-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="a1c4a-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a1c4a-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1c4a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1c4a-109">See also</span></span>

- [<span data-ttu-id="a1c4a-110">LINQ to XML (Visual Basic) 的 XPath 使用者適用的</span><span class="sxs-lookup"><span data-stu-id="a1c4a-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
