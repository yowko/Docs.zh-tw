---
title: 作法：尋找具有特定名稱的同層級屬性 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 0317e03de6f671991d6d0a4247ca2e9c172439b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405270"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="4c733-102">如何：尋找具有特定名稱之同級的屬性（XPath-LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4c733-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4c733-103">本主題顯示如何尋找內容節點之同層級的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="4c733-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="4c733-104">在集合中，只會傳回具有特定名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="4c733-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="4c733-105">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="4c733-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="4c733-106">範例</span><span class="sxs-lookup"><span data-stu-id="4c733-106">Example</span></span>  
 <span data-ttu-id="4c733-107">此範例會先尋找 `Book` 項目，接著尋找名稱為 `Book` 的所有同層級項目，然後尋找名稱為 `id` 的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="4c733-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="4c733-108">結果為屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="4c733-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="4c733-109">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="4c733-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="4c733-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="4c733-110">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c733-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c733-111">See also</span></span>

- [<span data-ttu-id="4c733-112">XPath 使用者的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4c733-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
