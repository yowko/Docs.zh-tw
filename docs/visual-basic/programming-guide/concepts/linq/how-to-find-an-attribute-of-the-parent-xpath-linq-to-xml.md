---
title: HOW TO：尋找父代 (XPATH-LINQ to XML) 的屬性 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: ded20c173063492d260aee5ba55f3c4c585bd961
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828650"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="be4e1-102">HOW TO：尋找父代 (XPATH-LINQ to XML) 的屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be4e1-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="be4e1-103">這個主題顯示如何導覽到父項目並尋找其屬性。</span><span class="sxs-lookup"><span data-stu-id="be4e1-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="be4e1-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="be4e1-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="be4e1-105">範例</span><span class="sxs-lookup"><span data-stu-id="be4e1-105">Example</span></span>  
 <span data-ttu-id="be4e1-106">這個範例會先尋找 `Author` 項目。</span><span class="sxs-lookup"><span data-stu-id="be4e1-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="be4e1-107">接著，它會尋找父項目的 `id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="be4e1-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="be4e1-108">此範例使用下列 XML 文件：[XML 範例檔：書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="be4e1-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 <span data-ttu-id="be4e1-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="be4e1-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="be4e1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be4e1-110">See also</span></span>

- [<span data-ttu-id="be4e1-111">LINQ to XML (Visual Basic) 的 XPath 使用者適用的</span><span class="sxs-lookup"><span data-stu-id="be4e1-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
