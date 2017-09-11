---
title: "如何：尋找同層級節點 (XPath-LINQ to XML) (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1e40a04b1e4359b2455442b2589b9d036562d70a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="663de-102">如何：尋找同層級節點 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="663de-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="663de-103">您可能想要尋找具有特定名稱之節點的所有同層級。</span><span class="sxs-lookup"><span data-stu-id="663de-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="663de-104">如果內容節點也有特定的名稱，所產生的集合可能包含內容節點。</span><span class="sxs-lookup"><span data-stu-id="663de-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="663de-105">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="663de-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="663de-106">範例</span><span class="sxs-lookup"><span data-stu-id="663de-106">Example</span></span>  
 <span data-ttu-id="663de-107">此範例會先尋找 `Book` 項目，然後尋找名稱為 `Book` 的所有同層級項目。</span><span class="sxs-lookup"><span data-stu-id="663de-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="663de-108">所產生的集合包含內容節點。</span><span class="sxs-lookup"><span data-stu-id="663de-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="663de-109">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="663de-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="663de-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="663de-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Book id="bk101">  
  <Author>Garghentini, Davide</Author>  
  <Title>XML Developer's Guide</Title>  
  <Genre>Computer</Genre>  
  <Price>44.95</Price>  
  <PublishDate>2000-10-01</PublishDate>  
  <Description>An in-depth look at creating applications   
      with XML.</Description>  
</Book>  
<Book id="bk102">  
  <Author>Garcia, Debra</Author>  
  <Title>Midnight Rain</Title>  
  <Genre>Fantasy</Genre>  
  <Price>5.95</Price>  
  <PublishDate>2000-12-16</PublishDate>  
  <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="663de-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="663de-111">See Also</span></span>  
 [<span data-ttu-id="663de-112">XPath 使用者適用的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="663de-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

