---
title: HOW TO：尋找子系，子項目 (XPATH-LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a958af40-f754-4409-85f9-7746978d4cb3
ms.openlocfilehash: 5d5ccd46a595a7ec7477246dd9a9cd351614fdf8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520954"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="76785-102">HOW TO：尋找子系，子項目 (XPATH-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76785-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="76785-103">本主題顯示如何利用特定名稱取得子項目的子代項目。</span><span class="sxs-lookup"><span data-stu-id="76785-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="76785-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="76785-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="76785-105">範例</span><span class="sxs-lookup"><span data-stu-id="76785-105">Example</span></span>  
 <span data-ttu-id="76785-106">此範例模擬從字組處理文件的 XML 表示擷取文字的問題。</span><span class="sxs-lookup"><span data-stu-id="76785-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="76785-107">它會先選取所有 `Paragraph` 項目，然後它會選取每個 `Text` 項目的所有 `Paragraph` 子代項目。</span><span class="sxs-lookup"><span data-stu-id="76785-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="76785-108">這不會選取 `Text` 項目的子代 `Comment` 項目。</span><span class="sxs-lookup"><span data-stu-id="76785-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Paragraph>  
            <Text>This is the start of</Text>  
        </Paragraph>  
        <Comment>  
            <Text>This comment is not part of the paragraph text.</Text>  
        </Comment>  
        <Paragraph>  
            <Annotation Emphasis='true'>  
                <Text> a sentence.</Text>  
            </Annotation>  
        </Paragraph>  
        <Paragraph>  
            <Text>  This is a second sentence.</Text>  
        </Paragraph>  
    </Root>  
  
' LINQ to XML query  
Dim str1 As String = _  
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _  
    Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
' XPath expression  
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _  
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _  
    .Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
If str1 = str2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(str2)  
```  
  
 <span data-ttu-id="76785-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="76785-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="76785-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76785-110">See also</span></span>
- [<span data-ttu-id="76785-111">LINQ to XML (Visual Basic) 的 XPath 使用者適用的</span><span class="sxs-lookup"><span data-stu-id="76785-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
