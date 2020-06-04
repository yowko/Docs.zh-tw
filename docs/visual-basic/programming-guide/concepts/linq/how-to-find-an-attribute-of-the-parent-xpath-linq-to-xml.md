---
title: 作法：尋找父系的屬性 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: 98b6e0e55390a2be13968e455321311661d81e84
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405296"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b947c-102">如何：尋找父系的屬性（XPath-LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b947c-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b947c-103">這個主題顯示如何導覽到父項目並尋找其屬性。</span><span class="sxs-lookup"><span data-stu-id="b947c-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="b947c-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="b947c-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="b947c-105">範例</span><span class="sxs-lookup"><span data-stu-id="b947c-105">Example</span></span>  
 <span data-ttu-id="b947c-106">這個範例會先尋找 `Author` 項目。</span><span class="sxs-lookup"><span data-stu-id="b947c-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="b947c-107">接著，它會尋找父項目的 `id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b947c-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="b947c-108">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="b947c-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b947c-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b947c-109">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="b947c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b947c-110">See also</span></span>

- [<span data-ttu-id="b947c-111">XPath 使用者的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b947c-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
