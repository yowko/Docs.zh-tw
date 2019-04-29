---
title: HOW TO：撰寫可根據內容 (Visual Basic) 尋找項目的查詢
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: 0981da1e35f2c0b6023c009d4f62c95a612d8971
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614879"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a><span data-ttu-id="17730-102">HOW TO：撰寫可根據內容 (Visual Basic) 尋找項目的查詢</span><span class="sxs-lookup"><span data-stu-id="17730-102">How to: Write a Query that Finds Elements Based on Context (Visual Basic)</span></span>
<span data-ttu-id="17730-103">有時候您可能必須撰寫會依其內容選取項目的查詢。</span><span class="sxs-lookup"><span data-stu-id="17730-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="17730-104">您可能想要依據前面或後面的同層級項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="17730-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="17730-105">您可能想要依據子系或祖系項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="17730-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="17730-106">您僅能撰寫查詢並使用 `where` 子句中的查詢結果來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="17730-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="17730-107">如果您必須先依據 Null 進行測試，然後再測試值，在 `let` 子句中進行查詢，然後使用 `where` 子句中的結果會比較方便。</span><span class="sxs-lookup"><span data-stu-id="17730-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17730-108">範例</span><span class="sxs-lookup"><span data-stu-id="17730-108">Example</span></span>  
 <span data-ttu-id="17730-109">下列範例會選取緊跟著 `p` 項目後面的所有 `ul` 項目。</span><span class="sxs-lookup"><span data-stu-id="17730-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```vb  
Dim doc As XElement = _  
    <Root>  
        <p id='1'/>  
        <ul>abc</ul>  
        <Child>  
            <p id='2'/>  
            <notul/>  
            <p id='3'/>  
            <ul>def</ul>  
            <p id='4'/>  
        </Child>  
        <Child>  
            <p id='5'/>  
            <notul/>  
            <p id='6'/>  
            <ul>abc</ul>  
            <p id='7'/>  
        </Child>  
    </Root>  
  
Dim items As IEnumerable(Of XElement) = _  
    From e In doc...<p> _  
    Let z = e.ElementsAfterSelf().FirstOrDefault() _  
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _  
    Select e  
  
For Each e As XElement In items  
    Console.WriteLine("id = {0}", e.@<id>)  
Next  
```  
  
 <span data-ttu-id="17730-110">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="17730-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="17730-111">範例</span><span class="sxs-lookup"><span data-stu-id="17730-111">Example</span></span>  
 <span data-ttu-id="17730-112">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="17730-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="17730-113">如需詳細資訊，請參閱 <<c0> [ 處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="17730-113">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim doc As XElement = _  
            <Root>  
                <p id='1'/>  
                <ul>abc</ul>  
                <Child>  
                    <p id='2'/>  
                    <notul/>  
                    <p id='3'/>  
                    <ul>def</ul>  
                    <p id='4'/>  
                </Child>  
                <Child>  
                    <p id='5'/>  
                    <notul/>  
                    <p id='6'/>  
                    <ul>abc</ul>  
                    <p id='7'/>  
                </Child>  
            </Root>  
  
        Dim items As IEnumerable(Of XElement) = _  
            From e In doc...<p> _  
            Let z = e.ElementsAfterSelf().FirstOrDefault() _  
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _  
            Select e  
  
        For Each e As XElement In items  
            Console.WriteLine("id = {0}", e.@<id>)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="17730-114">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="17730-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="17730-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17730-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="17730-116">基本查詢 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17730-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
