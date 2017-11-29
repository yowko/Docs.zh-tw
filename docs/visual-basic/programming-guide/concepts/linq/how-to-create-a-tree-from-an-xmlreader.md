---
title: "如何： 從 XmlReader (Visual Basic) 中建立樹狀結構"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ceae7c2bee85e7b368322c8ba195dea9feff672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="6e662-102">如何： 從 XmlReader (Visual Basic) 中建立樹狀結構</span><span class="sxs-lookup"><span data-stu-id="6e662-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="6e662-103">這個主題顯示如何從 <xref:System.Xml.XmlReader> 直接建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="6e662-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="6e662-104">若要從 <xref:System.Xml.Linq.XElement> 建立 <xref:System.Xml.XmlReader>，您必須將 <xref:System.Xml.XmlReader> 定位在項目節點上。</span><span class="sxs-lookup"><span data-stu-id="6e662-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="6e662-105"><xref:System.Xml.XmlReader> 將會略過註解與處理指示，但是，如果 <xref:System.Xml.XmlReader> 定位在文字節點上，則會擲出錯誤。</span><span class="sxs-lookup"><span data-stu-id="6e662-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="6e662-106">若要避免此類的錯誤，請務必將 <xref:System.Xml.XmlReader> 定位在項目上，然後再從 <xref:System.Xml.XmlReader> 建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="6e662-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e662-107">範例</span><span class="sxs-lookup"><span data-stu-id="6e662-107">Example</span></span>  
 <span data-ttu-id="6e662-108">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="6e662-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="6e662-109">下列程式碼會建立 `T:System.Xml.XmlReader` 物件，然後讀取節點，直到找到第一個項目節點為止。</span><span class="sxs-lookup"><span data-stu-id="6e662-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="6e662-110">接著，它會載入 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="6e662-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="6e662-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="6e662-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e662-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e662-112">See Also</span></span>  
 [<span data-ttu-id="6e662-113">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e662-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
