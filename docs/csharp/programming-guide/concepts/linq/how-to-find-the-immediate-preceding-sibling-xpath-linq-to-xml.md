---
title: 如何尋找緊接在的先前的兄弟（XPath-LINQ to XML）C#（）
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 1e5aece41021642d43b7f6f7b78bb105156ee4ee
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140999"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="abfdb-102">如何尋找緊接在的先前的兄弟（XPath-LINQ to XML）C#（）</span><span class="sxs-lookup"><span data-stu-id="abfdb-102">How to find the immediate preceding sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="abfdb-103">有時候您會想要尋找節點正前面的同層級。</span><span class="sxs-lookup"><span data-stu-id="abfdb-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="abfdb-104">由於前面同層級座標軸的位置性述詞語意 (Semantics) 在 XPath 中與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 相反的這個差異，這是其中一個更有趣的比較。</span><span class="sxs-lookup"><span data-stu-id="abfdb-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abfdb-105">範例</span><span class="sxs-lookup"><span data-stu-id="abfdb-105">Example</span></span>  
 <span data-ttu-id="abfdb-106">在這個範例中，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢會使用 <xref:System.Linq.Enumerable.Last%2A> 運算子，尋找集合中由 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> 傳回的最後一個節點。</span><span class="sxs-lookup"><span data-stu-id="abfdb-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="abfdb-107">相較之下，XPath 運算式會使用述詞搭配 1 這個值來尋找正前面的項目。</span><span class="sxs-lookup"><span data-stu-id="abfdb-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
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
  
 <span data-ttu-id="abfdb-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="abfdb-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child3 />  
```  
