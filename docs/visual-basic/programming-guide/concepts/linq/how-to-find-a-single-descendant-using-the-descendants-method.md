---
title: HOW TO：尋找單一子系使用 Descendants 方法 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: 0a2574422f95ed4d2b82c33ee999b233d95ea398
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855591"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a><span data-ttu-id="a49c3-102">HOW TO：尋找單一子系使用 Descendants 方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a49c3-102">How to: Find a Single Descendant Using the Descendants Method (Visual Basic)</span></span>
<span data-ttu-id="a49c3-103">您可以使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸方法快速撰寫程式碼以尋找唯一具名的單一項目。</span><span class="sxs-lookup"><span data-stu-id="a49c3-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="a49c3-104">當您想要利用特定名稱尋找特定子代時，這個技術特別實用。</span><span class="sxs-lookup"><span data-stu-id="a49c3-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="a49c3-105">您可以撰寫程式碼來導覽所需的項目，但使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸撰寫程式碼通常比較快也比較容易。</span><span class="sxs-lookup"><span data-stu-id="a49c3-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a49c3-106">範例</span><span class="sxs-lookup"><span data-stu-id="a49c3-106">Example</span></span>  
 <span data-ttu-id="a49c3-107">此範例使用 <xref:System.Linq.Enumerable.First%2A> 標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="a49c3-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 <span data-ttu-id="a49c3-108">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a49c3-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="a49c3-109">範例</span><span class="sxs-lookup"><span data-stu-id="a49c3-109">Example</span></span>  
 <span data-ttu-id="a49c3-110">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="a49c3-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a49c3-111">如需詳細資訊，請參閱 <<c0> [ 處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="a49c3-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="a49c3-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a49c3-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="a49c3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a49c3-113">See also</span></span>

- [<span data-ttu-id="a49c3-114">基本查詢 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a49c3-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
