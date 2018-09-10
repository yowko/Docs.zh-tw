---
title: 如何：從檔案載入 XML (C#)
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: b8322863ad33f8116e26d98467490b9114339553
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43746651"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="e0e3a-102">如何：從檔案載入 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e0e3a-102">How to: Load XML from a File (C#)</span></span>
<span data-ttu-id="e0e3a-103">這個主題顯示如何使用 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 方法，從 URI 載入 XML。</span><span class="sxs-lookup"><span data-stu-id="e0e3a-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0e3a-104">範例</span><span class="sxs-lookup"><span data-stu-id="e0e3a-104">Example</span></span>  
 <span data-ttu-id="e0e3a-105">下列範例顯示如何從檔案載入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e0e3a-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="e0e3a-106">下列範例會載入 books.xml，並將 XML 樹狀輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="e0e3a-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="e0e3a-107">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e3a-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="e0e3a-108">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e0e3a-108">This code produces the following output:</span></span>  
  
```xml  
<Catalog>  
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
</Catalog>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0e3a-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0e3a-109">See Also</span></span>

- [<span data-ttu-id="e0e3a-110">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e0e3a-110">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
