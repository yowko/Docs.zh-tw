---
title: "如何︰ 尋找父代 (XPATH-LINQ to XML) 的屬性 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 93cc2804f52201bd87282020a381ada8550b7a0f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b2e9d-102">如何︰ 尋找父代 (XPATH-LINQ to XML) 的屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e9d-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b2e9d-103">這個主題顯示如何導覽到父項目並尋找其屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e9d-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="b2e9d-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="b2e9d-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="b2e9d-105">範例</span><span class="sxs-lookup"><span data-stu-id="b2e9d-105">Example</span></span>  
 <span data-ttu-id="b2e9d-106">這個範例會先尋找 `Author` 項目。</span><span class="sxs-lookup"><span data-stu-id="b2e9d-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="b2e9d-107">接著，它會尋找父項目的 `id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e9d-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="b2e9d-108">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="b2e9d-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b2e9d-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b2e9d-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2e9d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2e9d-110">See Also</span></span>  
 [<span data-ttu-id="b2e9d-111">LINQ to XML 的 XPath 使用者 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e9d-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

