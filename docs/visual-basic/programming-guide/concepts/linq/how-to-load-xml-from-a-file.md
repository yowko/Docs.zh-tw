---
title: "如何︰ 載入 XML 檔案 (Visual Basic) |Microsoft 文件"
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
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0b336816a7a557a4cd820b31f64ee42a791f3649
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a><span data-ttu-id="1134d-102">如何︰ 載入 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1134d-102">How to: Load XML from a File (Visual Basic)</span></span>
<span data-ttu-id="1134d-103">本主題說明如何使用從 URI 載入 XML<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>方法。</xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1134d-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1134d-104">範例</span><span class="sxs-lookup"><span data-stu-id="1134d-104">Example</span></span>  
 <span data-ttu-id="1134d-105">下列範例顯示如何從檔案載入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1134d-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="1134d-106">下列範例會載入 books.xml，並將 XML 樹狀輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="1134d-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="1134d-107">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1134d-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim booksFromFile As XElement = XElement.Load("books.xml")  
Console.WriteLine(booksFromFile)  
```  
  
 <span data-ttu-id="1134d-108">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1134d-108">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1134d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1134d-109">See Also</span></span>  
 [<span data-ttu-id="1134d-110">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1134d-110">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
